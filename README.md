# CSE3210-Team1
STL Set Implementation using AVL Tree

프로젝트 소개 

본 프로젝트는 오픈소스응용프로그래밍 과목의 팀 프로젝트입니다. 

C++의 인터페이스와 구현을 분리하는 추상화 설계를 통해 AVL 트리 기반의 set 자료구조를 직접 구현하였습니다.

---
📅 개발 정보

개발 기간: 2025. 09 ~ 2025. 12. 18 

담당 교수: 김영호 교수님 

분반: 003분반 (TEAM 1)

---
👥 개발자 및 역할 분담

박서진 (팀장)
+ 프로젝트 전체 개발 일정 조율 및 관리 
+ set.h 인터페이스 정의 및 추상화 적용 
+ 기본 기능(Find, Size) 및 고급 기능(Erase) 구현 

김지영
+ UML 클래스 다이어그램 작성 
+ 기본 기능(Empty, UpperBound) 및 고급 기능(Rank) 구현 
+ Google Test를 활용한 단위 테스트 및 채점 서버 검증 

오리항 푸레브자브
+ 프로젝트 초기 구조 설계 및 Node 클래스 구현 
+ 오픈소스 라이선스(MIT) 선정 및 적용 

조승흠
+ 기본 기능(Insert, Prev) 구현 
+ AVL 트리 균형 유지를 위한 보조 함수(Rotation, Rebalance 등) 구현 
+ 코드 리뷰 방식 및 테스트 설계 원칙 수립 참여

---
🛠 기술 스택 및 개발 환경

1. Language: C++ (CSE3210 스타일 가이드 준수) 
2. Build System: CMake 
3. Test Framework: Google Test (GTest) 
4. Formatter: Clang-format 
5. License: MIT License

---
프로젝트 아키텍처

설계 원칙 단일 책임 원칙(Single Responsibility Principle)을 준수하여 각 클래스가 오직 하나의 명확한 책임만을 갖도록 분리하였습니다. 

1. Set (Interface)
+ 자료구조의 추상적인 동작을 정의하는 사용자 인터페이스입니다. 
+ 실제 구현 방식은 숨기고 공통된 기능 명세만을 제공합니다. 

2. AVLSet (Mediator)
+ Set 인터페이스를 구현하며 사용자 요청을 AVLTree 객체에 위임합니다. 
+ 사용자 인터페이스와 내부 자료구조 사이의 중간 계층 역할을 수행합니다. 

3. AVLTree (Core Logic)
+ 노드의 삽입, 삭제, 탐색 연산 및 트리의 균형 유지 로직을 전담합니다. 
+ 트리의 구조적 안정성과 시간 복잡도를 보장합니다. 

4. Node (Data Container)
+ 데이터(Key)와 구조적 정보(자식 노드 포인터, 높이, 서브트리 크기 등)를 저장합니다. 
+ 순수하게 데이터 컨테이너 역할만을 수행하며 연산 로직과 분리됩니다.

---
🚀 주요 기능

기본 기능 (Basic Operations)

+ Insert: 이진 탐색 트리 규칙에 따라 노드를 삽입하고 AVL 균형 조건에 맞게 트리를 재조정합니다. 
+ Find: 특정 키값 존재 여부를 확인하고, 해당 노드의 Depth × Height 값을 반환합니다. 
+ Size & Empty: 현재 트리의 원소 개수를 확인하며, *O(1)*의 상수 시간 복잡도를 보장합니다. 
+ Prev & Next: 특정 노드의 전임자(Predecessor)와 후임자(Successor)를 탐색합니다. 
+ UpperBound: 주어진 키보다 큰 원소 중 가장 작은 원소를 탐색합니다 (O(log N)). 


고급 기능 (Advanced Operations)

+ Rank: 특정 키의 순위를 구하는 연산으로, 서브트리 크기 정보를 활용해 O(log N) 이내에 수행됩니다. 
+ Erase: 노드 삭제 후 트리의 균형 유지 및 서브트리 크기 정보를 갱신합니다. 

---

🧪 테스트 설계 및 결과

+ 단위 테스트: Google Test의 TEST 매크로를 사용하여 각 함수별로 개별 검증을 수행하였습니다. 
+ 검증 범위: 빈 트리, 단일 노드 삽입, 치우친 삽입 등 다양한 엣지 케이스를 포함하였습니다. 
+ 통합 테스트: 실제 채점 서버 환경에서 모든 테스트 항목에 대해 CORRECT 판정을 획득하였습니다.
