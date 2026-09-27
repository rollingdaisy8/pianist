# Piano Loop Coach V1

개인 피아노 연습용 정적 웹앱 프로토타입입니다.

## 포함 기능
- YouTube 링크를 곡 보관함에 저장
- 로컬 오디오/영상 파일을 IndexedDB에 저장
- 재생 위치를 기준으로 마디/구간 시작·끝 지정
- 저장한 구간 반복 재생
- 마이크로 내 연주 녹음
- 구간별 녹음 저장 및 재생
- Gemini API key를 직접 입력해 곡/구간 분석
- 곡 메타데이터/마디/AI 분석 JSON 백업 및 복원
- Storage Persistence 요청 버튼

## 실행
가장 간단한 방법은 GitHub Pages에 `index.html`로 올리는 것입니다.
마이크 녹음은 일반적으로 HTTPS 또는 localhost 환경이 필요합니다.

## 곡 보관 방식
- YouTube 곡: 링크/ID와 연습 데이터만 저장
- 로컬 파일: 브라우저 IndexedDB에 파일 Blob 자체를 저장
- 같은 브라우저 + 같은 사이트 origin에서는 HTML 코드를 업데이트해도 IndexedDB는 유지됩니다.
- 브라우저 사이트 데이터 삭제, 기기 변경, 도메인/포트 변경 시에는 데이터가 이어지지 않을 수 있습니다.
- JSON 백업은 로컬 미디어 파일 자체를 포함하지 않습니다.

## Gemini API
V1은 프런트엔드 프로토타입이므로 API key를 화면에서 직접 입력합니다.
키는 앱에 저장하지 않지만, 프로덕션 서비스에서는 반드시 서버 프록시를 두고 키를 서버에 보관하세요.
현재 코드는 `gemini-3.8-flash` generateContent REST endpoint를 사용합니다.
