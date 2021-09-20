# Springboot와 JPA로 구현한 블로그 프로젝트
프로젝트 기간 : 2021.07.13 ~ 2021.09.20

### Reference
- [Springboot - 나만의 블로그 만들기(데어 프로그래밍)](https://www.youtube.com/playlist?list=PL93mKxaRDidECgjOBjPgI3Dyo8ka6Ilqm)

## 개발환경 ##
* Spring Boot 2.3.2
* Spring Data JPA
* lombok
* JDK 11
* JSP
* MySQL

# 요구사항
| 구분     | 내용                                    |
| :----- | ---------------------------------------- |
| 요구사항 1 | 로그인, 회원가입, 회원정보변경 |
| 요구사항 2 | 게시판 만들기                         |
| 요구사항 3 | 스프링 시큐리티 로그인                 |
| 요구사항 4 | 카카오 로그인 Oauth(라이브러리 없이 직접 하나하나 구현)    |

### 1. 로그인, 회원가입, 회원정보변경   
### 2. 게시판
* 게시글 CRUD
* 본인이 쓴 게시글이 아닐 시 수정, 삭제 못하도록 구현
* 게시글 페이징 처리
* 댓글 작성, 수정, 삭제

### 3. 스프링 시큐리티 로그인   
* 로그인하지 않은 사용자가 게시글을 작성할 경우 로그인 페이지로 리다이렉팅
* 비밀번호 해시처리
* 회원수정 시 세션도 바뀌도록 구현

### 4. 카카오 로그인 Oauth(라이브러리 사용 안하고 직접 구현)  
* 카카오 소셜 로그인일 경우 기존 회원가입과 구별하기 위해 oauth 컬럼에 kakao 추가
* 구현 순서
  1. 웹서버주소
  2. 클라이언트 키 
  3. 카카오 로그인 요청 주소 
  4. 카카오 로그아웃 요청 주소 
  5. 카카오 동의 구성
    * User 오브젝트 : id(번호), username, password, email
    * 카카오로부터 받을 정보 : profile정보(필수), email(선택)
  6. 로그인 요청 주소(GET방식) 
  7. 응답받은 코드  
  8. 토큰 발급 요청 주소(POST방식) - http body에 데이터를 전달 (4가지 데이터)

# 주요 화면
## 메인페이지
<img src="https://user-images.githubusercontent.com/52141636/133950912-a9b50737-cac7-4077-bcd4-6d0758988d2f.jpg">  
## 회원가입
카카오 회원가입일 경우 개인정보 동의 페이지로 넘어간다.  
<img src="https://user-images.githubusercontent.com/52141636/133950955-324b57f4-9b77-4953-ab4a-9746d0ec5b76.jpg">  
## 로그인
<img src="https://user-images.githubusercontent.com/52141636/133950961-45f31d04-6b38-49ed-8b05-70dd587d5dde.jpg">  
## 회원정보 수정
회원정보를 수정한 뒤 강제로 새로운 세션을 넣어 업데이트된 정보를 갱신한다.  
<img src="https://user-images.githubusercontent.com/52141636/133950972-8c783d02-de7d-4ce4-b822-8dfec9b79889.jpg">  
## 게시글 조회
<img src="https://user-images.githubusercontent.com/52141636/133950968-22174db9-c5b5-48d4-8080-d7904cf544a0.jpg">  
## 게시글 쓰기 및 수정
내가 쓴 게시글이 아닐 경우 수정과 삭제 버튼이 나타나지 않는다.  
<img src="https://user-images.githubusercontent.com/52141636/133950966-cc372d49-252d-4c93-b8f9-11a5587eb257.jpg">
