# 🐷 식단 관리 SNS 플랫폼 <살과 칼로리의 행방불명>



**저희 프로젝트 <살과 칼로리의 행방불명>은 본인의 룰에 따른 식단을 게시하면서 다른 유저들과 소통도 하고, 함께 의기투합 해 각자의 목표를 달성할 수 있도록 동기를 부여하는 SNS 플랫폼을 목표로 제작되었습니다.**

---
## ⏳ 제작 기간

- 24/05/31 ~ 24/06/07

 ---

## 기술 환경 및 스택


<img src="https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB"/> <img src="https://img.shields.io/badge/redux-%23593d88.svg?style=for-the-badge&logo=redux&logoColor=white"/> <img src="https://img.shields.io/badge/React_Router-CA4245?style=for-the-badge&logo=react-router&logoColor=white" /> <img src="https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white" /> <img src="https://img.shields.io/badge/vercel-%23000000.svg?style=for-the-badge&logo=vercel&logoColor=white" />

 ---
  
## 🧑‍💻 역할 및 업무 분담



- 박요셉(팀장)
  - 서버와의 통신 api 제작과 redux를 통한 전역 상태 관리를 위한 reducer들의 제작 담당
- 강연주
  - 개인 프로필 페이지, 게시물 생성, 수정 페이지의 UI 담당
- 강지현
  - 메인 페이지, 게시물 상세 페이지 담당
- 선지원
  - nav bar 및 회원 별 게시물을 확인할 수 있는 my Posts 페이지 담당
- 정현욱
  - 로그인, 회원가입 페이지 담당

---

## 📑 메인 페이지

- 최신순으로 각자 올린 식단을 메인 화면에 노출
- 칼로리 별로 확인 가능한 정렬 버튼

---

## 📑 상세 페이지

- 댓글 기능 구현
- instagram 등 sns들의 좋아요 기능 구현

---

## 📑 개인 프로필 페이지

- 회원별 닉네임, 이미지 수정 기능 구현
  
---

## 📑 게시물 생성, 수정 페이지

- SNS 포스트를 생성 그리고 수정할 수 있도록 페이지로 구현
---



## 📑 MyPosts 페이지
- 회원별, 나의 게시물만 모아서 확인할 수 있도록 구현
---



## 📑 로그인, 회원가입 페이지
- supabase의 auth api를 활용하여 로그인, 회원가입 구현

---

## 📑 페이지 구성

- 메인 페이지
- 사용자 개인 페이지

  - 회원별 게시물 페이지
  - 회원 정보 페이지

- 게시물 관련 페이지

  - 게시물 생성 페이지
  - 게시물 수정 페이지
  - 게시물 상세 정보 페이지

- 인증 관련 페이지
  - 로그인 페이지
  - 회원가입 페이지



---
## 부가 라이브러리


<img src="https://img.shields.io/badge/styled--components-DB7093?style=for-the-badge&logo=styled-components&logoColor=white"/> 

- Redux-persist
- uuid

---

# Trouble Shooting

 ## 문제 확인 : postlist 페이지에서 사용자가 포스트 삭제 버튼을 클릭해도 삭제되지 않음
  1. 문제 재현을 위해 다시 삭제 버튼을 클릭해보기
  2. 어떤 에러가 발생했는지 확인하기 위해 브라우저 콘솔을 확인하기
  3. 에러가 발생한 삭제 버튼 클릭 이벤트 핸들러와 관련된 코드 검토하기
  4. 여러가지 가설을 설정: 클릭이벤트가 발생한 포스트의 id를 넘겨주지 않은건지 / 요청이 제대로 전송되지 않은건지
  5. 가설 검증하기: 이벤트핸들러 콘솔에 넘겨받은 id가 잘 출력되는지 확인하기 / 네트워크 탭 확인하기
  6. 문제 해결: 이벤트핸들러의 인자로 잘못된 id가 넘겨진 것을 확인하고, 오류 수정
  7. 유사한 문제가 발생하지 않도록 발생했던 문제와 해결방법에 대해 잘 기록해두기(e.g 코드리뷰)

 ## 문제 확인 : 수정 페이지에서 게시글을 수정했을 때 수정된 글이 목록에 바로 반영 안 됨
  1. 문제 재현을 위해 게시글을 여러 개 생성하고 수정하고 글 목록으로 돌아와서 확인
  2. 새로 고침을 했을 때만 수정된 사항이 반영되는 것을 확인
  3. 설정한 가설들 :
    (1) 새로 고침 했을 때 반영이 되니까 수정을 완료하고 글 목록 페이지로 이동하면 나오지 않을까?
    (2) 페이지 최초 렌더링시 게시글들을 불러오는 함수로 글을 한 번 불러오는데 이때, 글을 수정하고 DB에 수정된 사항을 저장하고 게시글을 한 번더 불러와야 바로 반영이 되지 않을까?
  4. 가설 확인 및 문제 해결:
    (1) 수정을 완료하고 useNavigate를 이용해 글 목록 페이지로 돌아가도 바로 반영이 안되고 새로 고침을 해줘야 반영이 됨 => 단순히 페이지 이동으로 해결 안 됨
    (2) 수정을 완료하고 함수를 이용해 다시 게시글을 불러오고 페이지도 글 목록 페이지로 이동 => 수정을 하고 글 목록에 바로 반영됨 (문제 해결)
  5. 문제 재발 방지를 위해서 문제 해결을 위한 로직 기록 및 앞으로 특정한 작업을 성공한 이후의 로직도 생각하기

 ## 문제 확인 : 페이지 로드 시 데이터가 들어오지 않으면 에러발생 현상
  1. 문제 재현을 위해 다시 페이지 새로고침하여 확인
  2. 어떤 에러가 발생했는지 확인하기 위해 브라우저 콘솔 확인
  3. 에러가 발생한 관련 코드 확인
  4. 여러가지 가설을 설정: 새로고침을 하였을때 데이터가 안들어 온것인가 아니면 들어왔는데 못 불러온것인가
  5. 가설 검증하기: 콘솔로 데이터가 제대로 넘어왔나 확인
  6. 문제 해결: 옵셔널 체이닝을 사용하여서 null, undifined의 경우에만 동작 할 수 있도록 코드를 수정하였다.
  7. 문제가 재발 방지를 위해서 문제해결 로직을 기록하여 관리