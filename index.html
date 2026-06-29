<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>QR 코드 생성기</title>

  <!-- QR 코드 생성 라이브러리 (CDN) - ISO/IEC 18004 QR Code Model 2 구현 -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>

  <style>
    /* ─────────────────────────────────────────
       CSS 변수 (토큰 시스템)
    ───────────────────────────────────────── */
    :root {
      --bg:          #0d0d0f;       /* 최외곽 배경 */
      --surface:     #17171b;       /* 카드 배경 */
      --surface2:    #1f1f25;       /* 입력창 배경 */
      --border:      #2c2c36;       /* 테두리 */
      --accent:      #6c63ff;       /* 주 강조색 (보라) */
      --accent-glow: rgba(108,99,255,.25);
      --accent-dim:  #4b44cc;       /* hover 시 어두운 강조 */
      --danger:      #ff5c5c;       /* 오류/삭제 색 */
      --success:     #3dd68c;       /* 성공 색 */
      --text:        #e8e8f0;       /* 기본 텍스트 */
      --text-muted:  #6b6b80;       /* 보조 텍스트 */
      --mono:        'JetBrains Mono', 'Fira Code', monospace;
      --sans:        'Inter', 'Segoe UI', system-ui, sans-serif;
      --radius:      12px;
      --radius-sm:   8px;
      --transition:  .18s ease;
    }

    /* ─────────────────────────────────────────
       리셋 & 기본
    ───────────────────────────────────────── */
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: var(--sans);
      background: var(--bg);
      color: var(--text);
      min-height: 100dvh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 24px 16px;
      /* 서브틀한 그리드 패턴 배경 */
      background-image:
        radial-gradient(ellipse 80% 50% at 50% -20%, rgba(108,99,255,.18) 0%, transparent 70%),
        linear-gradient(var(--border) 1px, transparent 1px),
        linear-gradient(90deg, var(--border) 1px, transparent 1px);
      background-size: auto, 40px 40px, 40px 40px;
    }

    /* ─────────────────────────────────────────
       헤더
    ───────────────────────────────────────── */
    .header {
      text-align: center;
      margin-bottom: 32px;
    }

    .header__eyebrow {
      font-family: var(--mono);
      font-size: 11px;
      letter-spacing: .14em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 10px;
    }

    .header__title {
      font-size: clamp(24px, 5vw, 36px);
      font-weight: 700;
      letter-spacing: -.02em;
      line-height: 1.1;
      background: linear-gradient(135deg, #fff 30%, var(--accent));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .header__sub {
      margin-top: 8px;
      font-size: 13px;
      color: var(--text-muted);
    }

    /* ─────────────────────────────────────────
       메인 카드
    ───────────────────────────────────────── */
    .card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      width: 100%;
      max-width: 480px;
      padding: 28px 24px;
      box-shadow: 0 0 60px rgba(0,0,0,.5), 0 0 0 1px rgba(108,99,255,.08);
    }

    /* ─────────────────────────────────────────
       섹션 레이블
    ───────────────────────────────────────── */
    .label {
      display: block;
      font-size: 11px;
      font-weight: 600;
      letter-spacing: .08em;
      text-transform: uppercase;
      color: var(--text-muted);
      margin-bottom: 8px;
    }

    /* ─────────────────────────────────────────
       URL 입력 영역
    ───────────────────────────────────────── */
    .input-wrap {
      position: relative;
      margin-bottom: 14px;
    }

    .input-icon {
      position: absolute;
      left: 14px;
      top: 50%;
      transform: translateY(-50%);
      color: var(--text-muted);
      pointer-events: none;
      display: flex;
    }

    #urlInput {
      width: 100%;
      background: var(--surface2);
      border: 1.5px solid var(--border);
      border-radius: var(--radius-sm);
      color: var(--text);
      font-family: var(--mono);
      font-size: 13px;
      padding: 12px 14px 12px 40px;
      outline: none;
      transition: border-color var(--transition), box-shadow var(--transition);
    }

    #urlInput::placeholder {
      color: var(--text-muted);
    }

    #urlInput:focus {
      border-color: var(--accent);
      box-shadow: 0 0 0 3px var(--accent-glow);
    }

    /* 유효성 상태별 테두리 */
    #urlInput.is-valid   { border-color: var(--success); }
    #urlInput.is-invalid { border-color: var(--danger); }

    /* ─────────────────────────────────────────
       에러 메시지
    ───────────────────────────────────────── */
    .error-msg {
      font-size: 12px;
      color: var(--danger);
      min-height: 18px;
      margin-bottom: 10px;
      padding-left: 2px;
      display: none; /* JS에서 제어 */
    }

    .error-msg.visible {
      display: block;
    }

    /* ─────────────────────────────────────────
       옵션 행 (ECC 선택)
    ───────────────────────────────────────── */
    .options-row {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-bottom: 16px;
      flex-wrap: wrap;
    }

    .options-row .label {
      margin-bottom: 0;
      white-space: nowrap;
    }

    .ecc-group {
      display: flex;
      gap: 6px;
    }

    /* 라디오 버튼을 커스텀 칩으로 */
    .ecc-group input[type="radio"] {
      display: none;
    }

    .ecc-group label {
      display: inline-flex;
      align-items: center;
      gap: 4px;
      padding: 5px 12px;
      border-radius: 20px;
      border: 1.5px solid var(--border);
      font-size: 12px;
      font-weight: 600;
      font-family: var(--mono);
      color: var(--text-muted);
      cursor: pointer;
      transition: all var(--transition);
      user-select: none;
    }

    .ecc-group input[type="radio"]:checked + label {
      border-color: var(--accent);
      background: var(--accent-glow);
      color: var(--text);
    }

    .ecc-group label:hover {
      border-color: var(--accent);
      color: var(--text);
    }

    /* ─────────────────────────────────────────
       버튼 그룹
    ───────────────────────────────────────── */
    .btn-group {
      display: flex;
      gap: 8px;
      margin-bottom: 24px;
    }

    .btn {
      flex: 1;
      padding: 11px 16px;
      border: none;
      border-radius: var(--radius-sm);
      font-family: var(--sans);
      font-size: 13px;
      font-weight: 600;
      cursor: pointer;
      transition: all var(--transition);
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
    }

    /* 주 버튼 - 생성 */
    .btn--primary {
      background: var(--accent);
      color: #fff;
    }

    .btn--primary:hover {
      background: var(--accent-dim);
      box-shadow: 0 0 20px var(--accent-glow);
      transform: translateY(-1px);
    }

    .btn--primary:active { transform: translateY(0); }

    /* 보조 버튼 - 다운로드 */
    .btn--secondary {
      background: var(--surface2);
      color: var(--text);
      border: 1.5px solid var(--border);
    }

    .btn--secondary:hover {
      border-color: var(--accent);
      color: var(--accent);
    }

    /* 위험 버튼 - 삭제 */
    .btn--danger {
      background: transparent;
      color: var(--danger);
      border: 1.5px solid rgba(255,92,92,.3);
    }

    .btn--danger:hover {
      background: rgba(255,92,92,.1);
      border-color: var(--danger);
    }

    /* 비활성 버튼 공통 */
    .btn:disabled {
      opacity: .35;
      cursor: not-allowed;
      pointer-events: none;
    }

    /* ─────────────────────────────────────────
       QR 결과 영역
    ───────────────────────────────────────── */
    #resultSection {
      display: none; /* QR 생성 전 숨김 */
      flex-direction: column;
      align-items: center;
      gap: 16px;
      animation: fadeUp .25s ease;
    }

    #resultSection.visible {
      display: flex;
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(12px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    /* QR 코드 캔버스 컨테이너 */
    #qrContainer {
      width: 300px;
      height: 300px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #fff; /* QR은 흰 배경 */
      border-radius: var(--radius-sm);
      overflow: hidden;
      box-shadow: 0 0 0 4px var(--border), 0 8px 40px rgba(0,0,0,.4);
    }

    /* qrcode.js가 생성하는 canvas/img 직접 타겟 */
    #qrContainer canvas,
    #qrContainer img {
      display: block;
      width: 300px !important;
      height: 300px !important;
    }

    /* ─────────────────────────────────────────
       생성된 URL 표시
    ───────────────────────────────────────── */
    .result-url {
      width: 100%;
      background: var(--surface2);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 10px 12px;
    }

    .result-url__label {
      font-size: 10px;
      letter-spacing: .08em;
      text-transform: uppercase;
      color: var(--text-muted);
      margin-bottom: 4px;
    }

    .result-url__text {
      font-family: var(--mono);
      font-size: 12px;
      color: var(--success);
      word-break: break-all;
      line-height: 1.5;
    }

    /* ─────────────────────────────────────────
       하단 액션 버튼 (다운로드 / 삭제)
    ───────────────────────────────────────── */
    .result-actions {
      display: flex;
      gap: 8px;
      width: 100%;
    }

    /* ─────────────────────────────────────────
       구분선
    ───────────────────────────────────────── */
    .divider {
      width: 100%;
      border: none;
      border-top: 1px solid var(--border);
      margin: 4px 0 20px;
    }

    /* ─────────────────────────────────────────
       푸터
    ───────────────────────────────────────── */
    .footer {
      margin-top: 24px;
      font-size: 11px;
      color: var(--text-muted);
      text-align: center;
    }

    .footer span {
      color: var(--accent);
    }

    /* ─────────────────────────────────────────
       반응형 (모바일 ≤ 420px)
    ───────────────────────────────────────── */
    @media (max-width: 420px) {
      .card { padding: 20px 16px; }
      .btn-group { flex-direction: column; }
      .result-actions { flex-direction: column; }
    }

    /* ─────────────────────────────────────────
       접근성: 모션 감소 설정 존중
    ───────────────────────────────────────── */
    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { transition: none !important; animation: none !important; }
    }
  </style>
</head>
<body>

  <!-- ── 헤더 ─────────────────────────────── -->
  <header class="header">
    <p class="header__eyebrow">ISO/IEC 18004 · QR Code Model 2</p>
    <h1 class="header__title">QR 코드 생성기</h1>
    <p class="header__sub">URL을 입력하면 브라우저에서 바로 QR을 생성합니다</p>
  </header>

  <!-- ── 메인 카드 ──────────────────────────── -->
  <main class="card" role="main">

    <!-- URL 입력 -->
    <label class="label" for="urlInput">URL 입력</label>
    <div class="input-wrap">
      <!-- 링크 아이콘 -->
      <span class="input-icon" aria-hidden="true">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none"
             stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M10 13a5 5 0 0 0 7.54.54l3-3A5 5 0 0 0 9.08 5.96"/>
          <path d="M14 11a5 5 0 0 0-7.54-.54l-3 3A5 5 0 0 0 14.92 18"/>
        </svg>
      </span>
      <input
        type="url"
        id="urlInput"
        placeholder="https://example.com"
        autocomplete="off"
        spellcheck="false"
        aria-describedby="urlError"
      />
    </div>

    <!-- 유효성 오류 메시지 -->
    <p class="error-msg" id="urlError" role="alert" aria-live="polite"></p>

    <!-- ECC 옵션 선택 -->
    <div class="options-row">
      <span class="label">오류 정정 수준</span>
      <div class="ecc-group" role="radiogroup" aria-label="오류 정정 수준 선택">
        <!-- M: 약 15% 복원 가능 (기본) -->
        <input type="radio" name="ecc" id="eccM" value="M" checked />
        <label for="eccM">M</label>
        <!-- Q: 약 25% 복원 가능 -->
        <input type="radio" name="ecc" id="eccQ" value="Q" />
        <label for="eccQ">Q</label>
      </div>
    </div>

    <!-- 생성 버튼 -->
    <div class="btn-group">
      <button class="btn btn--primary" id="generateBtn" aria-label="QR 코드 생성">
        <!-- 생성 아이콘 -->
        <svg width="15" height="15" viewBox="0 0 24 24" fill="none"
             stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
          <rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/>
          <rect x="3" y="14" width="7" height="7"/>
          <path d="M14 14h.01M18 14h.01M14 18h.01M18 18h.01"/>
        </svg>
        QR 생성
      </button>
    </div>

    <!-- ── 결과 구역 (QR 생성 후 노출) ──────── -->
    <section id="resultSection" aria-label="QR 코드 결과">
      <hr class="divider" />

      <!-- QR 코드 렌더링 영역 (qrcode.js가 내부에 canvas/img를 삽입) -->
      <div id="qrContainer" role="img" aria-label="생성된 QR 코드"></div>

      <!-- 생성된 URL 표시 -->
      <div class="result-url" aria-label="인코딩된 URL">
        <div class="result-url__label">인코딩된 URL</div>
        <div class="result-url__text" id="resultUrlText"></div>
      </div>

      <!-- 다운로드 / 삭제 버튼 -->
      <div class="result-actions">
        <button class="btn btn--secondary" id="downloadBtn" aria-label="PNG로 다운로드">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none"
               stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
            <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
            <polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/>
          </svg>
          PNG 다운로드
        </button>

        <button class="btn btn--danger" id="clearBtn" aria-label="QR 코드 초기화">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none"
               stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
            <polyline points="3 6 5 6 21 6"/><path d="M19 6l-1 14H6L5 6"/>
            <path d="M10 11v6"/><path d="M14 11v6"/>
          </svg>
          삭제
        </button>
      </div>
    </section>

  </main>

  <!-- ── 푸터 ─────────────────────────────── -->
  <footer class="footer">
    서버 없이 브라우저에서만 동작 &middot; 라이브러리: <span>qrcodejs</span>
  </footer>


  <script>
    /* ============================================================
       QR 코드 생성기 - 메인 스크립트
       ============================================================

       [라이브러리 동작 흐름]
       1. 사용자가 URL 입력 후 버튼 클릭(또는 Enter)
       2. validateUrl()로 입력 검사
       3. QRCode() 생성자에 URL 문자열 전달
       4. 내부적으로 ISO/IEC 18004 QR Code Model 2 처리:
          a. 데이터를 비트열로 인코딩
          b. Reed–Solomon ECC 계산 및 추가
          c. Finder / Alignment / Timing Pattern 배치
          d. 최적 Mask Pattern 선택
          e. Canvas(또는 img)에 매트릭스 렌더링
       5. PNG 다운로드 시 canvas.toDataURL('image/png')으로 변환
    ============================================================ */

    /* ── DOM 참조 ────────────────────────────── */
    const urlInput      = document.getElementById('urlInput');
    const urlError      = document.getElementById('urlError');
    const generateBtn   = document.getElementById('generateBtn');
    const downloadBtn   = document.getElementById('downloadBtn');
    const clearBtn      = document.getElementById('clearBtn');
    const resultSection = document.getElementById('resultSection');
    const qrContainer   = document.getElementById('qrContainer');
    const resultUrlText = document.getElementById('resultUrlText');

    /* ── 상태 ────────────────────────────────── */
    let qrInstance = null; // 현재 QRCode 인스턴스

    /* ── QR 옵션 상수 ────────────────────────── */
    const QR_WIDTH  = 300;
    const QR_HEIGHT = 300;
    const QR_MARGIN = 4;         // 조용한 영역(Quiet Zone) 모듈 수
    const QR_COLOR_DARK  = '#000000';
    const QR_COLOR_LIGHT = '#FFFFFF';

    /* ── ECC 레벨 매핑 ───────────────────────── */
    // qrcodejs는 QRCode.CorrectLevel.M / .Q 등을 사용
    const ECC_MAP = {
      M: QRCode.CorrectLevel.M,
      Q: QRCode.CorrectLevel.Q,
    };

    /* ============================================================
       validateUrl - URL 유효성 검사
       @param {string} value - 사용자 입력 문자열
       @returns {{ valid: boolean, message: string }}
    ============================================================ */
    function validateUrl(value) {
      // 빈 값 검사
      if (!value.trim()) {
        return { valid: false, message: 'URL을 입력해 주세요.' };
      }

      // 프로토콜 없으면 https:// 자동 보완 후 파싱 시도
      let normalized = value;
      if (!/^[a-zA-Z][a-zA-Z\d+\-.]*:\/\//.test(value)) {
        normalized = 'https://' + value;
      }

      try {
        const parsed = new URL(normalized);
        // 호스트네임에 점이 있거나 localhost면 유효한 링크로 간주
        const host = parsed.hostname;
        if (!host || (!host.includes('.') && host !== 'localhost')) {
          return { valid: false, message: '유효한 도메인을 입력해 주세요. (예: example.com)' };
        }
        return { valid: true, message: '', normalized };
      } catch {
        return { valid: false, message: '올바른 링크 형식이 아닙니다. (예: example.com)' };
      }
    }

    /* ============================================================
       showError - 에러 메시지 표시
       @param {string} message - 표시할 메시지 (빈 문자열이면 숨김)
    ============================================================ */
    function showError(message) {
      urlError.textContent = message;
      if (message) {
        urlError.classList.add('visible');
        urlInput.classList.add('is-invalid');
        urlInput.classList.remove('is-valid');
      } else {
        urlError.classList.remove('visible');
        urlInput.classList.remove('is-invalid');
      }
    }

    /* ============================================================
       clearError - 에러 상태 초기화
    ============================================================ */
    function clearError() {
      showError('');
    }

    /* ============================================================
       getSelectedEcc - 선택된 ECC 레벨 반환
       @returns {number} QRCode.CorrectLevel 값
    ============================================================ */
    function getSelectedEcc() {
      const selected = document.querySelector('input[name="ecc"]:checked');
      return ECC_MAP[selected ? selected.value : 'M'];
    }

    /* ============================================================
       generateQr - QR 코드 생성 메인 함수
    ============================================================ */
    function generateQr() {
      const url = urlInput.value.trim();

      // 1. 유효성 검사 (프로토콜 없으면 normalized에 https:// 붙은 값 반환)
      const { valid, message, normalized } = validateUrl(url);
      if (!valid) {
        showError(message);
        return;
      }

      // 보완된 URL 사용 (예: example.com → https://example.com)
      const finalUrl = normalized;

      // 2. 에러 초기화 + 입력창 성공 스타일
      clearError();
      urlInput.classList.add('is-valid');

      // 3. 기존 QR 제거 (재생성 시 중복 방지)
      destroyQr();

      // 4. qrcode.js 인스턴스 생성
      //    - QRCode 생성자가 내부적으로 ECC, Mask, Reed-Solomon 처리 후
      //      qrContainer 내부에 canvas(또는 img) 엘리먼트를 삽입함
      qrInstance = new QRCode(qrContainer, {
        text:           finalUrl,
        width:          QR_WIDTH,
        height:         QR_HEIGHT,
        colorDark:      QR_COLOR_DARK,
        colorLight:     QR_COLOR_LIGHT,
        correctLevel:   getSelectedEcc(),
      });

      // 5. 결과 URL 텍스트 표시
      resultUrlText.textContent = finalUrl;

      // 6. 결과 섹션 표시 (애니메이션 포함)
      resultSection.classList.add('visible');

      // 7. 결과 영역으로 부드럽게 스크롤
      resultSection.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
    }

    /* ============================================================
       destroyQr - 현재 QR 인스턴스 및 DOM 초기화
    ============================================================ */
    function destroyQr() {
      if (qrInstance) {
        // qrcode.js 인스턴스 내부 clear 메서드
        qrInstance.clear();
        qrInstance = null;
      }
      // qrContainer 내부 DOM 완전 초기화
      qrContainer.innerHTML = '';
    }

    /* ============================================================
       downloadQr - QR 코드를 PNG 파일로 다운로드
       Canvas → toDataURL → <a> 클릭 트릭으로 저장
    ============================================================ */
    function downloadQr() {
      if (!qrInstance) return;

      // qrcode.js가 생성한 canvas 엘리먼트 탐색
      const canvas = qrContainer.querySelector('canvas');

      if (canvas) {
        // Canvas → PNG base64 데이터 URL 변환
        const dataUrl = canvas.toDataURL('image/png');

        // 임시 <a> 태그로 다운로드 트리거
        const link = document.createElement('a');
        link.href     = dataUrl;
        link.download = 'qr-code.png';
        link.click();
      } else {
        // 일부 환경에서 img 태그로 렌더링된 경우 안내
        const img = qrContainer.querySelector('img');
        if (img) {
          const link = document.createElement('a');
          link.href     = img.src;
          link.download = 'qr-code.png';
          link.click();
        }
      }
    }

    /* ============================================================
       clearQr - QR 및 입력 전체 초기화
    ============================================================ */
    function clearQr() {
      destroyQr();
      resultSection.classList.remove('visible');
      resultUrlText.textContent = '';
      urlInput.value = '';
      urlInput.classList.remove('is-valid', 'is-invalid');
      clearError();
      urlInput.focus();
    }

    /* ============================================================
       이벤트 바인딩
    ============================================================ */

    // 생성 버튼 클릭
    generateBtn.addEventListener('click', generateQr);

    // 다운로드 버튼 클릭
    downloadBtn.addEventListener('click', downloadQr);

    // 삭제 버튼 클릭
    clearBtn.addEventListener('click', clearQr);

    // Enter 키로 QR 생성
    urlInput.addEventListener('keydown', (e) => {
      if (e.key === 'Enter') generateQr();
    });

    // 입력 중 에러 메시지 즉시 제거 (UX 개선)
    urlInput.addEventListener('input', () => {
      if (urlError.classList.contains('visible')) {
        clearError();
        urlInput.classList.remove('is-invalid');
      }
    });
  </script>
</body>
</html>
