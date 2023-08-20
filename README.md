# 2023 관광분야 GEN AI 해커톤
**한국관광공사 주관**

## 💻 프로젝트 주제
Chat GPT를 활용한 **개인 성향 맞춤 여행코스 추천** 애플리케이션

## 📆 개발 기간
2023.08.03 ~ 07

## 👨‍👨‍👧‍👦 팀 구성
기획1, 안드로이드2, 백엔드1, 디자인1

## 📌 주요 기능
1. **Big Five Model기반**으로 **사용자의 성격유형을 분석**
2. **생성형 인공지능(Chat GPT)을 활용**하여 **사용자 성향 맞춤 여행 코스 분석** 및 다음 여행지 추천

## 📊 프로그램 구조
![시스템 흐름도](https://github.com/yesue2/GenAI-Hackathon/assets/108323785/67e34b91-4ad7-4d78-bb30-68e2f91bda16)

## 📜 기능 설명
### 사용자의 성격유형 분석 및 결과 출력
![KakaoTalk_20230820_152314752](https://github.com/yesue2/GenAI-Hackathon/assets/108323785/5632e08f-770a-41f6-ae43-c135109158ba)
![KakaoTalk_20230820_152314752_01](https://github.com/yesue2/GenAI-Hackathon/assets/108323785/8d02005b-1a8f-49a0-8237-44ec6ca92fbd)
1. **동적인 설문지 질문 출력**: 설문지는 총 5개의 화면으로 구성되어 있으며, 사용자에게 질문을 동적으로 제공합니다. 직접 액티비티에 질문을 하드코딩하지 않고 JSON 파일에 저장된 25개의 질문을 불러와 사용자에게 표시하도록 코드를 구현하여 질문지를 쉽게 업데이트하고 관리할 수 있게 되었습니다.
2.  **효율적인 데이터처리와 네트워크 부하 최소화**: 사용자의 응답은 ViewModel을 통해 관리됩니다. AnswerModel에 모든 응답이 저장되며, 사용자가 응답을 완료할 때마다 업데이트됩니다. 사용자가 마지막 질문까지 응답을 완료하면, 앱은 ViewModel에 저장된 모든 응답을 한 번에 서버로 전송합니다. 이로써 서버와의 통신을 최소화하여 네트워크 부하를 줄이고, 더 효율적인 데이터 관리와 전송을 가능하게 하였습니다.
3. **라디오 버튼을 사용한 UX 개선**: 질문에 대한 응답은 라디오 버튼을 통해 수집하며, 클릭시 선택된 옵션은 강조 표시되어 사용자의 경험을 향상시킵니다. 또한, 모든 질문에 응답하지 않았을 경우 다음 페이지로의 이동을 제한하여 응답 누락을 방지하였습니다.
4. **Retrofit2를 통한 API 요청**: Retrofit2를 활용하여 백엔드 서버와 통신합니다. 앱은 백엔드 API 엔드포인트로 POST 요청을 전송하며, 사용자의 응답 데이터를 Request 값으로 보내어 Big Five Model을 기반으로 한 성향 분석 결과를 Response 값으로 받아오도록 코드를 구현하였습니다. 이 결과에는 사용자의 주요 성격 특성과 여행 선호도가 포함되어 사용자에게 표시됩니다.


### 코스 추천 희망 여행 정보 입력
![KakaoTalk_20230820_152314752_02](https://github.com/yesue2/GenAI-Hackathon/assets/108323785/fc038943-c1fe-43b0-9cb8-a7002824f83d)
![KakaoTalk_20230820_152314752_03](https://github.com/yesue2/GenAI-Hackathon/assets/108323785/67a06d1e-6c0f-474c-889f-f4eecfbb658e)
![KakaoTalk_20230820_152314752_04](https://github.com/yesue2/GenAI-Hackathon/assets/108323785/67a4e29a-2369-4bec-beb2-2e00ddb0a15f)
1. **동적인 지역 선택 버튼**: JSON 파일에 저장된 지역 정보를 동적으로 불러와 라디오 버튼으로 표시합니다. 사용자는 이 중 하나의 지역을 선택할 수 있습니다. 선택된 라디오 버튼은 강조 표시되어 사용자에게 선택 사항을 명확하게 보여줘 사용자 경험을 더욱 향상시키고 인터랙티브한 화면을 제공합니다.
2. **DatePickerDialog 사용**: 여행 출발일과 도착일을 선택하기 위해 각각의 버튼을 누르면 DatePickerDialog가 표시되며, 사용자가 날짜를 선택하면 해당 버튼에 선택한 날짜가 텍스트로 표시됩니다.또한 여행 출발일을 기준으로 최대 3일까지의 여행 기간을 선택할 수 있도록 구현했습니다.
3. **효율적인 데이터처리**: 사용자가 입력한 여행 정보를 모두 SharedPreferences에 저장하여 다른 액티비티에서 서버로 입력받은 데이터를 한 번에 보낼 수 있습니다. 이를 통해 여러 개의 액티비티 간에 데이터를 효율적으로 전달하고 처리할 수 있어 개발 및 유지보수에 용이합니다. 


### 추천 여행 코스 생성 로딩
![KakaoTalk_20230820_152314752_05](https://github.com/yesue2/GenAI-Hackathon/assets/108323785/411b55c5-236c-4a4c-ada2-0c3d088ec436)
1. **Lottie 애니메이션을 활용한 로딩 이미지**: 로딩 화면을 나타내기 위해 로티 애니메이션을 사용하였습니다. 사용자에게 데이터를 불러오는 동안 진행 중임을 시각적으로 보여주며, 유저 경험을 향상시키고자 구현되었습니다.
2. **Retrofit2를 통한 API 요청**: 해당 액티비티에서 Retrofit2로 백엔드 API 엔드포인트로 POST 요청을 전송해 SharedPreferences에 저장되어 있는 사용자가 입력한 여행 정보가 서버에 전달되고, 서버에서는 이 정보를 기반으로 사용자 성향 맞춤의 여행 코스가 반환됩니다.
3. **예외 처리**: API 요청이 실패했을 경우나 예외가 발생한 경우, 적절한 에러 핸들링이 이루어집니다. 에러 메시지나 로그를 출력하여 디버깅 및 사용자에게 정확한 정보를 제공하도록 처리됩니다. 서버와의 통신에 실패한 경우 사용자를 성향 선택 화면으로 다시 안내하며, 애플리케이션의 원활한 이용을 지원합니다.


### 사용자 성향 맞춤 여행 코스 생성 완료
![KakaoTalk_20230820_152314752_06](https://github.com/yesue2/GenAI-Hackathon/assets/108323785/68a22a9c-d61d-4035-b207-891c89fab179)
1. **탭 화면 구현**: 사용자가 라디오 버튼을 선택하면, 해당 날짜의 코스가 아래에 있는 TextView에 표시됩니다. 또한 라디오 버튼은 한 번에 하나만 선택될 수 있도록 제어되며, 선택된 버튼을 추적하여 이전에 선택된 버튼을 해제하여 탭 화면을 구현하였습니다.

### 추천 여행 코스 만족도 설문조사 및 다음 여행지 추천 
![KakaoTalk_20230820_152314752_08](https://github.com/yesue2/GenAI-Hackathon/assets/108323785/c6955a8b-b272-400f-9b6b-6a2cacd75cfe)
![KakaoTalk_20230820_152314752_09](https://github.com/yesue2/GenAI-Hackathon/assets/108323785/f2f370d6-3136-4c5f-abd1-578c53aa2bc5)
1.**WebView를 통한 웹 페이지 표시**: WebView를 사용하여 웹 페이지를 로드하고 화면에 표시합니다. WebSettings를 활용하여 웹 뷰 설정을 조정하고, WebViewClient를 지정하여 웹 페이지가 앱 내부에서 열리도록 합니다.
2. **다음 여행지 랜덤 추천**: JSON 파일에서 Gson 라이브러리를 사용하여 파싱한 여러 여행지 중에서 Random 클래스를 사용해 랜덤하게 하나를 선택하여 화면에 표시합니다. 랜덤 알고리즘을 통해 사용자에게 다양한 다음 여행지를 소개하게 됩니다.
