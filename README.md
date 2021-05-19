### 5주차 Django. 
url list:  
- '/': 자기소개  
- '/brain': 재고관리  

---

4주차에 주어지는 과제는 여러분의 역량에 맞게 진행하실 수 있습니다.

날마다 필수 과제를 진행해주시고, 이를 끝냈다면 보너스 과제를 진행할 수 있습니다.

과제는 해당 폴더에 작업했던 파일들을 복사해서 옮겨주시고, PR을 날려주세요.

PR를 날릴 때 **반드시** base의 branch가 week4인지 확인해주세요.

진행하다가 부족한 부분이 있다면 **학습**을, 그리고 **기록**을 남겨봅시다 🖊

---

# Day 1 - Flask를 Flask 답게

실습에서는 `GET` 과 `POST` 를 이용해서 `/menu` 자원으로부터 데이터를 가지고오고, 자원에 데이터를 추가해보았습니다. 이는 자원에서 할 수 있는 4가지 logic인 CRUD(Create, Read, Update, Delete) 중 Create와 Read에 해당하는 부분입니다. 이를 바탕으로 다음 과제를 해결해봅시다.

### 필수 과제 : 메뉴 관리 CRUD 구현하기

- HTTP 메서드 `PUT` 를 이용해 Update, `DELETE` 를 이용해 Delete 기능을 구현해주세요.
- `PUT /menu/<int:id>` : 해당하는 id에 해당하는 데이터를 갱신합니다. (HTTPRequest으로 Body가 주어집니다.)
- `DELETE /menu/<int:id>` : 해당하는 id에 해당하는 데이터를 삭제합니다.
- `@app.route()` 의 인자로 들어가는 경로에는 다음과 같이 사용해줄 수도 있습니다.

```python
@app.route('/<name>') # URL에 <>를 붙임으로서 이를 함수의 인자로 대입할 수 있습니다.
def my_view_func(name):
    return name
```

### 보너스 과제 I: ID야 움직여라 얍!

- 새로운 menu를 추가하는 `POST` 영역에서 id가 4로 고정되어있는 문제가 발생합니다.
- POST 요청이 들어올 때마다 id가 하나씩 증가하여 `menu` 리스트에 추가될 수 있도록 코드를 수정해주세요.
- 이 과제는 필수 과제 이후에 진행되어야 합니다.

### 보너스 과제 II : 데이터베이스 연동하기

- 수업에서 다룬 API는 서버를 재시작하면 모든 정보가 리셋되는 치명적인 문제가 있었습니다. 이를 해결하기 위해 데이터만을 저장하는 **데이터베이스**를 도입하여 Flask과 연동할 필요가 생겼습니다.
- SQL과 ORM 중 하나를 선택하여 데이터베이스와 Flask app을 연동해봅시다. (즉, 자원에 CRUD가 발생하면 이 정보가 데이터베이스에 저장되어야합니다.)
- 이 과제는 필수 과제, 보너스 과제 I 이후에 진행되어야 합니다.

---

# Day 3 - Django로 자기소개 페이지 만들기

### 필수 과제 : 아이엠 그라운드 자기소개 하기

- 다음 요청을 처리하는 웹 어플리케이션을 제작해주세요.
- `GET /` → **자기소개 웹 페이지**를 Response
    - 이 페이지는 HTML을 이용해서 여러분이 원하는 내용을 작성해주세요.

### 보너스 과제 : ⭐️아이😊엠 그라운드⛳️ 자기💁‍♀️소개💁‍♂️ 하기⭐️

- CSS나 JavaScript를 이용해 자신의 웹 페이지를 더욱 멋있게 만들 수 있습니다. HTML으로만 된 밋밋한 자기소개 페이지를 꾸며봅시다.
- 이들을 사용하기 위해선 이 파일들이 담긴 경로를 [STATIC_URL](https://docs.djangoproject.com/en/3.1/howto/static-files/)을 이용해 지정해주어야합니다.

---

# Day 4 - Django로 동적 웹 페이지 만들기

### 필수 과제 : 재고 관리 List 구현하기

- 다음 요청을 처리하는 웹 어플리케이션을 제작해주세요.
- `GET /` : Day 3에서 만든 자기소개 웹 페이지를 Response
- django를 바탕으로 재고 관리를 진행하는 Website를 만들고자 합니다.
    1. 재고관리를 하고자 하는 대상을 하나 정해주세요. (coffee, burger, )
    2. 이 대상에 맞는 Database Scheme를 model로 하여 `model.py` 에 작성합니다. 
    아래 예시에서는 coffee 재고 관리 리스템이라는 가정하에 서술합니다.
    3. 이를 바탕으로 다음 기능을 구현해주세요.
        - `GET /coffees` : 커피 목록을 *unordered list*로 보여주기

### 보너스 과제 : form을 이용해서 CUD구현하기

HTML의 `form` 을 이용해서 우리는 정보를 클라이언트단에서 서버단으로 전달할 수 있는데요, 이 정보를 바탕으로 다음 기능을 admin page가 아닌, `/coffees` 페이지에서 진행할 수 있도록 만들어봅시다.

다음 기능을 구현해주세요. 필수 과제 부분을 완성한 후에 구현하셔야합니다.

- `POST /coffees`  : 새로운 커피를 추가
- `PUT /coffees/<pk>` : 해당하는 커피의 정보를 변경
- `DELETE /coffees/<pk>` : Primary Key값에 해당하는 커피를 제거
- `POST`, `PUT`, `DELETE`를 진행하고 난 후에는 커피 목록을 *unordered list*로 보여주기
- `redirect()` 함수가 필요할 수 있습니다. 이는 인자에 해당하는 URL로 이동합니다. (그에 해당하는 views가 실행될 수도 있습니다.)
