##### 이 readme페이지는 리눅스 명령 top,ps,jobs,kill에 대해 설명한다.

****

### 1. top에 대해

top은 시스템의 현재 상태를 실시간으로 모니터링하는 명령어이다. 주로 시스템 리소스 사용량과 프로세스 관련 정보를 표시한다. top을 실행하면 CPU 사용량, 메모리 사용량, 실행 중인 프로세스 목록 등을 볼 수 있다. 상단에는 시스템 전반적인 정보가 표시되며, 하단에는 프로세스 목록이 표시된다. top을 실행한 후에는 일정한 간격으로 업데이트되며, 프로세스 정렬, 종료 등의 작업을 수행할 수도 있다.

top을 실행하는법

![top을 실행하는법](https://1.bp.blogspot.com/-4QsYJ3duF9U/X1t8Tk1HJxI/AAAAAAAADYE/R9DcDeun0xY5MF4TCBgX00fXiPtNNKb7gCLcBGAsYHQ/s821/4-1_%25EA%25B8%25B0%25EB%25B3%25B8%2B%25EC%2582%25AC%25EC%259A%25A9%25EB%25B2%2595%2B%25EB%25B3%25B4%25EA%25B8%25B0.png)

리눅스에서 top -h를 입력하면 top을 실행시킬수있다

![top 실행화면](https://1.bp.blogspot.com/-6soIwrMhJ_I/X1t5zimgM2I/AAAAAAAADXY/lXoGOGDPInQkaNhjKRAHLB2pW-_SsvhtgCLcBGAsYHQ/s821/2_top%2B%25EB%25AA%2585%25EB%25A0%25B9%25EC%2596%25B4%2B%25EC%25B6%259C%25EB%25A0%25A5%25ED%2599%2594%25EB%25A9%25B4%2B%2528%25EC%259A%2594%25EC%2595%25BD%2B%25EC%25B6%259C%25EB%25A0%25A5%2B%25ED%2595%25AD%25EB%25AA%25A9%2529.png)

실행시킬시 이런화면이 나타난다. 

* xx:xx :상단에 현재 시간 옆에 xx:xx 표시는 해당 시간 전에 서버 구동 시간 (예를 들어 2:10 표시할 경우 서버는 2시간 10분 전에 서버가 구동되었다는 의미임.)

* users: users 앞에 숫자는 총 사용자 수

* load average: 각각 1, 5, 15 분 동안의 평균 시스템 부하량 평균값

* Tasks & %Cpu(s)

이 부분은 최소 2 줄로 구성되며 SMP 환경에서 추가행은 개별 CPU 상태 백분율을 반열할 수 있음.

1 번째 줄은 작업/스레드 모드 상태에 따라 총 작업 또는 스레드를 표시함. (작업/스레드 모드 변경 문자열은 'H' 임)

분류는 running, sleeping, stopped, zombie 로 분류됨.

2 번째 줄은 마지막 새로 고침 이후 간격을 기준으로 한 CPU 상태율을 표시함.

분류는 아래와 같음.

us, user    - un-niced 사용자 프로세스를 실행하는 시간

sy, system  - 커널 프로세스 실행 시간

ni, nice    - niced 사용자 프로세스 실행 시간

id, idle    - 커널 idle 핸들러에서 보낸 시간

wa, IO-wait - I/O 완료를 기다리는 시간

hi          - 하드웨어 인터럽트 서비스에 소요 된 시간

si          - 소프트웨어 인터럽트 서비스에 소요 된 시간

st          - Hypervisor VM 에 할당된 시간



* Mem & Swap

바이트 단위 표시에 따라 키로바이트(KiB) ~ 엑스비바이트(EiB)까지 표시됨.

바이트 단위 표시 변경 문자열은 'E' 임.

1 번째 줄은 물리적 메모리를 반영함.

분류는 total, free, used, buff/cache 로 구분됨.

2 번째 줄은 대부분 가상 메모리를 반영함.

분류는 total, free, used(물리적 메모리), avail Mem(물리적 메모리)

****

### 2. ps에 대해

ps는 현재 실행 중인 프로세스 목록을 보여주는 명령어입니다. ps 명령어는 다양한 옵션과 함께 사용할 수 있으며, 실행 중인 모든 프로세스 또는 특정 사용자의 프로세스 등을 필터링하여 표시할 수 있습니다. 일반적으로 ps aux 또는 ps -ef와 함께 사용하여 모든 프로세스 목록을 볼 수 있습니다. ps 명령어를 사용하면 프로세스 ID(PID), CPU 사용량, 메모리 사용량, 실행 시간 등의 정보를 확인할 수 있습니다.

##ps 실행화면

![ps실행화면](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F992710385BC6EE070F)

* UID :실행유저

* PID :프로세스 id

* PPID :부모 프로세스 PID

* C: cpu사용

* STIME: START TIME

* TTY:프로세스 제어 위치

* TIME: 구동시간

* CMD: 실행명령어

****

### 3. JOBS에 대해

jobs는 쉘에서 백그라운드로 실행되고 있는 작업 목록을 표시하는 명령어입니다. 쉘에서 실행 중인 프로그램을 백그라운드로 전환하면 해당 작업은 제어권을 쉘로 돌려주고 백그라운드에서 실행됩니다. jobs 명령어를 사용하면 현재 쉘에서 백그라운드로 실행 중인 작업 목록과 해당 작업에 할당된 작업 번호(JOB ID)를 볼 수 있습니다.

## JOBS 실행화면

![JOBS실행 화면](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F99B5DF505E60F42C10)

해당 작업의 상태에 따라서 다음 형태로 나타난다.

* Running - 작업이 종료하지 않고 계속 진행 중

* Done - 작업이 완료되어 0을 반환하고 종료 함

* Stopped - 작업이 일시 중단

* Done(code) - 작업이 정상적 완료 코드를 반환

* Stopped(SIGTSTP) - SIGTSTP 신호가 작업을 일시 중단

* Stopped(SIGSTOP) - SIGSTOP 신호가 작업을 일시 중단
* Stopped(SIGTTIN) - SIGTTIN 신호가 작업을 일시 중단
* Stopped(SIGTTOU) - SIGTTOU 신호가 작업을 일시 중단

## 또한 JOBS에 -l이 붙으면 다음과 같이 프로세스 아이디도 출력 가능하다

![jobs -l](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F99E14B465E60F42D2A)

*******************

### 4. kill에 대해

kill은 실행 중인 프로세스를 종료하는 명령어입니다. kill 명령어를 사용하기 위해서는 종료하려는 프로세스의 프로세스 ID(PID)를 알아야 합니다. 기본적으로 kill 명령어는 SIGTERM 시그널을 보내 프로세스를 종료시킵니다.

## kill 실행화면

![kill실행화면](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F993696485C6377E90C)

다음과 같이 ps를 통해 pid를 얻고 kill과 결합시키면 종료시킬수있다.

![kill -l](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F99E84B455C6378A109)

또한 kill-l을 이용하면 지원하는 시그널의 목록을 알 수 있다.

**************************

따라서 리눅스 명령어 top,ps,jobs,kill 명령어의 역할을 한문장으로 나타내면 다음과 같다.

| top | ps | jobs | kill |
|---------|---------|---------|---------|
| 시스템의 현재상황 모니터링   | 현재 실행중인 프로세스 목록  |  쉘에서 백그라운드로 실행중인 프로세스 목록   | 실행중인 프로세스 종료 |





