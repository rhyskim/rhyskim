# 김민재 · Coffee_Driven_Dev

### AI를 실제 서비스에 붙이는 백엔드 · 웹 개발자를 목표로 합니다

충남대학교 컴퓨터공학과 4학년

> 🇰🇷 한국어 | [🇺🇸 English](./README_EN.md) *(준비 중)*

<br/>

<!-- TODO: GPA/자격증/어학 등 공개할 지표가 있다면 아래 형식으로 배지 추가
![GPA](https://img.shields.io/badge/GPA-0.00%20/%204.5-1f6feb?style=for-the-badge)
-->

[![Blog](https://img.shields.io/badge/Blog-rhyskim.github.io-000000?style=for-the-badge&logo=github&logoColor=white)](https://rhyskim.github.io/)
[![Email](https://img.shields.io/badge/Email-rhyskim@naver.com-03C75A?style=for-the-badge&logo=naver&logoColor=white)](mailto:rhyskim@naver.com)

</div>

---

## About Me

백엔드와 웹 서비스를 만드는 것을 기본기로 삼고, 여기에 AI/ML을 붙여 실제로 동작하는 제품을 만드는 데 관심이 있습니다.
온디바이스 AI 경량화, 서버-클라이언트 간 추론 책임 분리, 데이터베이스 계층에서의 무결성 보장을 직접 구현하며 배우고 있습니다.

개발할 때 아래 기준을 지키려 합니다.

- **AI는 기능이 아니라 서비스의 일부로 통합하기** — 추론을 어디서 실행할지, 실패하면 무엇을 보장할지부터 설계
- **DB·서버 계층에서 무결성을 보장하기** — 애플리케이션 로직만이 아니라 제약·트리거·트랜잭션으로도 지키기
- **궁금한 내용은 끝까지 알아내기** — 동작 원리를 이해하지 못한 코드는 남기지 않기

### Currently Working On

- **Kakao Tech Campus** — Kakao가 주최하는 부트캠프로 프론트엔드/백엔드/AI Agent 설계/프로젝트의 기획부터 배포까지의 전 과정을 학습 중입니다.
- On-Device AI를 활용한 보안에 문제 없이 **검색 가능한 갤러리** 개발 프로젝트 진행 중
- **브릿지 프로그램 개발 중** - 세부 내용은 프로젝트 배포 후 공개 예정 

---

# Projects

## 1. Seoul Landmark Assistant — 온디바이스 AI 랜드마크 인식 앱

<sub><!-- TODO: 기간(YYYY.MM ~ YYYY.MM) · 팀 인원 / 담당 역할 --> 팀 프로젝트 · 담당: 백엔드 · 모델 통합</sub>

<!-- 대표 화면 1장 -->
<p align="center">
  <img width="300" height="600" alt="Screenshot_20260822_144545_Gallery" src="https://github.com/user-attachments/assets/6675fa99-011f-404e-9a9d-3d9ea8a8e7b0" alt="Seoul Landmark Assistant 메인 화면" />
  <img width="300" height="600" alt="Screenshot_20260822_144605_Gallery" src="https://github.com/user-attachments/assets/5486aed2-d321-451c-9486-5ea9781726a8" alt="랜드마크 인식 결과 화면" />

![Inference](https://img.shields.io/badge/Inference-On--Device-238636?style=flat-square)
![Model](https://img.shields.io/badge/MobileCLIP2--S3-FP16-8E75B2?style=flat-square)
![Landmarks](https://img.shields.io/badge/Landmarks-25-1f6feb?style=flat-square)

- **네트워크가 끊긴 상황에서도 인식이 동작해야 해서** 추론을 서버가 아닌 단말에 두고, 서버는 인증·제보·검색 로그·통계만 담당하도록 책임을 분리했습니다.
- **MobileCLIP2-S3 FP16 모델을 ONNX Runtime으로 단말에서 실행**하여 25개 서울 랜드마크(궁궐 세부 건물 포함)를 분류합니다.
- **중복 로그인 방지를 위해 "1기기 1계정" 정책**을 적용해, 새 기기에서 로그인하면 기존 푸시 토큰을 무효화하도록 FCM 등록 로직을 구성했습니다.
- 검색 로그에 **모델 버전 · 추론 백엔드 · Top-3 스코어 · 지연시간(latency)**을 함께 기록해, 배포 후에도 인식 품질을 추적할 수 있게 했습니다.
- <!-- TODO: 정량 결과 1줄 추가 (예: "테스트셋 기준 Top-1 정확도 __%, 단말 평균 추론 __ms") -->
- <!-- TODO: 트레이드오프 1줄 추가 (예: 모델 크기를 줄이며 포기한 것, 남은 과제) -->

<p>
  <img src="https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white" alt="Flutter"/>
  <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white" alt="FastAPI"/>
  <img src="https://img.shields.io/badge/ONNX%20Runtime-005CED?style=flat-square&logo=onnx&logoColor=white" alt="ONNX Runtime"/>
  <img src="https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white" alt="SQLAlchemy"/>
  <img src="https://img.shields.io/badge/Firebase%20FCM-FFCA28?style=flat-square&logo=firebase&logoColor=black" alt="Firebase FCM"/>
</p>

[![Repo](https://img.shields.io/badge/Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/rhyskim/landmark-on-device-ai-app)

---

## 2. CNU Airline — 공항 예약 시스템

<sub><!-- TODO: 기간 · 팀 인원 / 담당 역할 --> 팀 프로젝트 · 담당: DB 설계 · 백엔드</sub>

<p align="center">
  <img width="900" height="440" alt="image" src="https://github.com/user-attachments/assets/5f130535-734c-40f8-afee-b675c0fa479d" alt="항공편 검색 화면" />
  <img src="assets/projects/airline-admin.png" alt="관리자 대시보드 화면" width="300"/>
</p>

![DB](https://img.shields.io/badge/Oracle-OCI-F80000?style=flat-square)
![Integrity](https://img.shields.io/badge/Integrity-Trigger%20%2B%20Constraint-238636?style=flat-square)
![Role](https://img.shields.io/badge/Role-Admin%20%2F%20User-1f6feb?style=flat-square)

- **좌석 중복 예약 같은 무결성 문제는 애플리케이션 로직만으로는 완전히 막을 수 없다고 판단해**, Oracle의 참조 무결성(cascading delete)과 이벤트 트리거로 좌석 잔여석을 실시간 동기화하도록 DB 계층에서 보장했습니다.
- Next.js App Router 기반으로 **일반 사용자 / 관리자 역할 분리 인증**을 구현했습니다.
- 예매 완료 시 **e-티켓 자동 이메일 발송**, 관리자용 **운영 통계 대시보드**를 구성했습니다.
- 스키마와 샘플 데이터를 `/database/create_and_insert.sql`에 정리해 누구나 동일한 환경에서 재현할 수 있게 했습니다.
- <!-- TODO: 정량 결과 1줄 추가 (예: 테이블 __개, 트리거 __개, 항공편 검색 응답시간 등) -->

<p>
  <img src="https://img.shields.io/badge/Next.js%2015-000000?style=flat-square&logo=nextdotjs&logoColor=white" alt="Next.js 15"/>
  <img src="https://img.shields.io/badge/React%2019-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React 19"/>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript"/>
  <img src="https://img.shields.io/badge/Tailwind%204-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white" alt="Tailwind CSS 4"/>
  <img src="https://img.shields.io/badge/Oracle-F80000?style=flat-square&logo=oracle&logoColor=white" alt="Oracle"/>
</p>

[![Repo](https://img.shields.io/badge/Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/rhyskim/AirLine_DB)

---

## 3. LPCVC 2026 Track 1 — 온디바이스 AI 경량화 대회

<sub><!-- TODO: 기간 · 팀 인원 / 담당 역할 --> Qualcomm LPCVC 2026 · 진행 중</sub>

<p align="center">
  <img src="assets/projects/lpcvc-pipeline.png" alt="학습-경량화-배포 파이프라인 다이어그램" width="620"/>
</p>

![Status](https://img.shields.io/badge/Status-In%20Progress-d4a72c?style=flat-square)
![Task](https://img.shields.io/badge/Task-Image--Text%20Retrieval-1f6feb?style=flat-square)
![Target](https://img.shields.io/badge/Target-Qualcomm%20AI%20Hub-8E75B2?style=flat-square)

- **Knowledge Distillation → ONNX Export → Qualcomm AI Hub 컴파일/프로파일링 → 추론**으로 이어지는 전체 파이프라인을 구성했습니다.
- ViT-S-16, MobileCLIP2-S4(듀얼 티처 distillation), SigLIP2-Base 세 가지 학생 모델로 정확도-지연시간 트레이드오프를 비교하고 있습니다.
- **Seoul Landmark Assistant 앱에 필요한 온디바이스 추론 경험**이 이 대회에서 모델을 경량화하고 프로파일링하는 과정과 직접 연결됩니다.
- <!-- TODO: 정량 결과 1줄 추가 (예: 베이스라인 대비 정확도 변화, 지연시간(ms), 모델 크기(MB), 대회 내 순위) -->
- <!-- TODO: 트레이드오프 1줄 추가 -->

<p>
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" alt="PyTorch"/>
  <img src="https://img.shields.io/badge/ONNX-005CED?style=flat-square&logo=onnx&logoColor=white" alt="ONNX"/>
  <img src="https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black" alt="HuggingFace"/>
</p>

[![Repo](https://img.shields.io/badge/Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/lpcvc-2026-CNU/gogildong)

---

## 4. MiniC Interpreter & Type Checker in OCaml

<sub><!-- TODO: 기간 · 개인/팀 과제 여부 --> 개인 프로젝트</sub>

<p align="center">
  <img src="assets/projects/minic-run.png" alt="MiniC 인터프리터 실행 화면" width="620"/>
</p>

![Language](https://img.shields.io/badge/OCaml-EC6813?style=flat-square&logo=ocaml&logoColor=white)
![Pipeline](https://img.shields.io/badge/Lexer→Parser→TypeChecker→Interpreter-6e7681?style=flat-square)

- C언어의 핵심 기능을 추상화한 MiniC 언어의 **어휘 분석부터 실행까지 컴파일러 전 과정**을 `ocamllex`·`menhir`로 직접 구현했습니다.
- 실행 전 타입 오류를 잡아내는 **정적 타입 체커**와, Environment-Store 모델 기반의 **메모리·포인터 연산**을 구현했습니다.
- 배열, 튜플, 포인터, 중첩 함수 등 복잡한 데이터 구조를 지원해 실제 C의 동작을 재현했습니다.
- <!-- TODO: 정량 결과 1줄 추가 (예: 테스트 케이스 __개 통과, 지원 문법 범위) -->

<p>
  <img src="https://img.shields.io/badge/OCaml-EC6813?style=flat-square&logo=ocaml&logoColor=white" alt="OCaml"/>
  <img src="https://img.shields.io/badge/Dune-black?style=flat-square" alt="Dune"/>
  <img src="https://img.shields.io/badge/Menhir-6e7681?style=flat-square" alt="Menhir"/>
</p>

[![Repo](https://img.shields.io/badge/Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/rhyskim/MiniC-Interpreter-Type-Checker-in-OCaml)

---

## 5. KB 머니룰 기반 안심보이스 — 시니어 금융 Agentic AI

<sub>2026 KB AI Challenge · 팀 프로젝트 · 진행 중</sub>

<!-- TODO: 대회 규정상 공개 가능한 스크린샷이 있다면 추가. 없으면 이 블록 삭제
<p align="center">
  <img src="assets/projects/kb-flow.png" alt="안심보이스 서비스 흐름도" width="620"/>
</p>
-->

![Status](https://img.shields.io/badge/Status-In%20Progress-d4a72c?style=flat-square)
![Domain](https://img.shields.io/badge/Domain-Senior%20FinTech-1f6feb?style=flat-square)

- 시니어 사용자가 음성·텍스트로 금융 업무를 요청할 수 있는 **Agentic AI**를 팀 단위로 개발하고 있습니다.
- <!-- TODO: 실제 담당 역할과 구현 내용으로 구체화 (예: LLM은 의도 파악만, 실행 승인은 결정론적 규칙이 담당하도록 권한 분리 등) -->
- <!-- TODO: 정량 결과 또는 현재 진행 상태 1줄 -->

> 대회 진행 중인 프로젝트로, 제출 이후 공개 가능한 구현과 결과를 업데이트할 예정입니다.

---

<details>
<summary><strong> More Projects — 추가 프로젝트 3개 펼쳐보기</strong></summary>

<br/>

| 프로젝트 | 설명 | 핵심 기술 |
| --- | --- | --- |
| [🚗 자율 주행 로봇 청소기](https://github.com/rhyskim/embedded-autonomous-vehicle) | STM32F429 + FreeRTOS 기반 미로 탈출 로봇. 초음파·적외선 센서 퓨전과 PD 제어로 벽면 추종과 동적 장애물 회피 구현 | C, FreeRTOS, Embedded |
| ☕ 스타벅스 고객 클러스터링 | 고객 데이터 클러스터링을 통한 맞춤형 서비스 제안 <!-- TODO: 저장소 공개 후 링크 연결 --> | Python, scikit-learn |
| 🌾 드론 농작물 병해 분류 AI | 드론 촬영 이미지 기반 작물 병해 분류 모델 <!-- TODO: 저장소 공개 후 링크 연결 --> | PyTorch, CV |

</details>

---

## Tech Stack

| Area | Tools |
| --- | --- |
| **Backend** | Python · FastAPI · Java |
| **Web** | TypeScript · React · Next.js |
| **Database** | Oracle · MySQL · SQLite · SQLAlchemy |
| **AI/ML** | PyTorch · ONNX (Runtime / Export) · scikit-learn · HuggingFace |
| **Systems** | C · OCaml · Assembly |
| **Tools** | Git · Docker |

### Currently Learning

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![ONNX](https://img.shields.io/badge/ONNX-005CED?style=flat-square&logo=onnx&logoColor=white)

---

## Contact

[![Blog](https://img.shields.io/badge/Blog-rhyskim.github.io-000000?style=flat-square&logo=github&logoColor=white)](https://rhyskim.github.io/)
[![Email](https://img.shields.io/badge/Email-rhyskim@naver.com-03C75A?style=flat-square&logo=naver&logoColor=white)](mailto:rhyskim@naver.com)

---

*이 README는 지속적으로 업데이트됩니다.*
</content>
