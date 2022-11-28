# 서울시 착한가격업소 현황조사 및 소비자만족도분석

## 프로젝트 개요
+ 현재 소비자물가가 상승함에 따라 외식비도 높은 상승률을 보이고 있다. <br>
서울시와 각 기초자치단체에서는 물가안정을 위해 가격이 저렴하고 서비스가 좋은 모범업소를 선정하고 인센티브를 제공하는 <b>'착한가격업소'</b>라는 제도를 실시하고 있다.<br>
그래서 우리팀은 착한가격업소의 운영현황과 소비자 만족도 분석을 통해 제도의 본 취지와 방향성에 맞게 운영되고 있는지 살펴보고자 한다.

## 데이터수집·전처리
### 데이터 수집
+ [서울 열린데이터 광장] - 서울시 착한가격업소 현황.csv -> 업소명, 주소, 전화번호 둥
+ [kakao map API] -> 위·경도 좌표
+ [네이버 MY플레이스] -> 업소별 메뉴, 가격, 별점, 키워드 리뷰 크롤링
+ [한국소비자원] - 외식 품목별 가격 현황.csv -> 냉면, 삼겹살, 자장면, 칼국수 등의 외식 대표 품목별 물가 현황
+ [공공데이터포털] - 서울시 OO구 음식점 현황.csv, 서울시 식품위생업소 현황.csv

### 데이터 전처리
+ 서울시 착한가격업소에 따른 데이터들을 병합
+ 서울시 일반음식점에 따른 데이터들을 병합
  + 수집되지 않은 데이터 NULL값(-) 처리
+ 외식 품목별 가격현황과 비교하기 위해 각 음식점의 메뉴를 8가지 항목으로 라벨링
  + 냉면, 비빔밥, 김치찌개, 삼겹살, 자장면, 삼계탕, 칼국수, 김밥

## 데이터 시각화 및 분석
### 자치구별 착한가격업소 현황                              
![image](https://user-images.githubusercontent.com/72624263/186717510-9c9235cb-0c04-4a78-8b34-dcf3d7c1e4ce.png)
<br>강남구/동작구/서대문구에 착한가격업소가 많이 있다.

### 식품접객업소 수 대비 착한가격업소 수
![image](https://user-images.githubusercontent.com/72624263/186717695-f278fb1d-192e-4150-b5c8-d801b0fb7722.png)
![image](https://user-images.githubusercontent.com/72624263/186717679-c8b319fe-019b-48c0-966d-77d71039727b.png)
- 상관계수=0.505689로 양의상관을 보이는것으로 보아 식품접객업소가 많은 구에 착한가격업소수도 많다고 할 수 있다.

### 서울시 착한가격업소와 일반음식점의 별점 분포
![image](https://user-images.githubusercontent.com/72624263/204282613-a74e06e4-2e59-416a-a843-477671ce5e8c.png)
![image](https://user-images.githubusercontent.com/72624263/186718479-37d28834-c7d1-4a23-ba10-f5eb7309b963.png)
- 전체적으로 4~5점 사이로 높은 별점 분포를 보이지만 착한가격업소의 별점 분포가 더 낮은것을 볼 수 있다.
  - 서울시 전체 음식점 : 약 12만 5천개
  - 표본 크기 : 1100개
  - 신뢰구간 : 95%
  - 표본오차 : 2.94%

### 착한가격업소 키워드리뷰와 별점의 상관계수
![image](https://user-images.githubusercontent.com/72624263/186718813-9907d9d5-4296-4cee-ab82-17b11f3f1773.png)
<br>※ 이때 별점은 별점*별점평가횟수로 보정하여 사용하였다.

### 일반음식점 키워드리뷰와 별점의 상관계수
![image](https://user-images.githubusercontent.com/72624263/186719127-7e062965-84bc-4899-8875-d0533fe28505.png)
- 친절, 특별한메뉴, 특별한날 등의 키워드는 상관관계가 높고 가성비는 낮은것으로 나타난다.

### 착한가격업소 현황 상위 3개구 품목별 물가비교                
![image](https://user-images.githubusercontent.com/72624263/204282483-e48cb99e-aca4-48d2-82d9-6ac2549de5fa.png)
<br>
- 착한가격업소가 제일 많이 있는 강남구의 경우 외식비에 비해 일반음식점의 가격이 높다.
- 하지만 동작구와 서대문구는 오차를 제외하더라도 외식비보다 가격이 낮은것을 볼 수 있다.<br>
※ 외식비 : 한국소비자원에서 산정하여 공개한 서울시 22년 7월 데이터<br>
※ 삼겹살의 경우 기준g이 각기 달라 비교하기 어려움이 있어 제외<br>
※ 삼계탕의 경우 비교대상이 없거나 적어서 제외

### 각 행정구별 가성비 맛집 순위
![image](https://user-images.githubusercontent.com/72624263/186719424-5911a6e6-e0ca-48b0-a504-bf31afa14abc.png)
※ 산정점수=별점평균-가격평균/10000

### 각 행정구별 착한가게업소 맵매핑                  
![image](https://user-images.githubusercontent.com/72624263/186719775-6b3cf5f3-0110-4b29-9936-34045ed48b71.png)
- 착한가격업소를 쉽게 찾을 수 있도록 지도에 표현하였다.
## 결론
### 인사이트 도출

+ 착한가격업소가 일반음식점에 비해 28%가 저렴하나 별점은 낮은분포를 보인다. 이는 요즘 소비자들이 가성비보다는 가심비를 중요시여기기 때문이라고 볼 수 있다. 별점과 키워드리뷰의 상관분석에서도 가성비(가격이 저렴해요)는 낮은 상관관계를 보였고  친절해요, 특별한메뉴가 있어요 등 가심비를 만족할 수 있는 요소는 높은 상관관계를 보였다. <br>
따라서 <b>착한가격업소의 활성화를 위해선 가심비를 잡으려는 방안이 필요</b>한 것으로 보인다. <br>
그 중 하나로 착한가격업소가 가지고 있는 사회적가치를 알리는 방안을 생각했는데, 전기차는 매번 충전소를 찾아 충전을 해야한다는 불편함이 있지만 환경이라는 사회적 가치로 많이 이용한다. 이처럼 착한가격업소를 이용하면 <b>물가안정</b>에 도움이 된다는 점을 적극적으로 알려 사람들로 하여금 만족감을 느끼게 하는것이다.<br>
+ 착한가격업소가 활성화되어 주변 음식점들의 물가안정에 영향을 끼치면 소비자들은 낮은 가격으로 높은 질의 서비스를 제공받을 수 있을 것으로 기대된다.

### 개선사항
+ 착한가격업소가 많은 구인 강남구, 동작구, 서대문구를 분석해보았을 때 동작구, 서대문구는 가격평균이 낮은것으로 나타났으나 강남구는 외식비보다 높은것으로 나타났다. 동작구, 서대문구가 가격이 낮게 나타난 것도 착한가격업소들 때문인지 지역적인 특성인지 알 수 없다. 따라서 착한가격업소의 취지인 물가안정이 제대로 적용되고 있는지 정확히 파악하기가 어렵다.
+ 착한가격업소가 소비자들에게 착한가격으로 서비스를 제공하는것 뿐만아니라 물가안정에 이바지 하고 있는지 정확히 파악하지 못해 아쉬움이 남는다. 이 점을 분석하기 위해 월 혹은 연별로 착한가격업소가 많은 지역과 아닌 지역의 물가상승률을 계산해보면 파악할 수 있지 않을까 하는 생각이 든다.

### 느낀점
- 김지훈 : 너무 재밌고 유익한 시간이었던 것 같습니다.
- 손지수 : 이번 프로젝트를 통해 코딩과 통계에서 모호하게 느껴지던 개념들을 다시 정리할 수 있어 좋았습니다.
- 이서정 : 이번 프로젝트를 수행하면서 알맞은 데이터를 찾아 수집하는 일이 쉽지않다는 것을 알게되었고 데이터를 가공, 분석해서 우리가 기획한 바를 이끌어내는 것이 무엇인지 느낄 수 있었습니다.
- 이지훈 : 이번 프로젝트를 통해서 그동안 배워왔던 것들을 잘 복습할 수 있었고, 팀워크가 얼마나 중요한지 깨닫는 좋은 시간이었습니다.
- 홍효정 : 직접 필요한 데이터를 크롤링하여 수집하고, 유용한 데이터로 정제하여 분석, 시각화를 하면서 전체적인 분석 프로세스를 조금이나마 경험할 수 있었습니다. 각 과정에서 어려움은 있었지만 팀원들끼리 합이 잘 맞아 잘 진행될 수 있었던 것 같습니다.
