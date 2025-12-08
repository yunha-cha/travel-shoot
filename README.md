# ✈️ Travel Shoot - AI 기반 원스톱 숙박 예약 서비스

**끊김 없는 여행, AI가 완성하는 나만의 여행 플래너**

[![Deployment](https://img.shields.io/badge/Deployed-travelshoot.store-blue)](https://travelshoot.store)
![GPT-5](https://img.shields.io/badge/GPT--5-412991?logo=openai)
![React](https://img.shields.io/badge/React-19.1-61DAFB?logo=react)
![Vite](https://img.shields.io/badge/Vite-5.4.9-646CFF?logo=vite)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5.6-6DB33F?logo=springboot)



---

## 📋 프로젝트 개요

### 🌟 서비스 소개
Travel Shoot은 숙소 예약부터 맞춤형 여행 코스 생성까지 **원스톱으로 제공하는 AI 기반 여행 솔루션**입니다. 
사용자의 여행 스타일을 분석하여 개인화된 숙소를 추천하고, 예약 완료 시 숙소, 맛집, 관광지를 기준으로 최적의 여행 코스를 생성합니다.

### 📈 기획 배경

**여행 계획의 3가지 문제점**
- ⏰ **시간 소모**: 평균 4-5시간이 소요되는 여행 계획 과정
- 🔍 **정보 분산**: 숙소, 맛집, 관광지 정보가 각기 다른 플랫폼에 분산
- 🎯 **획일적 추천**: 개인 취향을 고려하지 않은 검색 결과

**온라인 여행 시장 성장**
- 2024년 전 세계 온라인 여행 시장: 658.4억 달러
- 2028년 예상 규모: 807.9억 달러
- 온라인 판매 채널 점유율: 74% (2027년 예상)

**기존 서비스의 한계**
- 하나투어: 숙소 예약 후 별도 일정 작성 필요
- 트리플: AI 일정 생성과 숙소 예약이 분리, 구글맵 연동 불완전
- 여행콕콕: 일정 수정 불가, 최대 2박 3일로 제한


### 📅 개발 일정
**총 개발 기간**: 2025년 8월 25일 ~ 11월 20일 (약 3개월, 13주)

| 기간 | 단계 | 주요 활동 |
|------|------|-----------|
| 08.25 - 09.15 | 🎯 프로젝트 기획 및 설계 | 요구사항 분석, 시스템 아키텍처 설계, DB 스키마 설계, UI/UX 설계 |
| 09.16 - 11.07 | 🛠️ 핵심 기능 개발 | React 프론트엔드 개발, Spring Boot 백엔드 API, AI 모델 연동, Docker 환경 구성 |
| 11.08 - 11.20 | 🧪 통합 테스트 및 배포 | 전체 시스템 통합 테스트, AWS 배포 환경 구성, QA 및 문서화 |

---

## ✨ 주요 기능

### 🎮 AI 기반 개인화 추천
- **설문조사 기반 맞춤 추천**: 선호 지역, 여행 목적, 음식 취향, 액티비티 선호도 수집
- **4단계 사용자 분류**: 신규 → 라이트 → 라이트-미들 → 헤비 (예약 건수 기반)
- **동적 가중치 전략**: 설문(70%→20%) + 예약(30%→70%) + 평점(10%) 비율 조정
- **실시간 AI 스코어링**: 가중치 × 100 + 평점 × 10 - 거리 기반 매칭 점수 계산

### 🔍 통합 검색 시스템
- **실시간 자동완성**: 지역명/숙소명 검색 시 Debounce 적용
- **다중 필터링**: 가격, 평점, 숙소 유형, 편의시설 조합 검색
- **무한 스크롤**: React Query 캐싱 + Observer 기반 페이징 (20개씩 로드)
- **URL 파라미터 통일**: 모든 페이지 검색 조건 유지 및 공유 가능

### 🤖 AI 여행 코스 자동 생성
- **GPT-5 기반 코스 생성**: 숙소 주변 맛집·관광지 데이터 분석
- **6단계 완화 전략**: 평점 4.0+ 20km → 3.5+ 30km 단계적 필터링
- **Haversine 공식 적용**: 실제 거리 기반 장소 추천 (최대 20km 반경)
- **일자별 탭 구성**: DAY1, DAY2, DAY3 시간대별 동선 시각화
- **카카오맵 연동**: 실시간 위치 확인 및 경로 안내

### 📊 AI 리뷰 요약
- **GPT-5 감정 분석**: 리뷰 텍스트 기반 장점/단점 자동 추출
- **중복 호출 방지**: 리뷰 개수 변경 시에만 AI 재요약
- **구조화된 응답**: JSON 형식 강제 파싱으로 안정성 확보
- **6가지 세부 별점**: 청결도, 편의성, 체크인, 의사소통, 위치, 가성비

### 💳 간편 예약 · 결제
- **카카오페이 QR 결제**: 3단계 간편 예약 (선택 → 정보 → 결제)
- **요일별 차등 금액**: 주말/평일 자동 계산 및 표시
- **실시간 재고 관리**: 체크인/체크아웃 날짜 기반 객실 잔여 확인
- **약관 체크박스**: 필수/선택 약관 모달 제공

### 📍 지도 기반 위치 서비스
- **카카오맵 API 통합**: 숙소·맛집·관광지 마커 표시
- **실시간 검색**: 지역별 맛집·관광지 페이징 처리
- **마커 인터랙션**: 숙소 클릭 시 상세 페이지 이동, 맛집·관광지는 카카오맵 연동

---

## 🏗️ 시스템 아키텍처

### 기술 스택

#### Frontend
![React](https://img.shields.io/badge/React-19.1-61DAFB?logo=react)
![Vite](https://img.shields.io/badge/Vite-5.4.9-646CFF?logo=vite)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3.7-7952B3?logo=bootstrap)

#### Backend
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5.6-6DB33F?logo=springboot)
![Spring Security](https://img.shields.io/badge/Spring_Security-3.5.2-6DB33F?logo=springsecurity)
![Spring Data JPA](https://img.shields.io/badge/Spring_Data_JPA-3.5.4-6DB33F)
![Java](https://img.shields.io/badge/Java-21-007396?logo=openjdk)

#### Database
![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?logo=mysql)
![Redis](https://img.shields.io/badge/Redis-7.0-DC382D?logo=redis)

#### External AI
![GPT-5](https://img.shields.io/badge/GPT--5-412991?logo=openai)

#### Deploy
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker)
![AWS EC2](https://img.shields.io/badge/AWS_EC2-FF9900?logo=amazonec2)
![AWS S3](https://img.shields.io/badge/AWS_S3-569A31?logo=amazons3)
![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx)

#### Collaboration
![GitHub](https://img.shields.io/badge/GitHub-181717?logo=github)
![Git](https://img.shields.io/badge/Git-F05032?logo=git)
![Notion](https://img.shields.io/badge/Notion-000000?logo=notion)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-34A853?logo=googlesheets)
![Figma](https://img.shields.io/badge/Figma-F24E1E?logo=figma)

### 아키텍처 구조
<img width="1055" height="460" alt="image" src="https://github.com/user-attachments/assets/41618d05-5004-47e3-a459-d446c6e3857e" />


### CI/CD 파이프라인
<img width="1086" height="467" alt="image" src="https://github.com/user-attachments/assets/3de5e43b-cc81-4f53-9a98-1eae9710cb29" />

---

## 🚀 빠른 시작

### 사전 요구사항
- Java 21+
- Node.js 18+
- Docker & Docker Compose
- MySQL 8.0+
- Redis 7.0+

### 개발 환경 구축

```bash
# 1. 저장소 클론
git clone https://github.com/your-repo/travel-shoot.git
cd travel-shoot

# 2. Docker 환경 실행
cd ./docker
docker-compose build
docker-compose up -d

# 3. 환경 변수 설정 (.env 파일 생성)
# Backend
SPRING_DATASOURCE_URL=jdbc:mysql://localhost:3306/travelshoot
SPRING_DATASOURCE_USERNAME=your_username
SPRING_DATASOURCE_PASSWORD=your_password
REDIS_HOST=localhost
REDIS_PORT=6379
OPENAI_API_KEY=your_openai_api_key
KAKAO_MAP_API_KEY=your_kakao_map_key
KAKAO_PAY_API_KEY=your_kakao_pay_key
AWS_S3_BUCKET=your_s3_bucket_name
AWS_ACCESS_KEY=your_aws_access_key
AWS_SECRET_KEY=your_aws_secret_key

# Frontend
VITE_API_URL=http://localhost:8080
VITE_KAKAO_MAP_KEY=your_kakao_map_key

# 4. 애플리케이션 실행
# Backend
cd backend
./gradlew bootRun

# Frontend
cd frontend
npm install
npm run dev
```

### 배포 환경 접속
- **배포 URL**: https://travelshoot.store
---

## 📋 명세서

### ERD
- **테이블 수**: 19개
- **속성 수**: 198개
- [상세 ERD 다이어그램 보기](https://github.com/user-attachments/assets/85035d02-6622-4f13-8f8c-f0570ba17495)

### 요구사항 정의서
- **주요 기능**: 14개
- **상세 기능**: 64개
- [요구사항 정의서 보기](https://docs.google.com/spreadsheets/d/e/2PACX-1vRdllEawJ-PdiMA68Uhi32ZgmDz3x5GrX2QxYZdHGgg26cKxGMV1SL3Q1VoJjVTwxeEi5krivUfu9_m/pubhtml)

### 유스케이스 다이어그램
- [유스케이스 다이어그램 보기](https://github.com/user-attachments/assets/4181d58e-bb10-44bf-84df-ed070ec9256c)

---

## 🎨 화면 구성 및 시연

### 메인 페이지 & 숙소 추천

| AI 맞춤 추천 숙소 | 인기 급상승 숙소, 가격 착한 숙소 |
|:---:|:---:|
| ![AI 추천 숙소](https://github.com/user-attachments/assets/4d92168a-3461-47bd-9335-f6f72e57e0b9) | ![인기 급상승 숙소, 가격 착한 숙소](https://github.com/user-attachments/assets/9f522901-fb4e-4174-ad5a-5c68571c8aca) |

---

### 통합 검색 & 목록

| 통합 검색 | 다중 필터링 |
|:---:|:---:|
| ![통합 검색](https://github.com/user-attachments/assets/50da0836-81f0-4afa-abfd-11e2750f1cec) | ![다중 필터링](https://github.com/user-attachments/assets/64cc8e0f-566d-4d44-ab65-1c7a7f729a52) |

---

### 숙소 정보 & AI 리뷰

| 숙소 정보 | 객실 정보 | AI 리뷰 요약 |
|:---:|:---:|:---:|
| ![숙소 상세](https://github.com/user-attachments/assets/c4ec7a2f-6812-4f47-9480-f24e473c8990) | ![객실 상세](https://github.com/user-attachments/assets/81ef77ca-825c-4073-a527-87f59d44fe2f) | ![AI 리뷰 요약](https://github.com/user-attachments/assets/99a6cdb1-6907-4650-b674-646658fac2b2) |

---

### 사용자 숙박 리뷰


| 리뷰 작성 | 별점 통계 | 리뷰 목록 |
|:---:|:---:|:---:|
| ![리뷰 작성](https://github.com/user-attachments/assets/3f156317-b346-48c3-9735-663c1a6e30d4) | ![별점 통계](https://github.com/user-attachments/assets/47bae792-4369-41a0-a95f-6fcf683e3e2b) | ![리뷰 목록](https://github.com/user-attachments/assets/8675b6a3-9174-45c7-9784-de6b6a54438e) |

---

### 예약 & 결제

| 예약 정보 입력 | 카카오페이 QR 결제 | 예약 완료 |
|:---:|:---:|:---:|
| ![예약 정보 입력](docs/screenshots/booking-1.png) | ![카카오페이 결제](docs/screenshots/booking-2.png) | ![예약 완료](docs/screenshots/booking-3.png) |

---

### AI 여행 코스 생성

| AI 코스 자동 생성 | 일자별 상세 일정 | 카카오맵 연동 |
|:---:|:---:|:---:|
| ![AI 코스 생성](docs/screenshots/course-1.png) | ![일정 상세](docs/screenshots/course-2.png) | ![지도 연동](docs/screenshots/course-3.png) |

---

### 사용자 맞춤 설문조사

| 선호 지역 선택 | 숙박 유형 선택 | 음식 취향 선택 | 액티비티 선택 |
|:---:|:---:|:---:|:---:|
| ![설문조사1](docs/screenshots/survey-1.png) | ![설문조사2](docs/screenshots/survey-2.png) | ![설문조사3](docs/screenshots/survey-3.png) | ![설문조사4](docs/screenshots/survey-4.png) |

---

### 반응형 디자인

| Desktop (1024px~) | Tablet (768px~) | Mobile (470px~) |
|:---:|:---:|:---:|
| ![Desktop](docs/screenshots/responsive-desktop.png) | ![Tablet](docs/screenshots/responsive-tablet.png) | ![Mobile](docs/screenshots/responsive-mobile.png) |

<p align="center"><i>모든 디바이스에서 일관된 사용자 경험 제공</i></p>

---

## 📈 프로젝트 성과

### 📊 개발 지표
- **총 개발 기간**: 약 3개월 (4명 팀원)
- **개발 완료 기능**: 14개 주요 기능 / 60+ 세부 기능
- **프론트엔드 코드**: 43,700+ lines
- **백엔드 코드**: 12,400+ lines
- **RESTful API**: 58개 구현

### 🎯 핵심 성과

**1. 풀스택 설계 및 개발**
- React + Spring Boot 기반 확장 가능 시스템 설계
- MySQL + Redis 이중 DB로 응답 속도 개선
- RESTful API 58개 구현

**2. AI 기반 자동화 달성**
- 여행 코스 자동 생성으로 계획 시간 **90% 단축**
- 5개 이상 리뷰 AI 요약으로 정보 파악 시간 절감
- 4단계 설문 기반 개인화 추천 시스템 구현

**3. 사용자 경험 최적화**
- 카카오맵 API 전면 통합으로 UX 일관성 확보
- 무한 스크롤 + 실시간 검색으로 이탈률 감소
- 반응형 UI로 모든 디바이스 지원

**4. 안정성 및 성능 강화**
- 트랜잭션 관리로 데이터 정합성 보장
- 에러 핸들링으로 서비스 안정성 확보
- 통합 테스트로 안정성 검증

### 🔥 End-to-End 사용자 플로우 100% 구현

```
회원가입 → 설문조사 → 개인화 추천 → 검색/필터링 
   → 예약 → AI 여행코스 → 리뷰작성
```

**끊김 없는 원스톱 핵심 여정 완성**: 여행의 모든 과정을 하나의 플랫폼에 담아 처음부터 끝까지 완전한 여행 경험 제공

---

## 📊 프로젝트 차별점

### Travel Shoot vs 기존 플랫폼

| 비교 항목 | 기존 숙박 예약 플랫폼 | **Travel Shoot** |
|-----------|------------------------|------------------|
| 추천 방식 | 규칙 기반 추천 | ✅ **AI 기반 개인 맞춤 추천** |
| 리뷰 가독성 | 많은 리뷰 혼재, 가독성 저하 | ✅ **AI 리뷰 분석 및 핵심 요약 제공** |
| 여행 계획 | 숙박만 예약, 맛집·관광지 별도 검색 | ✅ **숙박·맛집·관광지 통합 제공** |
| 사용자 경험 | 여러 플랫폼 비교 필요 | ✅ **원스톱 통합 검색 플랫폼** |

**예상 결과**: 예약까지 시간 소요 감소 → 사용자 만족도 및 예약 효율 증가

---

## 🚀 향후 발전 계획

### 단기 계획 (3개월 이내)
- 🌐 **공공데이터포털 연동**: 전국 단위 숙소·관광지·맛집 데이터 확장
- 🔍 **검색 성능 향상**: Elasticsearch 도입으로 Full-Text Search 최적화
- 💬 **챗봇 도입**: 24/7 고객 문의 응대 자동화

### 중기 계획 (6개월 이내)
- 👥 **그룹 예약 기능**: 다인원 여행 예약 시스템 구축
- 📦 **CDN 캐싱**: 정적 리소스 캐싱으로 글로벌 응답 속도 개선
- 🔒 **예약 진행 상태 추적**: 실시간 예약 상태 알림 및 중복 방지

### 장기 계획 (1년 이내)
- 💰 **동적 가격 책정 알고리즘**: 수요 예측 기반 실시간 가격 조정
- 🤝 **협업 필터링**: 유사 사용자 기반 리뷰 우선순위 정렬
- 🏨 **편의시설 기반 맞춤 검색**: 세부 편의시설 필터 강화

---

## 🤝 팀원 소개 및 역할

<table>
  <tr>
    <td align="center" width="25%">
      <b>김이슬</b><br/>
      PM & 풀스택 개발<br/><br/>
      • Spring Security 인증/인가 시스템<br/>
      • 검색 서비스 풀스택 개발<br/>
      • 통합 헤더 풀스택 개발<br/>
      • 카카오페이 결제 연동<br/>
      • 예약 시스템 풀스택 개발
    </td>
    <td align="center" width="25%">
      <b>이은비</b><br/>
      인프라 구축 & 풀스택 개발<br/><br/>
      • OpenAI 기반 여행 코스 생성<br/>
      • 예약 상세 서비스 풀스택 개발<br/>
      • 마이페이지 풀스택 개발<br/>
      • 카카오맵 연동 구현<br/>
      • Docker 환경 구성
    </td>
    <td align="center" width="25%">
      <b>차윤하</b><br/>
      DB 설계 & 풀스택 개발<br/><br/>
      • OpenAI 기반 리뷰 요약<br/>
      • 리뷰 시스템 풀스택 개발<br/>
      • 숙소 상세 서비스 풀스택 개발<br/>
      • 데이터베이스 설계 및 최적화<br/>
      • Amazon S3 이미지 업로드
    </td>
    <td align="center" width="25%">
      <b>박은채</b><br/>
      인프라 총괄 & 풀스택 개발<br/><br/>
      • OpenAI 기반 숙소 추천<br/>
      • 메인 페이지 풀스택 개발<br/>
      • 설문조사 서비스 풀스택 개발<br/>
      • AWS 클라우드 배포 및 운영<br/>
      • Amazon S3 파일 관리 시스템
    </td>
  </tr>
</table>

---

### 기여 방법

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 🙏 감사의 말

**Travel Shoot**은 **개인 맞춤형 AI 추천과 원스톱 여행 솔루션을 통한 사용자 경험 혁신**을 목표로 합니다.
온라인 여행 시장의 성장 속에서 기존 플랫폼의 한계를 극복하고, 
사용자가 **숙소 예약부터 여행 계획까지 끊김 없이 완성할 수 있는 통합 플랫폼**을 제공합니다.
프로젝트를 함께 완성해 준 팀원들, 올바른 방향으로 이끌어주신 서정희 멘토님, 
그리고 기술적 기반을 다질 수 있도록 가르쳐 주신 허진경 강사님께 깊은 감사를 드립니다.
---

## 📄 License

© 2025 Travel Shoot. All rights reserved.

---

<div align="center">
  <h3>✈️ 함께 만들어가는 소중한 여행, Travel Shoot과 함께하세요 </h3>
  <p><i>"예약 한 번으로 완성되는, 나만의 AI 여행 플래너"</i></p>
</div>
