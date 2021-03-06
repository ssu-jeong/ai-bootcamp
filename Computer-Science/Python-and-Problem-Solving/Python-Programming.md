## 프로그래밍과 문제해결

---

###### Warm Up 

- [데이터 과학자가 미래에 핫한 직업인 이유](https://youtu.be/dZZfDj_ieEU)

- [프로그래밍을 배워야 하는 이유](https://www.youtube.com/watch?v=SESuctdE9vM)

---

- 현실에서 발생하는 복잡한 문제를 작은 문제로 **분할하면서 해결**한다.

- 문제에 대한 **패턴을 발견**한다.

- 문제를 **최소한의 비용으로 최대한 빠르게** 해결한다.

![image](https://dojang.io/pluginfile.php/13332/mod_page/content/10/001003.png)

![image](https://dojang.io/pluginfile.php/13349/mod_page/content/4/001007.png)

[문제해결을 위한 과학적 사고](https://dojang.io/mod/page/view.php?id=2151)
[소프트웨어 교육과 파이썬](https://www.youtube.com/watch?v=DZSde316k3E)

### 프로그래밍과 기반기술

---

![image](https://github.com/Maiven/data-science/blob/main/DS&AL%E1%84%80%E1%85%AA%E1%86%AB%E1%84%80%E1%85%A8.png?raw=true)
파이썬, 알고리즘, 자료구조는 생산을 위한 도구이다.

- 파이썬 : 컴퓨터와의 소통언어(예, 수학)

- 알고리즘 : 효율적인 문제해결ㄹ방법(예, 사칙연산 또는 미적분)

- 자료구조 : 프로그램의 구조와 크기(예, 수학문제들간의 관계와 난이도)

###### <기본학습흐름>

- 파이썬 코드를 다양한 형태로 활용한다.

- 컬렉션 자료형(리스트, 튜플, 셋, 딕셔너리)을 활용한다.


## 코드로 익히는 파이썬의 다양한 활용

#### 정규표현식

---

- (데이터 분석전)정규표현식과 다양한 메소드는 데이터를 구분하기 위해 많이 활용된다.

- 실무에서의 업무(데이터분석/엔지니어링/데이터사이언스/웹개발)와 개선해야 될 서비스(웹/앱/콘텐츠)에 따라 활용하게 되는 메소드는 달라진다.

- 정규표현식과 같이 프로그래밍에서 범용적으로 쓰이는 기술들은 프로그래밍언어나 특정 기술에 종속되지 않고 쓰이기 때문에 익숙해져야 한다.

```python
#정규표현식 라이브러리
import re

wordlist = ["color", "colour","work", 
            "working","fox", "worker", "working"]

#search()는 match()와 유사하지만 패턴이 문자열의 처음부터 일치하지 않아도 된다.
for word in wordlist:
    if re.search('col.r', word) :
        print(word)

>>> color
```
```python
regular_expressions = '<html><head><title>Title</title>'
print(len(regular_expressions))

print(re.match('<.*>', regular_expressions).span())

print(re.match('<.*>', regular_expressions).group())

>>> 32
    (0, 32)
    <html><head><title>Title</title>
```
```python
# case 1_1
phone = re.compile(r"""
010-    # 핸드폰 앞자리 
\d{4}-  # 중간자리
\d{4}  # 뒷자리
""", re.VERBOSE)

# case 1_2
phone = re.compile(r"010-\d{4}-\d{4}")

# case 1_3
info = ['홍길동 010-1234-1234', '고길동 010-5678-5679']

for text in info:
    match_object = phone.search(text)
    print(match_object.group())

>>> 010-1234-1234
    010-5678-5679
````

### 다양한 메소드의 활용
---
###### rjust(width, [fillchar])

- 원하는 문자를 따로 지정하고, "a"와 같이 다른 문자열로 앞 부분을 채워줄 수 있다.

```python
print("2".rjust(3,"0"))

print("50000".rjust(5,"0"))

print("123".rjust(5,"0"))

print("123".rjust(5,"a"))

>>> 002
    50000
    00123
    aa123
```

###### zfill(width)

- 숫자 출력시 앞에 0을 붙여주고 싶을 때

```python
print("2".zfill(3))
 
print("50000".zfill(5))
 
print("123".zfill(5))

>>> 002
    50000
    00123
```
###### Split

- 문자열을 일정한 규칙으로 잘라서 리스트로 만들어 주는 함수<br>

문자열.split(sep, maxsplit) 함수는 문자열을 maxsplit 횟수만큼 sep의 구분자를 기준으로 문자열을 구분하여 잘라서 리스트로 만들어 준다.

```python
string_ = "Hello, I am Jack and I am a data scientist"
print(string_)
print(string_[1])

>>> Hello, I am Jack and I am a data scientist
    e

string_list = string_.split(" ")
print(string_list)

>>> ['Hello,', 'I', 'am', 'Jack', 'and', 'I', 'am', 'a', 'data', 'scientist']

string_.startswith('Hello')
>>> True

string_.endswith('scientist')
>>> True

string_.endswith('tist')
>>> True

print(string_.replace("Jack", "John"))
print(string_)
>>> Hello, I am John and I am a data scientist
    Hello, I am Jack and I am a data scientist
```
###### 얕은 복사(shallow copy)

```python
fruits = {"apple", "banana", "cherry"}
fruits_copy = fruits.copy()
fruits_copy
>>> {'apple', 'banana', 'cherry'}

a = {'a': 5, 'b': 4, 'c': 8}
b = a
del b['a']
print(b)
print(a)
>>> {'b': 4, 'c': 8}
    {'b': 4, 'c': 8}

import copy
a = {'a': 5, 'b': 4, 'c': 8}
b = copy.copy(a)
del b['a']
print(b)
print(a)
>>> {'b': 4, 'c': 8}
    {'a': 5, 'b': 4, 'c': 8}
```
###### 깊은 복사(deep copy())

깊은 복사는 내부에 객체들까지 새롭게 copy되는 것이다.
완전히 새로운 변수를 만드는 것.

```python
import copy
list_var = [[1,2],[3,4]]
list_var_deepcopy = copy.deepcopy(list_var)
list_var_copy = list_var.copy()

list_var[1].append(5)

print(list_var)  # 원래 변수
>>> [[1, 2], [3, 4, 5]]
print(list_var_deepcopy)  # deepcopy : append와 같은 메소드를 써도 값이 변경되지 않음
>>> [[1, 2], [3, 4]]

print(list_var_copy)  # copy : 원본이 변경되었으므로 함께 변경됨
>>> [[1, 2], [3, 4, 5]]
```

### 반복문과 조건문

---

```python
# case 1
data = [90, 45, 32, 44]
for i in range(len(data)):
   print(data[i])
>>> 90
    45
    32
    44

# case 2
mock_data = {
  "id": 1,
  "first_name": "states",
  "last_name": "code",
  "email": "code@states.com",
  "gender": "Female",
  "ip_address": "123.123.123.23"
}

for x in mock_data:
    print(x) 
>>> id
    first_name
    last_name
    email
    gender
    ip_address

# case 3
mock_data = {
  "id": 1,
  "first_name": "states",
  "last_name": "code",
  "email": "code@states.com",
  "gender": "Female",
  "ip_address": "123.123.123.23"
}

for x in mock_data.keys():
    print(x)
>>> id
    first_name
    last_name
    email
    gender
    ip_address

# case 4
mock_data = {
  "id": 1,
  "first_name": "states",
  "last_name": "code",
  "email": "code@states.com",
  "gender": "Female",
  "ip_address": "123.123.123.23"
}

for x in mock_data.values():
    print(x)
>>> 1
    states
    code
    code@states.com
    Female
    123.123.123.23

# case 5 
mock_data = {
  "id": 1,
  "first_name": "states",
  "last_name": "code",
  "email": "code@states.com",
  "gender": "Female",
  "ip_address": "123.123.123.23"
}

for x in mock_data.items():
    print(x)

for k,v in mock_data.items():
    print(k,v)
>>> ('id', 1)
    ('first_name', 'states')
    ('last_name', 'code')
    ('email', 'code@states.com')
    ('gender', 'Female')
    ('ip_address', '123.123.123.23')
    id 1
    first_name states
    last_name code
    email code@states.com
    gender Female
    ip_address 123.123.123.23

# 일반적인 반복문 활용
a = [1,2,3,4,5]
b = [10,20,30,40,50]
for i in range(len(a)):
   print(a[i],b[i])
>>> 1 10
    2 20
    3 30
    4 40
    5 50

# zip 함수 활용
a = [1,2,3,4,5]
b = [10,20,30,40,50]
c = zip(a,b)
print(list(c))
>>> [(1, 10), (2, 20), (3, 30), (4, 40), (5, 50)]

# 반복문과 zip 활용
a = [1,2,3,4,5]
b = [10,20,30,40,50]
c = [100,200,300,400,500]
for x,y,z in zip(a,b,c):
   print(x,y,z)
>>> 1 10 100
    2 20 200
    3 30 300
    4 40 400
    5 50 500  

# break
IntCollection=[0,1,2,3,4,5,6,7]
for x in IntCollection:
    if(x>1):
        break
    else:
        print(x)
>>> 0
    1 

# continue
IntCollection=[0,1,2,3,4,5,6,7]
for x in IntCollection:
    if(x>3):
        continue
    else:
        print(x)
>>> 0
    1
    2
    3

# 반복문의 다양한 활용
list_ = [1,2,3,4,5]

def foo(list_):
  print(list_)

print('foo(list_[i])')
for i in range(len(list_)):
    foo(list_[i])

print('foo(element)')
for element in list_:
    foo(element)
>>> foo(list_[i])
    1
    2
    3
    4
    5
    foo(element)
    1
    2
    3
    4
    5
```
### 에러상황파악(Error & Wanring)

---

```python
# 케이스 1 - IndentationError

def print_list(list):
for item in list: # 에러 확인 및 해결필요
print(item)

# 케이스 2 - SyntaxError

123ddf

# 케이스 3 - KeyboardInterrupt

while True:
  pass

# 케이스 4 - TypeError

print(1) / 232

a,b = 0
print(a,b)

# 케이스 5 - ZeroDivisionError

value = 2/0

# 특이 케이스 6 - 경고(warning)
def A():
  a = 0
  c =0
  print(a,c,) # 경고는 명시적으로 보이지 않지만, 메모리 비효율/휴먼 에러 등이 발생할 수 있다.
```

### 컬렉션 자료형의 내장메소드

- append(), extend(), insert()
 - a.insert(len(a),x)는 a.append(x)와 동등하다.

```python
# case1
my_list=[]
for i in range(1000, 2200):
    if (i%7==0) and (i%5!=0):
        my_list.append(str(i))

print(','.join(my_list))

# case2
my_list=[]
for i in range(1000, 2200):
    if (i%7==0) and (i%5!=0):
        my_list.insert(len(my_list), str(i))

print(','.join(my_list))

# case3
words = []
while True:
    char = input()
    if char:
        words.append(char.upper())
    else:
        # while 문을 통해 char = input() 의 입력을 계속해서 받으므로,
        # 입력할 데이터가 끝났으면 아무것도 입력하지 않고 엔터를 입력한다.
        break;

for word in words:
    print(word)

# case4
values = []
for i in range(100, 300):
    char = str(i)

    if (int(char[0])%2==0) and (int(char[2])%2==0):
        values.append(char)

print(",".join(values))

# case5
list_1 = ['bread', 'meat']
list_2 = ['Lettuce',2 ,5]
list_1.extend(list_2)

print('list1: {}, list2: {}'.format(list_1, list_2))
```
- del, remove, pop

```python
list1 = [11, 12, 43, 4, 6]
for i in list1.copy():
    if not i % 2:
        list1.remove(i)

print(list1)
>>> [11, 43]
```

```python
my_list = [1, 2, 3, 4, 5]
my_list[0] = 99

print(my_list)
>>> [99, 2, 3, 4, 5]

del my_list[0]

print(my_list)
>>> [2, 3, 4, 5]
```

```python
my_list = [1, 2, 3, 4, 5]
my_list[0] = 99

print(my_list)
>>> [99, 2, 3, 4, 5]

my_list.pop()

print(my_list)
>>> [99, 2, 3, 4]
```

- count()와 index()

```python
my_list = ['xyz', 'XYZ' 'abc', 'ABC']

print("Index for xyz : ",  my_list.index( 'xyz' ))
print("Index for ABC : ",  my_list.index( 'ABC' ))
>>> Index for xyz :  0
    Index for ABC :  2

my_list = ['xyz', 'XYZ' 'abc', 'ABC']

print("Count for xyz : ",  my_list.count( 'xyz' ))
print("Count for ABC : ",  my_list.count( 'ABC' ))
>>> Count for xyz :  1
Count for ABC :  1
```
```python
import math
def bin_search(li, element):
    bottom = 0
    top = len(li)-1
    index = -1
    while top >= bottom and index == -1:
        mid = int(math.floor((top+bottom) / 2.0))
        if li[mid] == element:
            index = mid
        elif li[mid] > element:
            top = mid-1
        else:
            bottom = mid+1

    return index

li=[2,5,7,9,11,17,222]

print(bin_search(li,11))
print(bin_search(li,102))
>>> 4
    -1
```

```python
li = [12,24,35,70,88,120]
for (i,x) in enumerate(li):
   if i not in (0,3,5):
     li = x

print(li)
>>> 88

def list_update(data):
    new_li=[]
    new_set = set()
    for item in data:
        if item not in new_set:
            new_set.add(item)
            new_li.append(item)

    return new_li

list_test=[120,120,10,20,30,20]

print(list_update(list_test))
>>> [120, 10, 20, 30]
```

- sort와 sorted
  
  - sort()의 경우 기존 값을 기본 오름차순으로 정렬 -> 원래 목록 영향 O

  - sorted()의 경우 기존의 값은 내비두고 새롭게 정렬된 리스트로 반환

```python
#sort()
a = [1,3,2,5,4]
a.sort()

print(a)
>>> [1,2,3,4,5]

#sorted()
b = [1,3,2,5,4]
result = sorted(b)

print(result)
print(b)
>>> [1,2,3,4,5]
    [1,3,2,5,4]
```

```python
from operator import itemgetter
l = []
while True:
    s = input()
    if not s:
        break
    l.append(tuple(s.split(",")))

print(sorted(l, key=itemgetter(0,1,2)))

# 입력 테스트 시, ('dave', 'B', 10) 처럼 아이템인덱스 채워주기
```

- get()

선언된 dict에서 출력하고자 하는 key가 있으면, 그에 해당하는 value를 출력해준다. 
만일 출력하고자 하는 key가 없으면 오류가 아닌 None을 출력.

```python
dic = {}
s=input()
for s in s:
    dic[s] = dic.get(s,0)+1

print('\n'.join(['%s,%s' % (k, v) for k, v in dic.items()]))
```

### 람다(lambda)

---

###### 람다 활용 목적

- 함수는 컴퓨터 과학과 수학의 기초를 이루는 개념
<br>
- 람다 대수는 함수를 단순하게 표현할 수 있도록 하여 **함수의 계산**이라는 개념을 더 깊이 이해할 수 있게 돕는다.
<br>
- 람다는 인라인으로 작성할 수 있어 전체 함수보다 읽기 쉽다. 
-> 함수표현식의 규모가 작을 떄 람다를 사용하는 것이 좋음
<br>
- 람다 함수의 장점은 함수 객체를 반환한다.
  -> 함수 객체를 인수로 필요로 하는 map 또는 filter와 같은 함수와 함께 사용할 떄 유용.

```python
# 함수정의
define_word = (lambda word1,define :  word1 * define)

# 함수호출
result = define_word('call_result_',5)

# 결과출력
print(result)
>>> call_result_call_result_call_result_call_result_call_result_
```

```python
# 리스트 생성
spelling = ["test1", "test2", "test4 test5", "test3"]

# 람다함수적용
shout_spells = map(lambda item: item + ('!!!'), spelling)

# 리스트형태로 변환
shout_spells_list = list(shout_spells)

# 결과출력
print(shout_spells_list)
>>> ['test1!!!', 'test2!!!', 'test4 test5!!!', 'test3!!!']
```

```python
# 리스트 생성
fellowship = ['frodo', 'samwise', 'merry', 'pippin', 'aragorn', 'boromir', 'legolas', 'gimli', 'gandalf']

# 람다함수적용
result = filter(lambda member: len(member) > 6, fellowship)

# 리스트형태로 변환
result_list = list(result)

# 결과출력
print(result_list)
>>> ['samwise', 'aragorn', 'boromir', 'legolas', 'gandalf']
```

```python
# functools 모듈 사용
from functools import reduce

# 리스트 생성
stark = ['robb', 'sansa', 'arya', 'brandon', 'rickon']

# 람다함수적용
result = reduce(lambda item1, item2:  item1+item2, stark)

# 결과출력
print(result)
>>> robbsansaaryabrandonrickon
```

### Review

---

오늘 배운 것

```
1) 파이썬의 다양한 활용법
2) 파이썬 메소드의 활용
3) 파이썬 컬렉션 자료형의 활용 
```

오늘 해야할 것

```
1) 수학기본개념이 들어간 파이썬 코드를 다양하게 활용해보기
2) 컬렉션 자료형에 대해 생각해보기
```

### Reference

---

[리스트 슬라이싱](https://docs.python.org/ko/3/tutorial/introduction.html#lists)

[if문 다루기](https://www.acmicpc.net/step/4)

[for문 다루기](https://www.acmicpc.net/step/3)

[문자열 다루기](https://www.acmicpc.net/step/7)
