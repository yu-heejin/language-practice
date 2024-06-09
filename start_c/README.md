## Mac에서 C언어 시작하기
```
gcc hello.c -o hello
./hello
```
```
vi hello.c
make hello
./hello
```

## Hello World 살펴보기

```c
#include <stdio.h>
```

- `stdio.h`라는 파일에 있는 내용을 삽입한다는 의미
    - 해당 작업은 전처리기가 수행한다.
- `#`문자로 시작하는 라인은 Directives(지시문 혹은 지시어)라고 한다.
- 터미널에서 `ls /usr/include/stdio.h` 명령을 입력하면 stdio.h 파일이 있는 것을 확인할 수 있다.
- stdio는 standard input output의 줄임말로, 표준 입출력이라는 뜻이다.
    - 표준 입출력에서는 화면에 내용을 출력하고, 사용자로부터 무엇인가를 입력받는 기능들을 제공한다.
    - `.h`는 헤더 파일의 확장자인데, 헤더 파일이란 다른 소스 코드에 포함되기 위한 내용들을 모아놓은 파일이라 생각하면 된다.

```c
int main(void)
```

- main이라는 이름의 함수를 정의한다.
- **C로 만드는 모든 유저 프로그램은 main 함수에서 시작**한다.
- void는 main 함수가 실행될 때 전달받는 인자가 없다는 이야기이다.

```c
return 0;
```

- 0을 반환하며 종료한다는 의미이다.
- main 함수가 반환하는 값은 일반적으로 운영체제에 전달된다.
    - 즉, 리눅스에게 프로그램을 종료하며 0을 반환한다.
    - 운영체제는 반환 값을 가지고 있다가, 부모 프로세스가 해당 값을 받아서 프로그램이 정상적으로 종료되었는지 판단한다.
    - 보통 정상 종료를 판단할 때 반환 값이 0이라면, 정상이라고 판단하기 때문에 0을 반환한 것이다.

## C언어의 구성 요소

- C언어는 크게 선언(declaration)과 정의(definition)으로 이루어져 있다.
- 함수를 정의하면, 함수는 명령문들의 모음으로 이루어지게 된다.
    - 명령문은 식 연산 문장(expression statement)이나 점프 문장(jump statement) 등 여러 종류가 있다.
    - 이러한 명령문들과 선언들이 모여 복합 문장(compound statement)를 구성하게 된다.

## main 찍어먹기

- `main` 함수는 우리가 작성할 모든 C 유저 프로그램의 시작점이라고 한다.
- `main` 함수는 다른 함수들과 다르게 다음과 같이 특정한 두 개의 형태로만 정의할 수 있다.
    
    ```c
    // 1번 형태
    int main(void) 
    {
      /* ... */ 
      return 0;
    }
    
    // 2번 형태
    int main(int argc, char *argv[])
    {
      /* ... */
      return 0;
    }
    ```
    
    - 1번은 `main` 함수에 전달하는 것이 없을 때 사용하고, 2번은 `main` 함수에 무언가 전달할 인자가 있을 때 사용한다.
    

## printf 찍어먹기

- `printf` 함수는 **인자의 개수나 타입이 미리 정해지지 않았다는 것이 특징**이다.

### 서식 문자

```c
// simple_printf.c
#include <stdio.h>

int main(void)
{
    printf("First natural number is %d \n", 1);
    printf("Second natural number is %d \n", 2);
    printf("Pi is %f \n", 3.14);
    printf("First alphabet is %c \n", 'A');
    printf("I Like %s \n", "C Programming");
    printf("%d * %d = %d\n%d * %d = %d\n", 2, 1, 2, 2, 2, 4);
    return 0;
}
```

- `%d`, `%f`, `%c`, `%s` 같은 문자들을 서식 문자라고 한다.
- `printf`의 인자로 전달한 다른 값으로 치환된다.