
좋아요! Map과 Set의 사용법을 정리해드리겠습니다.

## Map (맵)

> Map은 **키-값 쌍**을 저장하는 자료구조입니다. 객체와 비슷하지만 몇 가지 중요한 차이점이 있어요.

### Map 생성 및 기본 메서드

```javascript
// 생성
const map = new Map();

// 값 추가/수정
map.set('name', '철수');
map.set('age', 25);
map.set(1, 'number key');  // 키로 숫자도 가능
map.set({id: 1}, 'object key');  // 객체도 키로 사용 가능!

// 값 가져오기
map.get('name');  // '철수'
map.get('age');   // 25

// 존재 여부 확인
map.has('name');  // true
map.has('job');   // false

// 삭제
map.delete('age');  // true (삭제 성공)

// 크기 확인
map.size;  // 2

// 전체 삭제
map.clear();
```

### Map 순회

```javascript
const map = new Map([
  ['a', 1],
  ['b', 2],
  ['c', 3]
]);

// for...of로 순회
for (let [key, value] of map) {
  console.log(`${key}: ${value}`);
}

// forEach
map.forEach((value, key) => {
  console.log(`${key}: ${value}`);
});

// keys, values, entries
map.keys();     // MapIterator {'a', 'b', 'c'}
map.values();   // MapIterator {1, 2, 3}
map.entries();  // MapIterator {['a', 1], ['b', 2], ['c', 3]}
```

---

## Set (셋)

Set은 **중복되지 않는 고유한 값**들의 집합입니다.

### Set 생성 및 기본 메서드

```javascript
// 생성
const set = new Set();

// 값 추가
set.add(1);
set.add(2);
set.add(3);
set.add(2);  // 중복 값은 무시됨

console.log(set);  // Set {1, 2, 3}

// 배열로부터 생성 (중복 제거에 유용!)
const set2 = new Set([1, 2, 2, 3, 3, 4]);
console.log(set2);  // Set {1, 2, 3, 4}

// 존재 여부 확인
set.has(2);  // true
set.has(5);  // false

// 삭제
set.delete(2);  // true

// 크기
set.size;  // 2

// 전체 삭제
set.clear();
```

### Set 순회

```javascript
const set = new Set(['apple', 'banana', 'orange']);

// for...of
for (let item of set) {
  console.log(item);
}

// forEach
set.forEach(item => {
  console.log(item);
});

// Set을 배열로 변환
const arr = [...set];  // 또는 Array.from(set)
```

---

## 객체 vs Map, 배열 vs Set

**언제 Map을 쓸까?**
- 키가 문자열이 아닌 경우 (숫자, 객체 등)
- 키-값 쌍을 자주 추가/삭제할 때
- 순서가 중요할 때 (Map은 삽입 순서 유지)
- 크기를 자주 확인할 때 (size 프로퍼티)

**언제 Set을 쓸까?**
- 중복을 제거하고 싶을 때
- 값의 존재 여부만 확인하면 될 때
- 집합 연산(합집합, 교집합 등)을 할 때
