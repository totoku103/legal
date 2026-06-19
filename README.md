# therene Legal (개인정보 처리방침 정적 사이트)

GitHub Pages + 커스텀 도메인으로 앱별 개인정보 처리방침을 호스팅한다.

- 공개 URL: `https://legal.therene.co.kr/`
- 앱별: `https://legal.therene.co.kr/<app-slug>/`

## 구조
```
.
├── CNAME                       # legal.therene.co.kr (커스텀 도메인)
├── index.html                  # 앱 목록 랜딩
├── rtsp-camera/
│   ├── index.html              # RTSP Camera 처리방침 (신규 앱 템플릿 겸용)
│   └── support/index.html      # RTSP Camera 지원 페이지
├── mini-browser-mirror/
│   ├── index.html              # Mini Browser Mirror 처리방침
│   └── support/index.html      # Mini Browser Mirror 지원 페이지
├── flagdeck/
│   ├── index.html              # FlagDeck 처리방침 (한/영)
│   └── support/index.html      # FlagDeck 지원 페이지 (FAQ·문의)
└── README.md
```

## 새 앱 추가 절차
1. `rtsp-camera/` 폴더를 `<새-app-slug>/`로 복제.
2. 그 안 `index.html`의 앱명·수집항목·SDK·권한을 수정.
3. 루트 `index.html`의 목록에 한 줄 추가.
4. 커밋·푸시 → 1~2분 내 반영.

> slug는 한번 정하면 ASC에 박히므로 변경 금지. 번들 ID 끝 세그먼트와 맞춘다
> (`kr.co.therene.rtspcamera` ↔ `rtsp-camera`).

## 최초 1회 셋업
1. 이 디렉터리를 GitHub 저장소로 푸시(예: `totoku103/legal`).
2. 저장소 Settings → Pages → Source: `main` 브랜치 `/ (root)`.
3. Settings → Pages → Custom domain: `legal.therene.co.kr` 입력(= CNAME 파일과 일치).
4. "Enforce HTTPS" 체크(인증서 발급까지 수 분~수십 분).

## DNS 설정 (도메인 등록기관에서)
`therene.co.kr` DNS에 아래 레코드 추가:

```
CNAME   legal   totoku103.github.io.
```

> apex(루트)가 아니라 `legal` 서브도메인이므로 CNAME으로 충분(A 레코드 불필요).
> 밑단 저장소를 therene 계정으로 이관하면 대상만 `therene.github.io.`로 바꾸면 되고,
> 공개 URL(`legal.therene.co.kr`)은 그대로 유지된다.

## 발행 전 채울 placeholder
- 각 `index.html`의 `<연락 이메일>` → 실제 문의 이메일
- 회사 법인명이 필요하면 footer의 `therene`를 정식 상호로
