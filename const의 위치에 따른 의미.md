#const의 위치에 따른 의미
##const와 자료형

#####1. 자료형의 왼쪽과 오른쪽에 붙은 const는 같은 의미를 지닌다.
###### ex)
###### `const int* a == int const* a`
###### `const int** a == int const** a`

#####2. const 와 포인터 연산자 \* 의 위치에 따른 의미는 아래와 같다.
|선언된 형식|`const int ** a`|`int * const * a`|`int ** const a`|
|:--:|:--:|:--:|:--:|
|`a`|const int\*\* 형 (값 변경 ○)|int\*const\* 형 (값 변경 ○)|**int\*\*const 형 (값 변경 ⅹ)**|
|`*a`|const int\* 형 (값 변경 ○)|**int\*const 형 (값 변경 ⅹ)**|int\* 형 (값 변경 ○)|
|`**a`|**const int 형 (값 변경 ⅹ)**|int 형 (값 변경 ○)|int 형 (값 변경 ○)|

#####※ void \* 형의 특성

`void*`형은 **주소값**을 먼저 저장하고, 형 변환을 통하여 **자료형 타입**을 나중에 정한다.
따라서 `void*` 자체적으로는 **값**을 변환할 수 없다.

##const와 함수
**const** 자료형 역시 자료형의 하나이기 때문에 다음과 같이 사용할 수 있다.
```C
const int foo(int a);

const int foo(int a){
...
}
```
위와 같이 사용된 경우에는 `foo`함수의  `return`값이 **const** 자료형으로 반환된다.

C++에서는 **const** 가 다음과 같은 위치에 사용되기도 한다.
```C++
class Point{
public:
	Point();
    Point(int x);
    Point(int x, int y);
    int getX() const;
    int getY() const;
private:
	int x;
    int y;
};
```

이 때 함수에 붙여진 **const**의 의미는 **이 함수는 멤버변수의 값을 가져다 쓸 수는 있지만 변경할 수 는 없다.** 라는 의미를 갖는다.

```C++
...
int Point :: getX() const{
	x = 5; 					//error.
    return x;
}
...
```
