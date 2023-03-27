# PlantUML - Sequence diagram

<br>

## 1. Introduction

<br>

```plantuml
@startuml
!pragma teoz true

title Sequence diagram example
autonumber

participant A
participant B
queue Q

A->B: Activate request
B --> Q++: Activate
A<-B: Activate done

A->B: Job input
B-->Q: Add(Job)
A<-B: Input success
&Q-->C++: Send start signal

C-->C: Working...
Q<--C--: Work done
B<--Q: Job done
A<-B: Job done

A->B: Deactivate
B <-- Q--: Deactivate
A<-B: Deactivate done
@enduml
```

<br>

1. 위 그림과 같이, 정해진 흐름을 따라 그려진 다이어그램을 시퀀스 다이어그램이라 한다.
2. 시퀀스 다이어그램의 구성요소는 아래와 같다.
    1. 객체
    2. 상호작용 (시퀀스)
3. 시퀀스 다이어그램을 통해 아래 항목 등을 파악할 수 있다.
    - 작업 항목
    - 객체간 관계
    - 각 객체의 작업 순서 및 라이프타임<br>
    $\vdots$

<br><br>

## 2. 기본 사용법

<br>

1. `객체`를 선언한 후, `->`, `-->` 등의 시퀀스를 이용해 다이어그램을 그린다.

<br>

<table>
<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>
@startuml<br><br>
participant A<br>
participant B<br>
<br>
A -> B : Hello world!<br>
A <- B : Hello!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
participant A
participant B

A->B: Hello world!
A<--B: Hello!
@enduml
```
</td>
</tr>
</table>

<br>

## 3. 세부 사용법

<br>

### 3.1. 객체 사용법

<br>

#### 3.1.1. 객체 선언

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>
@startuml<br><br>
participant P<br>
actor A<br>
boundary B<br>
control C<br>
entity E<br>
database D<br>
collections CO<br>
queue Q<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
participant P
actor A
boundary B
control C 
entity E
database D
collections CO
queue Q
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.1.2. 객체 활용

<br>

##### 3.1.2.1. 객체 이름에 특수문자 삽입

<br>

1. `쌍따옴표 ""` 사용하여 지정

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
participant "P()" as p<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
participant "P()" as p
@enduml
```
</td>
</tr>

</table>

<br>

##### 3.1.2.2. 객체 별칭 지정

<br>

1. `as` 사용하여 지정

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
participant Participant as p<br>
actor Actor as a<br>

p -> a : hello<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
participant Participant as p
actor Actor as a

p -> a : hello
@enduml
```
</td>
</tr>

</table>

<br>

##### 3.1.2.3. 객체 순서 지정

<br>

1. `order n` 사용하여 지정

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
participant P order 3<br>
actor A order 1<br>
boundary B order 2<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
participant P order 3
actor A order 1
boundary B order 2
@enduml
```
</td>
</tr>

</table>

##### 3.1.2.4. 객체 색상

<br>

1. `#colorname` or `#colorcode` 사용하여 지정

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
participant P #mediumseagreen<br>
actor A #magenta<br>
boundary B #13ab32<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
participant P #mediumseagreen
actor A #magenta
boundary B #13ab32
@enduml
```
</td>
</tr>

</table>

<br>

##### 3.1.2.5. 객체 세부 선언

<br>

1. `대괄호 []` 사용하여 지정

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
actor A [<br>
    =Upper<br>
    ----<br>
    ""Lower""<br>
]<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
actor A [
    =Upper
    ----
    ""Lower""
]
@enduml
```
</td>
</tr>

</table>

<br>

### 3.2. 시퀀스 사용법

<br>

#### 3.2.1. 시퀀스 선언

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
a -> b : message<br>
a --> b<br>
a <-> b<br>
a ->x b<br>
a ->o b<br>
a -\ b<br>
a -/ b<br>
a ->> b<br>
a -\\ b<br>
a -// b<br>
a -> a<br>
a ->(20) b : Slanted<br>

?-> b : Short incoming<br>
[-> b : Long incoming<br>
a ->? : Short outgoing<br>
a ->] : Long outgoing<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
a -> b : message
a --> b
a <-> b
a ->x b
a ->o b
a -\ b
a -/ b
a ->> b
a -\\ b
a -// b
a -> a
a ->(20) b : Slanted

?-> b : Short incoming
[-> b : Long incoming
a ->? : Short outgoing
a ->] : Long outgoing

a-[hidden]>b:Make it very long long long long 
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.2.2. 시퀀스 활용 

<br>

##### 3.2.2.1. 시퀀스 색상

<br>

1. `#colorname` or `#colorcode` 사용하여 지정

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
a -[#cyan]> b : Change by name<br>
a -[#1204fb]> b : Change by code<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
a -[#cyan]> b : Change by name
a -[#1204fb]> b : Change by code
@enduml
```
</td>
</tr>

</table>

<br>

##### 3.2.2.2. 여러 줄 메시징

<br>

1. `\n` 사용하여 여러 줄 메시지 삽입

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
a -> b : This is\nvery long and\nmultiline\nmessage<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
a -> b : This is\nvery long and\nmultiline\nmessage
@enduml
```
</td>
</tr>

</table>

<br>

##### 3.2.2.3. 메시지 번호

<br>

1. `autonumber` 키워드로 번호 삽입
2. 필드 구분을 위해 `.`, `,`, `;`, `:` 네 가지 Delimiter가 지원된다.

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
autonumber<br>
a -> b : 1st<br>
a -> b : 2nd<br>

autonumber 10<br>
a -> b : 10th<br>

autonumber 20 10<br>
a -> b : 20th<br>
a -> b : 30th<br>

autonumber stop<br>
a -> b : Temp stop<br>
autonumber resume 1<br>
a -> b : Resume<br>
a -> b : Next<br>

autonumber 1.1.1<br>
a -> b : Change format<br>
a -> b : Next<br>
autonumber inc A<br>
a -> b : Increase first<br>
autonumber inc B<br>
a -> b : Increase second<br>

a -> b : Number of this time is %autonumber%<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
autonumber
a -> b : 1st
a -> b : 2nd

autonumber 10
a -> b : 10th

autonumber 20 10
a -> b : 20th
a -> b : 30th

autonumber stop
a -> b : Temp stop
autonumber resume 1
a -> b : Resume
a -> b : Next

autonumber 1.1.1
a -> b : Change format
a -> b : Next
autonumber inc A
a -> b : Increase first
autonumber inc B
a -> b : Increase second

a -> b : Number of this time is %autonumber%
@enduml
```
</td>
</tr>

</table>

<br>

### 3.3. 생명선 사용법

<br>

#### 3.3.1. 생명선 선언

<br>

1. `activate` 또는 `++`로 활성화
2. `deactivate` 또는 `--`, `return`으로 종료
    - `return`은 마지막 생명선 활성화 지점의 출발점을 리턴
3. `destroy` 또는 `!!`는 `X` 표시와 함께 완전히 끝났음을 표현
4. 각 키워드는 바로 이전의 시퀀스에 적용

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
a -> b : Activate<br>
activate b<br>
a -> b : Deactivate<br>
deactivate b<br>

b -> c ++ : Activate<br>
c -> b -- : Deactivate<br>

a -> b ++ : Activate<br>
a -> b ++ : Additional active<br>
return Return<br>

b -> c --++ : Deactivate and activate<br>

b -> c : Destroy<br>
destroy c<br>
a -> b !! : Destroy<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
a -> b : Activate
activate b
a -> b : Deactivate
deactivate b

b -> c ++ : Activate
c -> b -- : Deactivate

a -> b ++ : Activate
a -> b ++ : Additional active
return Return

b -> c --++ : Deactivate and activate

b -> c : Destroy
destroy c
a -> b !! : Destroy
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.3.2. 생명선 활용

##### 3.3.2.1. 생명선 색상

<br>

1. `#colorname` or `#colorcode` 사용하여 지정

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
a -> b ++ #crimson : Activate<br>
b -> c ++ #34ab22 : Activate<br>
return end<br>
return end<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
a -> b ++ #crimson : Activate
b -> c ++ #34ab22 : Activate
return end
return end
@enduml
```
</td>
</tr>

</table>

<br>

### 3.4. Note 사용법

<br>

#### 3.4.1. Note 선언

<br>

1. `note` 키워드를 사용하여 선언
2. 여러 줄의 노트를 추가하는 경우에는 반드시 `end note` 사용

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
a -> b : Message<br>
note left : first note<br>
note right : second note<br>
a ->b : Message<br>
note left<br>
Multi<br>
line<br>
note<br>
end note<br>

note over a : Note over a<br>
note left of b : Note left of b<br>
note right of a : Note right of a<br>
note right of a : Note aligned<br>
/ note right of b : Note aligned<br>

note over a,b<br>
Note over<br>
selected<br>
objects<br>
end note<br>
note across : Note over all objects<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
a -> b : Message
note left : first note
note right : second note
a ->b : Message
note left
Multi
line
note
end note

note over a : Note over a
note left of b : Note left of b
note right of a : Note right of a
note right of a : Note aligned
/ note right of b : Note aligned 

note over a,b
Note over
selected
objects
end note
note across : Note over all objects
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.4.2. Note 활용

<br>

##### 3.4.2.1. Note 모양

<br>

1. `hnote` : 육각형
2. `rnote` : 사각형

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
hnote over a : hnote<br>
rnote over a : rnote<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
hnote over a : hnote
rnote over a : rnote
@enduml
```
</td>
</tr>

</table>

<br>

##### 3.4.2.2. Note 색상

<br>

1. `#colorname` or `#colorcode` 사용하여 지정

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
note over a #skyblue : Skyblue<br>
note over a #faacfb : Color code<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
note over a #skyblue : Skyblue
note over a #faacfb : Color code
@enduml
```
</td>
</tr>

</table>

<br>

### 3.5. Layout

<br>

#### 3.5.1. Mainframe

1. `mainframe`을 사용하여 다이어그램 frame 추가

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
mainframe main<br>

a -> b : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
mainframe main

a -> b : Hello world!
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.5.2. Page

1. `newpage`를 사용하여 다이어그램 페이지 추가
2. `newpage` 뒤에 새 페이지의 [`Title`](#353-title) 입력 가능

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
a -> b : Hello world!<br>

newpage<br>

a -> b : Next page!<br>

newpage Last page<br>

a -> b : Last page!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
a -> b : Hello world!

newpage

a -> b : Next page!

newpage Last page

a -> b : Last page!
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.5.3. Title

<br>

1. `title` 키워드를 이용하여 다이어그램 타이틀 생성
2. `\n` 이용하여 멀티라인 타이틀 생성 가능
3. `title`, `end title` 이용하여 멀티라인 타이틀 생성 가능

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
title MyTitle<br>

a -> b : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
title MyTitle

a -> b : Hello world!
@enduml
```
</td>
</tr>

<tr>
<td>

@startuml<br><br>
title My\nmulti line\ntitle<br>

a -> b : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
title My\nmulti line\ntitle

a -> b : Hello world!
@enduml
```
</td>
</tr>

<tr>
<td>

@startuml<br><br>
title<br>
My<br>
multi line<br>
title<br>
end title<br>

a -> b : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
title
My
multi line
title
end title

a -> b : Hello world!
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.5.4. Header, footer

<br>

1. `header`, `footer`를 이용하여 머리말, 꼬리말 표시
2. `%page%`, `%lastpage%`를 이용하여 현재 페이지 및 전체 페이지 수 표시 가능

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
header Header<br>
footer Page %page% of %lastpage%<br>

title MyTitle<br>

a -> b : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
header Header
footer Footer

title MyTitle

a -> b : Hello world!
@enduml
```
</td>
</tr>

<tr>
<td>

@startuml<br><br>
header Header<br>
footer Page %page% of %lastpage%<br>

a -> b : Hello world!<br>

newpage<br>

a -> b : Next page!<br>

newpage Last page<br>

a -> b : Last page!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
header Header
footer Page %page% of %lastpage%

a -> b : Hello world!

newpage

a -> b : Next page!

newpage Last page

a -> b : Last page!
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.5.5. 객체 생성

<br>

1. 시퀀스로 인해 객체가 생성되는 것을 표시하기 위해 사용
2. 시퀀스 바로 전에 `create` 를 사용하여 생성
3. 시퀀스에 `**` 를 이용하여 생성

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
participant a<br>

create b<br>
a -> b : Hello world!<br>
a -> c ** : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
participant a

create b
a -> b : Hello world!
a -> c ** : Hello world!
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.5.6. 객체 그룹

<br>

1. `box` 및 `end box` 를 이용하여 객체 그룹 형성
2. 그룹 타이틀 및 색상 지정 가능

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
box<br>
participant a<br>
end box<br>

box "Others" #mediumseagreen<br>
participant b<br>
participant c<br>
end box<br>

a -> b : Hello world!<br>
a -> c : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
box
participant a
end box

box "Others" #mediumseagreen
participant b
participant c
end box

a -> b : Hello world!
a -> c : Hello world!
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.5.7. 객체 Stereotype 추가

<br>

1. `<<` 및 `>>` 를 이용하여 객체에 Stereotype 추가
2. `(Symbol, #color)` 를 이용하여 Spot 추가

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
participant a << StereoType >><br>
participant b << (S,#12fcba) >><br>
participant c << (S,#12fcba) StereoType >><br>

a -> b : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
participant a << StereoType >>
participant b << (S,#12fcba) >>
participant c << (S,#12fcba) StereoType >>

a -> b : Hello world!
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.5.8. 객체 Footer 제거

<br>

1. `hide footbox` 를 이용하여 객체 footer 제거

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
hide footbox<br>

a -> b : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
hide footbox

a -> b : Hello world!
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.5.9. 미사용 객체 제거

<br>

1. `hide unlinked` 를 이용하여 미사용 객체 제거

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
participant a<br>
participant b<br>
participant c<br>

a -> b : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
participant a
participant b
participant c

a -> b : Hello world!
@enduml
```
</td>
</tr>

<tr>
<td>

@startuml<br><br>
hide unlinked<br>

participant a<br>
participant b<br>
participant c<br>

a -> b : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
hide unlinked

participant a
participant b
participant c

a -> b : Hello world!
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.5.10. 공백, Delay, 구분선

<br>

1. `|||` 및 `||size||` 를 이용하여 공백 추가
2. `...` 및 `... 메시지 ...` 를 이용하여 Delay 추가
3. `====` 및 `== 메시지 ==` 를 이용하여 구분선 추가

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
a -> b : Hello world!<br>

|||<br>
||50||<br>

...<br>
... Some times later ...<br>

====<br>
== Clear ==<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
a -> b : Hello world!

|||
||50||

...
... Some times later ...

====
== Clear ==
@enduml
```
</td>
</tr>

</table>

<br>

#### 3.5.11. 시퀀스 그룹

<br>

1. 다음 키워드를 사용하여 시퀀스 그룹 생성
    - `alt`, `else` : `if` / `else` 와 같음
    - `opt`
    - `loop`
    - `par`
    - `break`
    - `critical`
    - `group` : `[]` 를 이용하여 추가 문자 출력 가능
2. `end` 를 사용하여 그룹을 닫음
3. `#colorname` or `#colorcode` 사용하여 색상 지정

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
a -> b : Hello world!<br>

alt case 1<br>
    b -> a : Hello world!<br>

else case 2<br>
    opt send message<br>
        a -> b : Hello?<br>
    end<br>

else case 3<br>
    loop retry<br>
        a -> b : Hello?<br>
    end<br>

else case 4<br>
    group Find new friends [Who will be?]<br>
        a -> c : Hello world!<br>
    end<br>
end<br>

alt#skyblue #31a2f3 Add color<br>
    a -> b : Hello world!<br>
else #af3a7b Color case<br>
    a -> c : Hello world!<br>
end<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
a -> b : Hello world!

alt case 1
    b -> a : Hello world!

else case 2
    opt send message
        a -> b : Hello?
    end

else case 3
    loop retry
        a -> b : Hello?
    end

else case 4
    group Find new friends [Who will be?]
        a -> c : Hello world!
    end
end

alt#skyblue #31a2f3 Add color
    a -> b : Hello world!
else #af3a7b Color case
    a -> c : Hello world!
end
@enduml
```
</td>
</tr>

</table>

<br>

## 4. 기타

<br>

### 4.1. 테마 적용

<br>

1. `!theme` 키워드를 통해 다이어그램에 테마 적용 가능
2. `help themes` 로 적용 가능 테마 리스트 확인 가능
3. 테마 별 상세 정보는 [PlantUML themes Gallery](https://the-lum.github.io/puml-themes-gallery/) 에서 확인

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
!theme mars<br>

a -> b : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
!theme mars

a -> b : Hello world!
@enduml
```
</td>
</tr>

<tr>
<td>

@startuml<br><br>
help themes<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
help themes
@enduml
```
</td>
</tr>

</table>

<br>

### 4.2. Skinparam

<br>

1. 다이어그램 내 요소에 대한 스타일 지정
2. `skinparameters`로 사용 가능한 파라미터 목록 확인 가능
3. `skinparam paramname value`로 파라미터 set
4. 자세한 정보는 [Skinparam command](https://plantuml.com/ko/skinparam)을 참조

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
skinparameters<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
skinparameters
@enduml
```
</td>
</tr>

<tr>
<td>

@startuml<br><br>
skinparam sequenceMessageAlign center<br>

a -> b : Hello world!<br>
b -> a : Hello world, too!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
skinparam sequenceMessageAlign center

a -> b : Hello world!
b -> a : Hello world, too!
@enduml
```
</td>
</tr>

<tr>
<td>

@startuml<br><br>
skinparam ParticipantPadding 30<br>
skinparam BoxPadding 20<br>

box<br>
participant a<br>
end box<br>

box "Others" #mediumseagreen<br>
participant b<br>
participant c<br>
end box<br>

a -> b : Hello world!<br>
a -> c : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
skinparam ParticipantPadding 30
skinparam BoxPadding 20

box
participant a
end box

box "Others" #mediumseagreen
participant b
participant c
end box

a -> b : Hello world!
a -> c : Hello world!
@enduml
```
</td>
</tr>

</table>

<br>

### 4.3. teoz rendering engine

<br>

1. `PlantUML`의 몇몇 기능은 `teoz rendering engine`을 통해 확장이 가능하다.
2. `teoz rendering engine`을 사용하기 위해서는 `!pragma teoz true` 를 입력해주면 된다.

<br>

#### 4.3.1. Nested object group

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
!pragma teoz true<br>

box<br>
participant a<br>
box "Others" #mediumseagreen<br>
participant b<br>
participant c<br>
end box<br>
end box<br>

a -> b : Hello world!<br>
a -> c : Hello world!<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
!pragma teoz true

box
participant a
box "Others" #mediumseagreen
participant b
participant c
end box
end box

a -> b : Hello world!
a -> c : Hello world!
@enduml
```
</td>
</tr>

</table>

<br>

#### 4.3.2. 동시성 확장

<br>

1. `&` 기호를 사용하여 동시에 일어나는 요소를 표현할 수 있다.

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
!pragma teoz true<br>

a -> b : Hello world!<br>
& b -> c : Hello world!<br>

note left of a : I'm a<br>
& note right of b : I'm b<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
!pragma teoz true

a -> b : Hello world!
& b -> c : Hello world!

note left of a : I'm a
& note right of b : I'm b
@enduml
```
</td>
</tr>

</table>

<br>

#### 4.3.3. Anchor

<br>

1. `{start}`, `{end}` 지정을 통해 Time gap 표시를 할 수 있다.

<br>

<table>
<colgroup>
    <col style="width: 30%">
    <col style="width: 50%">
<colgroup>

<tr>
<th>Code</th><th>Render</th>
</tr>

<tr>
<td>

@startuml<br><br>
!pragma teoz true<br>

{start} a -> b : Hello world!<br>
{end} b -> a : Hi!<br>
{start} <-> {end} : Duration<br><br>
@enduml
</td>
<td>

```plantuml
@startuml
!pragma teoz true
skinparam responseMessageBelowArrow true

{start} a -> b : Hello world!
||40||
{end} b -> a : Hi!
{start} <-> {end} : Duration
@enduml
```
</td>
</tr>

</table>