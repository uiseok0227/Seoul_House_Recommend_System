# Seoul_House_Recommend_System
Recommending house in Seoul

# 국내 부동산 데이터 분석을 통한 자취방 매물 추천 시스템
자취방 이상형 월드컵을 통해 사용자의 취향을 파악하여 서울시의 자취방을 추천해주는 시스템입니다.

# 🏠 목차
1. [Overview](#-overview)
2. [과제 진행 방법](#-과제-진행-방법)
3. [Software 사용 방법](#-software-사용-방법)

# 🏠 Overview
실시간 국내 부동산 데이터를 수집 및 분석하여 사용자 맞춤 주거공간 매물을 선별해 제공하는 추천 시스템입니다. 
<br><br>
아이템에 대한 기존 구매 및 평가 이력이 없는 사용자 1명을 대상으로 기존 평가 점수가 없는 데이터로 구성된 데이터셋에서 사용자가 선호할 만한 아이템 상위 7개를 추천하는 추천 시스템입니다. 이때 해당 사용자의 선호도는 이상형 월드컵을 통해 수집하며, 데이터셋은 부동산 매물 데이터를 실시간으로 수집해 구성합니다.
<br><br>
이상형 월드컵이라는 설문 방식을 통해 아이템에 대한 기존 평가 이력이 없는 사용자의 정보를 정확하고 구체적으로 파악할 수 있습니다. 또한 기존 평가 점수가 부재하는 부동산 매물 데이터에서 사용자가 선호할 만한 아이템을 선별하여 제안할 수 있습니다. 

# 🏠 과제 진행 방법
## Summary
### 데이터 
- 부동산 데이터 수집: 네이버 부동산 크롤링, selenium
- 편의시설 데이터 수집: 카카오 developers api
### 이상형 월드컵 
- GUI: thkinter
### 추천 알고리즘
- 콘텐츠 기반 필터링
<br>
분석에 이용할 부동산 데이터는 네이버 부동산에서 크롤링을 통해 수집합니다. 방에서 가장 가까운 편의시설(대형마트, 편의점, 지하철역)까지의 거리 데이터를 얻기 위해 카카오 api를 활용합니다. 
<br><br>
사용자를 대상으로 하는 토너먼트 형식의 설문을 통해 주거공간 정보를 탐색하려는 사용자의 선호도와 요구사항을 수집합니다. 이때 설문에서는 이미지와 텍스트 형식의 가상 부동산 매물을 통해 사용자의 선호도 정보를 수집하며, 각 가상 매물은 특징과 해당 특징의 가중치를 달리하여 구분되도록 생성합니다. 
<br><br>
설문 결과를 통해 해당 사용자의 순위별 부동산 매물에 각각 가중치를 부여하여 사용자의 선호도를 분석합니다. 이러한 방식으로 수집 및 분석한 사용자의 선호도와 요구사항 정보를 바탕으로, 부동산 데이터에 콘텐츠 기반 필터링을 수행하여 사용자 맞춤 주거공간 매물 추천 결과를 사용자 이메일로 전송합니다.


# 🏠 Software 사용 방법 
### 크롤링
크롤링은 크롬과 크롬의 웹드라이버를 이용하여 파이썬 모듈인 셀레니움을 통해 진행됩니다. 사용자의 PC에 크롬이 사전에 설치되어야 하며 소스코드 압축파일의 크롬드라이버를 이용합니다. 이때 크롬 드라이버와 크롬의 버전이 일치하는 지 확인하고 일치하지 않는다면 본 소스코드 압축파일에 있는 크롬 드라이버는 삭제하고 https://chromedriver.chromium.org/downloads 에서 본인 크롬 버전에 맞는 드라이버를 설치합니다. 크롤링은 croll class의 crolling 함수를 통해 진행되며 최종적으로 csv파일을 만들어서 저장합니다. 이때 만약 한글 깨짐 현상이 나타나면 인코딩을 맞춰서 진행하도록 합니다.
### 추천 시스템
서울시_실시간매물추천시스템.ipynb 파일의 '실행' 블록에서 실행할 수 있습니다.
<br><br>
start_gui를 통해 이상형 월드컵이 진행합니다. (이때 꼭 이미지 파일이 있어야 진행됩니다.) 이상형 월드컵을 진행한 후 데이터 크롤링, 추천 알고리즘, 메일 전송 순으로 동작합니다. 
### 성능 평가
성능 평가는 Evaluator.ipynb 파일을 통해 실행할 수 있습니다. 
