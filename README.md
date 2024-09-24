# 실전! AI 추천 시스템 알고리즘 이해 및 구현, 2024년 9월 강의

## 실습 환경 구동 방법

윈도우즈 명령 프롬프트에 진입합니다. (Windows -> 실행 -> cmd)

wsl 구동시킵니다. 

```cmd
wsl 
```

wsl 환경에서,

```bash
cd ~
source rcmd/bin/activate
jupyter lab
```
cd ~ : 홈디렉터리로 이동

source rcmd/bin/activate : 추천시스템 용 python 환경 진입

jupyter lab: 쥬피터 랩 구동

## 실습 데이터셋 경로

실습 데이터 셋과 모델 파일은 Google Drive에 있습니다. 

[실습 Google Drive 경로](https://drive.google.com/drive/folders/1B2MWhhEjf1HChP85n9mp8Bp-UvqdvLLA)


## 실습 환경 구축 방법

실습 환경은 Windows 상에서 리눅스를 구축할 수 있는 WSL2(Windows Subsystem for Linux 2)을 기반으로 구축되었습니다.

WSL2 상의 Ubuntu Linux를 사용합니다.

1. Ubuntu 가상 환경 설치

윈도우즈 커맨드 창에서, 

```cmd
wsl --install -d Ubuntu
```
실행하면,  Ubuntu 가상환경이 wsl 상에 설치가 시작이되고, 

root 계정 ID/PW 를 입력하면 마무리 됩니다. (시스템 마스터 권한을 지니므로, 시스템 관리 작업 시 필요하므로 꼭 기억해 두세요)

WSL에 설치된 Ubuntu 가상환경에 진입합니다.

```cmd
wsl -d Ubuntu
```

2. Python(3.12.6) 설치 기준: 직접 빌드합니다. 

Linux를 최신 버젼으로 업데이트 하고, python을 빌드하기 위한 소프트웨어를 설치합니다.
```bash
sudo apt-get update
sudo apt install software-properties-common
sudo apt install build-essential
sudo apt install gdb lcov pkg-config zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev libsqlite3-dev wget libbz2-dev libgdbm-compat-dev liblzma-dev libreadline6-dev tk-dev uuid-dev
```

Python을 다운로드 하고 압축을 풉니다.
```bash
wget https://www.python.org/ftp/python/3.12.6/Python-3.12.6.tar.xz
tar -xvf Python-3.12.6.tar.xz
```

Python을 빌드하고 설치합니다.
```bash
cd Python-3.12.6
./configure --enable-optimizations
make -j 4
make altinstall
```

홈디렉터리로 이동하고, 설치된 Python을 사용하는 Python 가상환경을 만듭니다.
```bash
cd ~
/usr/local/bin/python3.12 -m venv rcmd
```
