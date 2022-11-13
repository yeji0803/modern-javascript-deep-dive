# 6. 데이터 타입

데이터 타입: 값의 종류(형태).

`데이터 타입`은 **원시 타입(Primitive type)** 과 **객체 타입(Object type)** 으로 나눌 수 있다.

<br>

#### 원시 타입

-   숫자(number): 숫자의 모든 경우에 속한다. 정수와 실수 구분이 없다.
-   문자열(string): 문자열
-   불리언(boolean): 논리적 참과 거짓(true, false)
-   undefined: 변수가 선언될 때 암묵적으로 할당되는 값
-   null: 값이 없다는 것을 의도적으로 명시할 때 사용하는 값
-   심벌(symbol): ES6에서 추가됨

#### 객체 타입

-   객체
-   함수
-   배열 ... 등

<br>
<br>

##### 숫자 타입

자바스크립트의 숫자 타입은 **배정밀도 64비트 부동소수점 형식**을 따른다.
즉, 모든 수를 실수로 처리한다.

숫자 타입은 모든 수를 배정밀도 64비트 부동소수점 형식의 2진수로 저장되기 때문에, 어떤 형태의 수를 참조하여도 10진수로 해석된다.

```javascript
var binary = 0b01000001;
var octal = 0o101;
var hex = 0x41;

console.log(binary); // 65
console.log(octal); // 65
console.log(hex); // 65

console.log(binary === octal); // true
console.log(octal === hex); // true

console.log(1 === 1.0); // true
console.log(5 / 2); // 2.5
```

숫자 타입에는 아래와 같은 특별한 값도 표현할 수 있다.

-   Infinity: 양의 무한대
-   -Infinity: 음의 무한대
-   NaN: 산술 연산 불가(not a number)

```javascript
console.log(10 / Infinity); // 0
console.log(10 / -Infinity); // -0

console.log(Infinity / -Infinity); // NaN
console.log(1 - Infinity); // -Infinity

console.log(Infinity - Infinity); // NaN
console.log(Infinity / -35); // -Infinity

console.log(1 / 0); // Infinity
```

<br>
<br>

##### 문자열 타입

문자열은 0개 이상의 **16비트 유니코드 문자(UTF-16)의 집합**으로, 전 세계 대부분의 문자를 표현할 수 있다.

```javascript
// 문자열 타입의 표기법
var myText;

myText = "Hello"; // 작은 따옴표
myText = "Hi"; // 큰 따옴표
myText = `ES6 backtick`; // 백틱(ES6)

myText = '작은 따옴표로 표기한 경우, 내부의 "큰따옴표"는 문자열로 인식됨.';
myText = "큰 따옴표로 표기한 경우, 내부의 '큰따옴표'는 문자열로 인식됨.";

// 템플릿 리터럴
var variable = "hello";
var testTemplate = `<div>
    <h1>${variable}, 나는 템플릿 리터럴이야</h1>
</div>`; // ${}를 사용하여 표현식을 삽입할 수 있다.

// hi
```

자바스크립트의 문자열은 원시 타입이므로 **변경이 불가능한 값**이다.
개행이나 탭, 큰 따옴표나 작은 따옴표를 표현하기 위해서는 **이스케이프 시퀀스**를 사용하여 표현하여야 한다.

그러나, 템플릿 리터럴을 사용한다면 이스케이프 시퀀스를 사용하지 않고 표현할 수 있다.
또한 표현식을 삽입하여 가독성 좋게 문자열을 조합할 수 있다.

<br>
<br>

##### 불리언 타입

논리적 참, 거짓을 나타내는 `true`와 `false`로 구성된다.

<br>
<br>

##### undefined 타입

`undefined` 타입은 `undefined`이 유일하다.
변수를 선언하면 자바스크립트 엔진은 자동으로 `undefined` 값으로 초기화한다.

`undefined`는 의도치 않은 미할당 변수임을 식별하는 용도로 쓰이는 것을 권장한다.
때문에 개발자가 일부러 빈 값으로 두고 싶을 때는 `undefined`를 사용하는 것이 아니라 `null`을 사용하는 것이 바람직하다.

<br>
<br>

##### null 타입

`null` 타입은 `null`이 유일하다.
`null`은 변수에 값이 없다는 것을 의도적으로 명시하기 위한 용도로 사용한다.

`null`은 유효한 값이 아닐 경우 반환하는 용도로도 사용된다.
ex) `document.querySelector`는 조건에 부합하는 HTML 요소를 검색하지 못한 경우, 에러 대신 `null`를 반환한다.

<br>
<br>

##### 심벌 타입

심벌은 **변경 불가능한 원시 타입의 값**이다.  
다른 값과 중복되지 않은 유일한 값이기 때문에 이름 충돌 위험이 없는 객체의 유일한 프로퍼티 키를 만들기 위해 사용한다.
심벌은 Symbol 함수를 호출하여 생성한다.

<br>
<br>

### 데이터 타입이 왜 필요한가?

##### 1. 데이터 타입에 의해 메모리 공간의 확보와 참조

값 > 메모리에 저장 공간이 필요함 > 값을 효율적으로 저장하기 위해서는 대략적인 용량을 결정해야 한다.
즉, 타입에 맞는 효율적인 용량을 정하여 메모리 공간을 확보하기 위함.

또한 참조할 때도 동일하다.
값을 참조함 > 한 번에 얼마나 데이터를 읽어 들여야 할지에 대해 결정해야 한다.
어디까지 값을 읽어들이냐에 따라 데이터가 다르기 때문이다.

<br>

##### 2. 데이터 타입에 의한 값의 해석

메모리에 저장된 값은 여러 형태로 해석될 수 있다.
데이터 타입에 따라 값의 해석이 다르기 때문에 데이터 타입을 통해 개발자가 해석되길 원하는 값의 형태로 해석해줄 수 있다.

<br>
<br>

### 동적 타이핑

정적 타입 언어: 변수를 선언할 때 변수에 할당할 수 있는 데이터 타입을 사전에 선언해야 하는 언어. 선언한 데이터 타입에 맞는 값만 할당 가능.
동적 타입 언어: 변수를 선언할 때 변수에 데이터 타입을 사전에 선언할 필요가 없는 언어. 어떠한 타입의 값을 자유롭게 할당 가능.

typeof 연산자를 통하여 변수의 데이터 타입을 조사할 수 있다.

```javascript
let value = "test";
console.log(typeof value); // string
```

정적 타입 언어는 변수를 선언할 때 타입이 결정되고, 동적 타입 언어는 **할당에 의해 타입이 결정(추론)**되기 때문에 타입이 동적으로 변할 수 있다.
이러한 특성을 **동적 타이핑**이라 한다.

<br>
<br>
<br>
<br>

# 7. 연산자

연산자: 하나 이상의 표현식을 대상으로 산술/할당/비교/논리/타입/지수 연산 등을 수행하여 값을 만들어 줌.
피연산자: 연산의 대상이 되는 것. 값으로 평가될 수 있는 표현식.

<br>

### 연산자의 종류

##### 산술 연산자

피연산자를 대상으로 수학적 계산을 수행함.
산술연산이 불가능한 경우, `NaN`을 반환.

**이항 산술 연산자**
2개의 피연산자를 산술 연산하여 값을 만듬.
피연산자의 값을 변경하는 부수 효과가 없다.
ex) 덧셈(+), 뺄셈(-), 곱셈(\*), 나눗셈(/), 나머지(%)

**단항 산술 연산자**
1개의 피연산자를 산술 연산하여 값을 만듬.
피연산자의 값을 변경하는 부수 효과가 일부 존재한다.

```javascript
let x = 1;

x++; // 'x = x + 1'과 같다
x--; // 'x = x - 1'과 같다.
-x; // -1의 값을 가진다.
+x; // 값의 변화가 없다.
```

<br>

++, --의 위치에 따라 의미가 달라진다.
전위 증가/감소연산자: 연산자를 피연산자 앞에 위치하고 먼저 피연산자의 값을 선 증가/감소 후, 다른 연산을 진행.
후위 증가/감소연산자: 연산자를 피연산자 뒤에 위치하고 먼저 다른 연산을 진행한 후, 피연산자의 값을 증가/감소 시킴.

```javascript
let x;

// 전위 연산자
x = 10;
console.log(x++); // 10 출력
console.log(x); // 11 출력

x = 10;
console.log(x--); // 10 출력
console.log(x); // 9 출력

// 후위 연산자
x = 10;
console.log(++x); // 11 출력
console.log(x); // 11 출력

x = 10;
console.log(--x); // 9 출력
console.log(x); // 9 출력
```

**단항 산술 연산자 `+`는 값의 변화도 없고 부수 효과도 없는데 무슨 의미가 있나요?**
`+`는 숫자 타입이 아닌 피연산자 사용할 경우, 숫자 타입으로 변환해준다.
마치, 숫자 타입에 `+ ''`를 사용하여 문자 타입으로 변환하는 것과 같다.

<br>
<br>

##### 할당 연산자

우항에 있는 피연산자의 평가 결과를 좌항에 있는 변수에 할당함.
좌항의 변수에 할당하는 행동이므로 부수 효과가 있음.

```javascript
let x;

x = 10;
x += 5; // 'x = x + 5' 와 같다
console.log(x); // 15

x = 10;
x -= 5; // 'x = x - 5' 와 같다
console.log(x); // 5

x = 10;
x *= 5; // 'x = x *+ 5' 와 같다
console.log(x); // 50

x = 10;
x /= 5; // 'x = x / 5' 와 같다
console.log(x); // 2

x = 10;
x %= 3; // 'x = x % 5' 와 같다
console.log(x); // 1
```

<br>
<br>

##### 비교 연산자

좌항과 우항의 피연산자를 비교하여 그 결과를 불리언 값으로 반환한다.

**동등/일치 비교 연산자**
동등비교(==): 암묵적 타입 변환을 통해 타입을 일치시킨 후 값을 비교하여 같은 경우 true를 반환함.
일치비교(===): 값과 타입이 같은 경우에만 true를 반환함.

```javascript
console.log(5 == "5"); // 동등 비교, true
console.log(5 == 5); // 동등 비교, true

console.log(5 === "5"); // 일치비교, false
console.log(4 === "5"); // 일치비교, false
console.log(5 === 5); // 일치비교, true

// 주의할 것
console.log(NaN === NaN); // false
console.log(0 === -0); // true
```

**대소 관계 비교 연산자**
피연산자의 크기를 비교하여 불리언 값을 반환함.

```javascript
let x, y;

x = 10;
y = 5;
console.log(x > y); // true
console.log(x < y); // false

x = 10;
y = 10;
console.log(x >= y); // true
console.log(x <= y); // true
```

<br>
<br>

##### 삼항 조건 연산자

사용방법

> 조건식 ? 조건식이 true일 때 반환 값 : 조건식이 false일 때 반환 값

```javascript
let x, y;

x = 5;
y = 7;

console.log(x > y ? "x가 더 커요!" : "y가 더 커요!"); // "x가 더 커요!"를 출력한다.
```

삼항 조건 연산자의 표현식은 값으로 평가할 수 있는 표현식인 문이기 때문에 값처럼 사용될 수 있다.

<br>
<br>

##### 논리 연산자

피연산자를 논리 연산한다.

```javascript
let x = true;
let y = false;

// 논리합: 좌우항 하나라도 true > true
console.log(x || x); // true
console.log(x || y); // true
console.log(y || x); // true
console.log(y || y); // false

// 논리곱: 좌우항 둘 다 true > true
console.log(x && x); // true
console.log(x && y); // false
console.log(y && x); // false
console.log(y && y); // false

// 논리 부정
console.log(!x); // false
console.log(!y); // true
```

<br>
<br>

##### 그룹 연산자

소괄호 `(`, `)`로 피연산자를 감싸서 연산의 우선순위를 가장 높게 설정할 수 있다.

```javascript
console.log(5 + 10 * 3); // 35
console.log((5 + 10) * 3); // 45
```

<br>
<br>

##### typeof 연산자

피연산자의 데이터 타입을 문자열로 반환한다.
반환하는 문자열은 아래와 같다.

-   string
-   number
-   boolean
-   undefined
-   symbol
-   object
-   function

**아래는 typeof의 버그이다.**

```javascript
// 자바스크립트 버그 주의
let x = null;
console.log(typeof x); // object. null이 아니다.

// 대체 방안
console.log(x === null); // true
```

<br>
<br>

##### 지수 연산자

좌항을 '밑'으로, 우항을 '지수'로 거듭 제곱하여 숫자를 반환한다. 이는 ES7에서 도입되었고 그 전에는 Math.pow 메서드를 사용하였다.

```javascript
console.log(2 ** 3); // 8
console.log(2 ** (1 / 2)); // 1.4142135623730951
console.log(2, 0); // 1
console.log(2, -2); // 0.25

// Math.pow 메서드 사용
Math.pow(2 ** 3); // 8
Math.pow(2 ** (1 / 2)); // 1.4142135623730951
Math.pow(2, 0); // 1
Math.pow(2, -2); // 0.25
```

<br>
<br>
<br>
<br>

### 출처

위키북스, 『모던 자바스크립트 Deep Dive』, 이웅모
