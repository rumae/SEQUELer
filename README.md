# About Sequel SAFE
## 배경
1972년 E.F Codd 박사에 의해 RDB 이론이 소개된 이후 여러 벤더가 RDBMS를 개발하였고, 다양한 third-party가 IDE, 백업 및 복원, 모니터링, CASE 도구와 같은 영역에서 경쟁하고 있습니다.

레드 오션을 방불케하는 비슷 비슷한 기능들의 경쟁 속에, 현업에서 절실히 필요로하는 이 기능 만큼은 어떤 도구도 제대로 지원하고 있지 않은데, 그것은 바로  **형상 관리** 입니다.

데이터베이스 형상 관리란, 데이테베이스를 구성하는 각 객체 - Table, View, Index, Stored Procedure, Function, Trigger, etc - 와 데이터베이스 자체에 대한 버전  관리를 기반으로 변경 사항을 체계적으로 추적하고 통제하는 것입니다.

다른 소프트웨어와 마찬가지로  **데이터베이스 역시 형상 관리** 가 필요합니다.

데이터베이스 변경의 원인을 알아내고 제어하며, 개발 단계 뿐 아니라 유지 보수 단계에서도, 현재 적절히 변경되고 있는지 확인하는 일은 어느 DB 조직에서나 원하고 있는 일이기 때문입니다.
또한 개발 과정에서 발생하는 문제 요인을 최소화함으로써 소프트웨어 개발의 전체 비용을 줄일 수 있습니다.

 **데이터베이스를 형상 관리한다면 배포 역시 체계적이 됩니다.** 
즉, 더 이상 Diff. 도구로 개발 DB와 프로덕트 DB의 차이점을 비교해 마이그레이션 스크립트를 작성할 필요가 없습니다.
이미 데이터베이스에는 명확한 버전이 부여되었으므로, 관리자는 배포할 버전을 선택하기만 하면 됩니다.

## 소개
 **Sequel Safe** 로 명명된 초기 스크립트 셋은 2009년  [개인 블로그](http://purumae.tistory.com) 에 소스 코드를 공개하였고, 대표적으로 Eyedentity Games에서 2010년 이후 현재까지 데이터베이스 (MS-SQL) 형상 관리 및 생산성 도구로 사용되고 있습니다.
Eyedentity Games가 개발한 온라인 MORPG인  **드래곤 네스트** 는 10개국 퍼블리셔(파트너)를 통해 40여개 국가에 서비스되고 있으며, Sequel Safe는 형상 관리 도구, Stored Procedure 작성을 지원하는 생산성 도구, 그리고 배포 도구로서 크게 기여하고 있습니다.

2016년에 MySQL의 형상 관리에 사용할 수 있도록 포팅하였으며, 현재는 단순 스크립트 셋이 아닌 웹 UI를 갖춘 형상 관리 도구의 기본적인 모습을 갖추게 되었습니다.

## 설명
* Sequel Safe는 RDB 형상 관리 및 배포 도구입니다.
    * 데이터베이스 객체의 형상 관리
        * 테이블, 인덱스, 뷰, 루틴, 이벤트 등의 버전 이력과 각 버전의 소스 코드를 조회할 수 있습니다. [링크](https://www.youtube.com/watch?v=VXorwse7oS0&list=PLx5jWq_wyS3y2JoRLokRie_mtXhlqXl-1&index=1)
        * 버전 사이의 소스 코드 차이를 비교할 수 있습니다. [링크](https://www.youtube.com/watch?v=lEwbf4jJ5Wo&list=PLx5jWq_wyS3y2JoRLokRie_mtXhlqXl-1&index=2)
    * 데이터베이스의 형상 관리 및 배포
        * 데이터베이스를 버저닝하고, 이전 버전에서 다음 버전으로 Migration하는 스크립트를 생성할 수 있습니다. [링크](https://www.youtube.com/watch?v=BEp8LCqH2MA&list=PLx5jWq_wyS3y2JoRLokRie_mtXhlqXl-1&index=3)
        * 배포 대상 인스턴스의 endpoint와 credential을 입력하여 다수의 인스턴스에 손쉽게 배포할 수 있습니다. [링크](https://www.youtube.com/watch?v=zR_FQgPNJSg&list=PLx5jWq_wyS3y2JoRLokRie_mtXhlqXl-1&index=4)
        * DML statement 를 배포용 Migration 스크립트에 포함시킬 수 있습니다. [링크](https://www.youtube.com/watch?v=7M9TYNe9BKc&list=PLx5jWq_wyS3y2JoRLokRie_mtXhlqXl-1&index=5)
            * 데이터가 포함된 테이블을 생성해야 할 때
            * 추가한 컬럼에 동적으로 들어가야할 데이터가 있을 때
            * 리팩토링 작업으로 테이블 레이아웃이 변경되어, 데이터 Migration이 필요할 때

* Sequel Safe는  데이터 주도 개발의 생산성 도구입니다. [링크](https://www.youtube.com/watch?v=wiz1TjQX-Xs&list=PLx5jWq_wyS3y2JoRLokRie_mtXhlqXl-1&index=6)
    * 테이블의 메타 데이터를 사용하여 CRUD를 수행하고, Business Logic을 처리할 수 있는 구조의 Stored Procedure 코드를 생성합니다.
    * 생성된 Stored Procedure에는 에러 핸들링과 로깅의 Best Practice가 포함되어 있습니다.
    * Stored Procedure의 API 명세를 웹 페이지로 제공합니다.
    * 팀원 모두 일관된 코딩 규칙을 사용하도록 돕습니다.

* 추가 예정 기능
    * Metadata Quality Service
        * 데이터 거버넌스의 한 부분으로서 데이터베이스 명명 규칙, 코딩 규칙을 감시합니다.
        * 팀은 적용할 규칙을 커스터마이징할 수 있습니다.
    * DDL Audit & Notification
        * 개발 조직과 데이터베이스 조직이 분리된 환경에서 DDL 감사 로그를 조회합니다.
        * 원하는 이벤트 (DDL 유형과 데이터베이스 객체의 조합)에 대해 Notification을 수신합니다.
    * Patch Note Generator
        * 데이터베이스 버저닝 과정에서 변경점을 패치 노트로 자동 생성합니다.
        
* 설치하기
    * AWS 계정이 있다면 옆에 링크한 가이드 문서를 참고하여 설치하시기 바랍니다. [링크](https://docs.google.com/document/d/1-whZ3zzj26P4MTOFB3IvZWMbUt9jNOnA7oVNd_3yEa0/edit?usp=sharing)
