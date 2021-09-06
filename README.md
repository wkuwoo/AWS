# **Amazon Web Service** 
*https://opentutorials.org/course/608/3002*

## **Cloud & Amazon Web Service**
* 서버의 구매, 구축, 운영을 대행해주는 서비스
* 웹호스팅과 유사
* 가상화 기술
* 탄력적인 인프라 운영
* 사용한 만큼 과금
## **Elastic Compute Cloud(EC2)**
* Amazon Web Service의 심장에 해당하는 서비스
* 독립적인 컴퓨터
* Linux, Windows 운영체제 제공
* 웹서버, 애플리케이션 서버로 사용
## **Elastic Block Store(EBS)**
* 필요한 용량에 맞게 구입 가능
* 필요에 따라서 즉시 생성하고, 제거 가능
* 사용한 만큼 과금 되는 종량제
* 내부적으로 데이터를 실시간 복제하고 있기 떄문에 하드디스크에 비해서 데이터를 잃어버릴 확률이 현저히 낮음
* 스냅샷 기능을 제공해서 EBS의 현재 상태 그대로 보존 가능
* EC2 인스턴스를 제거해도 EBS는 독립적이기 때문에 데이터 유지
## <span style="background-color:red">**Simple Storage Service(S3)**</span>
* <span style="background-color:red">파일 서버</span>
* <span style="background-color:red">저장할 수 있는 파일 수의 제한이 없음</span>
* <span style="background-color:red">많은 사용자가 접속을 해도 이를 감당하기 위해서 시스템적인 작업을 하지 않아도 됨</span>
* <span style="background-color:red">1B ~ 5T의 단일 파일을 저장 가능</span>
* <span style="background-color:red">파일에 인증을 붙여서 무단으로 엑세스 하지 못하도록 할 수 있음</span>
* <span style="background-color:red">HTTP와 BitTorrent 프로토콜을 지원</span>
* <span style="background-color:red">REST, SOAP 인터페이스를 제공</span>
* <span style="background-color:red">버전관리 기능을 통해서 사용자에 의한 실수도 복원 가능</span>
* <span style="background-color:red">정보의 중요도에 따라서 보호 수준을 차등할 수 있고, 이에 따라서 비용을 절감 (RSS)</span>
* d

## **Relational Database Service(RDS)**
* Mysql, Oracle, SQL Server 지원
* 백업, 리플리케이션을 아마존 인프라가 자동으로 제공
## **Elastic Load Balancing(ELB)**
* EC2로 유입되는 트래픽을 여러대의 EC2로 분산
* 장애가 발생한 EC2를 감지해서 자동으로 배제
* Auto Scaling 기능을 이용해서 EC2를 자동으로 생성, 삭제
* ### **Auto Scaling**
  * EC2 인스턴스의 규모를 자동으로 확대/축소
  * 인스턴스의 규모를 변화시키는 다양한 조건이 있기 때문에, 지능적으로 인스턴스를 증가/감소 가능
  * 처리량의 증가에 빠르게 대응 가능
  * Command Line Interface(CLI)를 통해서만 제어 가능
  * 미리 만들어진 이미지(AMI)를 이용해서 인스턴스를 자동으로 생성
  * ### **Auto Scaling Type**
    * 부하에 따라 자동으로 규모 변경
    * 현재의 규모 유지
    * 시간에 따라 변경
  * ### **Auto Scaling의 절차**
    * launch configuration 설정
      * AMI
      * instance type
    * Auto Scaling Group 생성
      * ELB
      * 최소/최대 인스턴스의 수량
      * 가용성 존
    * 정책(Policy) 생성
      * 인스턴스의 추가/제거의 방법과 수량
      * cooldown
    * Cloud Watch에서 Alarm을 생성하고 정책과 연결
* SSL 암호화 지원
* SSL의 경유지로 ELB를 사용하는 경우에 SSL 처리에 따른 부하를 ELB가 수용
* IPv4, IPv6 지원
* ELB에 EC2를 붙이면 EC2는 클라이언트와 직접 통신을 하지 않고, ELB를 경유해서 통신
  * 따라서 EC2 입장에서는 클라이언트의 IP, User-Agent, 프로토콜(http,https)을 파악 불가
  * *X-Forwarded-For* 라고하는 특수한 HTTP 헤더를 전달하여, 해당 문제를 해결할 수 있음
