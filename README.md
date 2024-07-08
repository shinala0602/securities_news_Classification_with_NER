# securities_news_Classification_with_NER
## 증권 뉴스 분류 및 개체명 인식
* [네이버 증권 뉴스 유형별 크롤링, 1만개 이상](https://finance.naver.com/news/news_list.naver?mode=LSS3D&section_id=101&section_id2=258&section_id3=401)
* [한국해양대학교 자연어처리연구실 개체명 데이터](https://github.com/kmounlp/NER)
  
### KoBERT 모델
* 뉴스 기사, 위키피디아 등 대규모 코퍼스로 사전 학습 된 한국어 특화 BERT 모델
* 뉴스의 타이틀을 분류하고 개체명을 인식하는 프로젝트이기에 KoBERT 모델 사용

### 타이틀 분류 모델
* 크롤링한 증권 뉴스 데이터를 사용해 학습
* 정확도 76%의 성능을 보임. 1만개 정도의 데이터를 나누어 학습과 검증에 사용했기에 더 많은 데이터로 학습시킨다면 더 높은 성능을 보일 것으로 보임
<img width="426" alt="image" src="https://github.com/shinala0602/securities_news_Classification_with_NER/assets/59050396/c07e81d7-2fae-420f-bcba-bae89f778b5d">
<img width="249" alt="image" src="https://github.com/shinala0602/securities_news_Classification_with_NER/assets/59050396/d496b6af-1639-411e-8879-dbe4d83fb1b9">


### 개체명 인식 모델
* 한국해양대학교 자연어처리연구실에서 제작한 개체명 형태소 말뭉치 데이터를 사용해 학습
* 뉴스 타이틀의 특성상 간결한 정보만 담고있기에 인명(PER), 기관명(ORG), 통화(MNY)만 인식되도록 말뭉치 전처리 진행
* 정확도 96%의 성능을 보임
* 하지만, 기관명 외로 인명 및 통화에 대한 학습은 제대로 되지 않음. 더불어, 기관명 또한 단어의 첫글자는 인식되지 않는 문제 발생.
* 말뭉치 데이터의 수가 적었고 추가로 학습시킨 데이터가 한국 상장기업의 데이터였기에 기관명에 더 과적합되었을 것이라 판단
<img width="397" alt="image" src="https://github.com/shinala0602/securities_news_Classification_with_NER/assets/59050396/4a5f5160-e16b-4d88-8399-beb692d7a484">
<img width="399" alt="image" src="https://github.com/shinala0602/securities_news_Classification_with_NER/assets/59050396/619db983-adc4-4231-92f0-8a214cbd975a">

### 느낀점  
* 자연어를 처리하는 모델은 많은 양의 데이터 학습이 충분히 있어야 좋은 성능을 확인할 수 있다.
* 개체명 인식의 경우 수 작업으로 개체명에 라벨링해야 하기 때문에 기술적으로 개체명을 라벨링해주는 연구를 진행해보면 좋을 것 같다.
* 두 모델을 LangChain으로 연결하여 사용자 경험을 더 높일 수 있는 서비스 개발이 될 수 있을 것 같다.
