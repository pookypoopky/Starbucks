[![Netlify Status](https://api.netlify.com/api/v1/badges/9f2f756f-e1fc-48d9-9c07-b7d7433d8aaa/deploy-status)](https://app.netlify.com/sites/flamboyant-lumiere-482a1e/deploys)

# ☕ STARBUCKS

스타벅스 랜딩 페이지(홈페이지)입니다. <br>

[DEMO+signin](https://vibrant-goodall-53c4bf.netlify.app)

![Starbucks](https://raw.githubusercontent.com/ParkYoungWoong/starbucks-vanilla-app/master/_assets/main_screenshot.jpg)

## Youtube API

[IFrame Player API](https://developers.google.com/youtube/iframe_api_reference?hl=ko)를 통해 YouTube 동영상을 제어할 수 있습니다.

유튜브 영상이 출력될 위치에 요소를 지정(생성)합니다.

```html
<!-- in HEAD -->
<script defer src="./js/youtube.js"></script>

<!-- in BODY -->
<div id="player"></div>
```

`onYouTubePlayerAPIReady` 함수 이름은 Youtube IFrame Player API에서 사용하는 이름이기 때문에 다르게 지정하면 동작하지 않습니다!<br>
그리고 함수는 전역(Global) 등록해야 합니다!

[플레이어 매개변수(playerVars)](https://developers.google.com/youtube/player_parameters.html?playerVersion=HTML5&hl=ko#Parameters)에서 더 많은 옵션을 확인할 수 있습니다.

```js
// Youtube IFrame API를 비동기로 로드합니다.
var tag = document.createElement('script');
tag.src = "https://www.youtube.com/iframe_api";
var firstScriptTag = document.getElementsByTagName('script')[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

function onYouTubePlayerAPIReady() {
  // <div id="player"></div>
  new YT.Player('player', {
    videoId: 'An6LvWQuj_8', // 재생할 유튜브 영상 ID
    playerVars: {
      autoplay: true, // 자동 재생 유무
      loop: true, // 반복 재생 유무
      playlist: 'An6LvWQuj_8' // 반복 재생할 유튜브 영상 ID 목록
    },
    events: {
      // 영상이 준비되었을 때,
      onReady: function (event) {
        event.target.mute(); // 음소거!
      }
    }
  });
}
```

## JS Strict Mode

JavaScript를 '엄격 모드'로 사용합니다.<br>
파일 혹은 함수의 최상단에 작성해야 합니다.

```javascript
'use strict';
```

> 'Strict Mode'는 ECMAScript 5 버전에 있는 새로운 기능으로써, 프로그램 또는 함수를 엄격한 운용 콘텍스트 안에서 실행시킬 수 있게끔 합니다. 이 엄격한 콘텍스트는 몇가지 액션들을 실행할 수 없도록 하며, 좀 더 많은 예외를 발생시킵니다.

### 엄격 모드의 장점

- 일반적인 코딩 실수에서 예외 처리
- 안전하지 않은 액션에 대한 예외 처리 (ex: 전역 객체로 접근)
- 혼란스럽거나 제대로 고려되지 않는 기능들을 비활성화

## 랜덤한 숫자를 생성하는 함수

```js
// 범위 랜덤 함수(소수점 2자리까지)
function random(min, max) {
  // `.toFixed()`를 통해 반환된 문자 데이터를,
  // `parseFloat()`을 통해 소수점을 가지는 숫자 데이터로 변환
  return parseFloat((Math.random() * (max - min) + min).toFixed(2))
}
```

## Main menu in Header

```html
<ul class="main-menu">
  <li class="item">
    <div class="item__name">COFFEE</div>
    <div class="item__contents">
      <div class="contents__menu">
        <ul class="inner">
          <li>
            <h4>커피</h4>
            <ul>
              <li>스타벅스 원두</li>
              <li>스타벅스 비아</li>
              <li>스타벅스 오리가미</li>
            </ul>
          </li>
          <li>
            <h4>에스프레소 음료</h4>
            <ul>
              <li>도피오</li>
              <li>에스프레소 마키아또</li>
              <li>아메리카노</li>
              <li>마키아또</li>
              <li>카푸치노</li>
              <li>라떼</li>
              <li>모카</li>
              <li>리스트레또 비안코</li>
            </ul>
          </li>
          <li>
            <h4>커피 이야기</h4>
            <ul>
              <li>스타벅스 로스트 스팩트럼</li>
              <li>최상의 아라비카 원두</li>
              <li>한 잔의 커피가 완성되기까지</li>
              <li>클로버® 커피 추출 시스템</li>
            </ul>
          </li>
          <li>
            <h4>최상의 커피를 즐기는 법</h4>
            <ul>
              <li>커피 프레스</li>
              <li>푸어 오버</li>
              <li>아이스 푸어 오버</li>
              <li>커피 메이커</li>
              <li>리저브를 매장에서 다양하게 즐기는 법</li>
            </ul>
          </li>
        </ul>
      </div>
      <div class="contents__texture">
        <div class="inner">
          <h4>나와 어울리는 커피 찾기</h4>
          <p>스타벅스가 여러분에게 어울리는 커피를 찾아드립니다.</p>
          <h4>최상의 커피를 즐기는 법</h4>
          <p>여러가지 방법을 통해 다양한 풍미의 커피를 즐겨보세요.</p>
        </div>
      </div>
    </div>
  </li>
  <li class="item">
    <div class="item__name">MENU</div>
    <div class="item__contents">
      <div class="contents__menu">
        <ul class="inner">
          <li>
            <h4>음료</h4>
            <ul>
              <li>콜드 브루</li>
              <li>브루드 커피</li>
              <li>에스프레소</li>
              <li>프라푸치노</li>
              <li>블렌디드 음료</li>
              <li>스타벅스 피지오</li>
              <li>티(티바나)</li>
              <li>기타 제조 음료</li>
              <li>스타벅스 주스(병음료)</li>
            </ul>
          </li>
          <li>
            <h4>푸드</h4>
            <ul>
              <li>베이커리</li>
              <li>케익</li>
              <li>샌드위치 & 샐러드</li>
              <li>따뜻한 푸드</li>
              <li>과일 & 요거트</li>
              <li>스낵 & 미니 디저트</li>
              <li>아이스크림</li>
            </ul>
          </li>
          <li>
            <h4>상품</h4>
            <ul>
              <li>머그</li>
              <li>글라스</li>
              <li>플라스틱 텀블러</li>
              <li>스테인리스 텀블러</li>
              <li>보온병</li>
              <li>액세서리</li>
              <li>커피 용품</li>
              <li>패키지 티(티바나)</li>
            </ul>
          </li>
          <li>
            <h4>카드</h4>
            <ul>
              <li>실물카드</li>
              <li>e-Gift 카드</li>
            </ul>
          </li>
          <li>
            <h4>메뉴 이야기</h4>
            <ul>
              <li>콜드 브루</li>
              <li>스타벅스 티바나</li>
            </ul>
          </li>
        </ul>
      </div>
      <div class="contents__texture">
        <div class="inner">
          <h4 class="new">스타벅스 티바나</h4>
          <p>다양한 찻잎과 향신료 등 개성있는 재료로 새로운 맛과 향의 티를 선보입니다.</p>
        </div>
      </div>
    </div>
  </li>
  <li class="item">
    <div class="item__name">STORE</div>
    <div class="item__contents">
      <div class="contents__menu">
        <ul class="inner">
          <li>
            <h4>매장 찾기</h4>
            <ul>
              <li>퀵 검색</li>
              <li>지역 검색</li>
              <li>My 매장</li>
            </ul>
          </li>
          <li>
            <h4>매장 이야기</h4>
            <ul>
              <li>청담스타</li>
              <li>티바나 인스파이어드 매장</li>
              <li>파미에파크</li>
            </ul>
          </li>
        </ul>
      </div>
      <div class="contents__texture">
        <div class="inner">
          <h4>매장 찾기</h4>
          <p>보다 빠르게 매장을 찾아보세요.</p>
          <h4 class="new">청담스타</h4>
          <p>스타벅스 1,000호점인 청담스타점을 만나보세요.</p>
        </div>
      </div>
    </div>
  </li>
  <li class="item">
    <div class="item__name">RESPONSIBILITY</div>
    <div class="item__contents">
      <div class="contents__menu">
        <ul class="inner">
          <li>
            <h4>지역 사회 참여 활동</h4>
            <ul>
              <li>회망배달 캠페인</li>
              <li>재능기부 카페 소식</li>
              <li>커뮤니티 스토어</li>
              <li>청년인재 양성</li>
              <li>우리 농산물 사랑 캠페인</li>
              <li>우리 문화 지키기</li>
            </ul>
          </li>
          <li>
            <h4>환경보호 활동</h4>
            <ul>
              <li>환경 발자국 줄이기</li>
              <li>일회용 컵 없는 매장</li>
              <li>커피 원두 재활용</li>
            </ul>
          </li>
          <li>
            <h4>윤리 구매</h4>
            <ul>
              <li>윤리적 원두 구매</li>
              <li>공정무역 인증</li>
              <li>커피 농가 지원 활동</li>
            </ul>
          </li>
          <li>
            <h4>글로벌 사회 공헌</h4>
            <ul>
              <li>윤리경영 보고서</li>
              <li>스타벅스 재단</li>
              <li>지구촌 봉사의 달</li>
            </ul>
          </li>
        </ul>
      </div>
      <div class="contents__texture">
        <div class="inner">
          <h4>커피원두 재활용</h4>
          <p>스타벅스 커피 원두를 재활용 해보세요.</p>
        </div>
      </div>
    </div>
  </li>
  <li class="item">
    <div class="item__name">MY STARBUCKS REWARDS</div>
    <div class="item__contents">
      <div class="contents__menu">
        <ul class="inner">
          <li>
            <h4>마이 스타벅스 리워드</h4>
            <ul>
              <li>마이 스타벅스 리워드 소개</li>
              <li>등급 및 혜택</li>
              <li>스타벅스 별</li>
              <li>자주하는 질문</li>
            </ul>
          </li>
          <li>
            <h4>스타벅스 카드</h4>
            <ul>
              <li>스타벅스 카드 소개</li>
              <li>스타벅스 카드 갤러리</li>
              <li>등록 및 조회</li>
              <li>충전 및 이용안내</li>
              <li>분실신고/환불신청</li>
              <li>자주하는 질문</li>
            </ul>
          </li>
          <li>
            <h4>스타벅스 카드 e-Gift</h4>
            <ul>
              <li>스타벅스 카드 e-Gift 소개</li>
              <li>이용안내</li>
              <li>선물하기</li>
              <li>자주하는 질문</li>
            </ul>
          </li>
        </ul>
      </div>
      <div class="contents__texture">
        <div class="inner">
          <h4>스타벅스 카드 등록하기</h4>
          <p>카드 등록 후 리워드 서비스를 누리고 사용내역도 조회해보세요.</p>
        </div>
      </div>
    </div>
  </li>
  <li class="item">
    <div class="item__name">WHAT'S NEW</div>
    <div class="item__contents">
      <div class="contents__menu">
        <ul class="inner">
          <li>
            <h4>프로모션 & 이벤트</h4>
            <ul>
              <li>전체</li>
              <li>스타벅스 카드</li>
              <li>마이 스타벅스 리워드</li>
              <li>온라인</li>
              <li>2017 스타벅스 플래너</li>
            </ul>
          </li>
          <li>
            <h4>새소식</h4>
            <ul>
              <li>전체</li>
              <li>상품 출시</li>
              <li>스타벅스의 문화</li>
              <li>스타벅스 사회공헌</li>
              <li>스타벅스 카드출시</li>
            </ul>
          </li>
          <li>
            <h4>매장별 이벤트</h4>
            <ul>
              <li>일반 매장</li>
              <li>신규 매장</li>
            </ul>
          </li>
        </ul>
      </div>
      <div class="contents__texture">
        <div class="inner">
          <h4>매장별 이벤트</h4>
          <p>스타벅스의 매장 이벤트 정보를 확인 하실 수 있습니다.</p>
          <h4>소셜 스타벅스</h4>
          <p>다양한 스타벅스 SNS 채널을 통해 스타벅스를 만나보세요!</p>
        </div>
      </div>
    </div>
  </li>
</ul>
```