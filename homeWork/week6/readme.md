## 서버통신

![클라이언트](https://github.com/dudgns3tp/Sopt25th-Nodejs/blob/master/homeWork/week6/public/images/client.png?raw=true "통신 성공 이미지")

## API 문서


## 책장속 발견 조회

### BaseURL
25_SOPT_cyh.pem ubuntu@13.209.62.201:3000

| 메소드 | 경로                   | 짧은 설명   |
| ------ | ---------------------- | ----------- |
| post  | /home/book/ | 책장속 발견 조회 |

### 요청 헤더

```json
Content-Type: application/json
Authorization: token(선택)
```

### 요청 바디
{"category":"library"}

### 응답 바디

#### 책 조회 성공

```json
{
    "success": true,
    "message": "책장 속의 발견 성공",
    "data": [
        {
            "bookIdx": 1,
            "bookname": "리액트를 다루는 기술",
            "author": " 벨로퍼트",
            "bookcover": "http://image.kyobobook.co.kr/images/book/large/796/l9791160508796.jpg",
            "star": 0,
            "scrap": 0,
            "category": "library"
        },
        {
            "bookIdx": 2,
            "bookname": "생각하는 프로그래밍",
            "author": "존 벤틀리",
            "bookcover": "http://image.kyobobook.co.kr/images/book/large/997/l9788966260997.jpg",
            "star": 0,
            "scrap": 0,
            "category": "library"
        },
        {
            "bookIdx": 3,
            "bookname": "Clean Code",
            "author": "로버트 C 마틴",
            "bookcover": "http://image.kyobobook.co.kr/images/book/large/959/l9788966260959.jpg",
            "star": 0,
            "scrap": 0,
            "category": "library"
        },
        {
            "bookIdx": 4,
            "bookname": "일의 기쁨과 슬픔",
            "author": "장류진",
            "bookcover": "http://image.kyobobook.co.kr/images/book/large/036/l9788936438036.jpg",
            "star": 0,
            "scrap": 0,
            "category": "library"
        },
        {
            "bookIdx": 5,
            "bookname": "호텔 창문",
            "author": "판혜영 외",
            "bookcover": "http://image.kyobobook.co.kr/images/book/large/614/l9791189982614.jpg",
            "star": 0,
            "scrap": 0,
            "category": "library"
        }
    ]
}
```
#### "category": "library" 가 아닐때!

```json
{
    no category!
}
```
#### INTERNAL SERVER ERROR

```json
{
    "status": 500,
    "message": "서버 내부 에러",
    "data": null
}
```


## 취향이 비슷한 사람들의 책 조회

### BaseURL
25_SOPT_cyh.pem ubuntu@13.209.62.201:3000

| 메소드 | 경로                   | 짧은 설명   |
| ------ | ---------------------- | ----------- |
| GET    | /home/booklike/{username}| 취향이 비슷한 조회 |

### 요청 헤더

```json
Content-Type: application/json
```
### 요청 파라미터
/:username = lee
### 응답 바디

#### 취향이 비슷한 사람의 책 조회 성공

```json
{
    "status": 200,
    "message": "취향이 비슷한 사람의 책 조회 성공!",
    "response_taste":[
            {
                "bookname":"호준이형 안드존잘",
                "author" :"호준이형",
                "bookcover":"Server_Android/week6/public/images/11.jpg",
                "star":"1",
                "scrap":"TRUE"
            },
    
            {
                "bookname":"호준이형 안드존잘(오해의 소지가 있음)",
                "author" :"호준이형",
                "bookcover":"Server_Android/week6/public/images/maple.jpg",
                "star":"4.9",
                "scrap":"TRUE"
            }
        ]

}
```
####  조회 실패

```json
{
    "status": 404
}
```
#### INTERNAL SERVER ERROR

```json
{
    "status": 500,
    "message": "서버 내부 에러"
}
```
------



## 해시태그 조회
### BaseURL
25_SOPT_cyh.pem ubuntu@13.209.62.201:3000


| 메소드 | 경로                   | 짧은 설명   |
| ------ | ---------------------- | ----------- |
| POST    | /home/hastag/ | 해시태그 조회 |

### 요청 헤더

```json
Content-Type: application/json
```

###요청 바디
{"username":"Sopt"}

### 응답 바디

#### 책 조회 성공

```json
{
    "success": true,
    "message": "Sopt랜덤 해시태그!",
    "data": {
            "image": "https://pds.joins.com/news/component/htmlphoto_mmdata/201904/05/8c5dbe76-9a59-41dd-90a2-87e9433f2116.jpg", 
            "main_keyword": "등불/페스티벌", 
            "keywords": "#감성 #축제 #연말 페스티벌 #가족,애인,친구와 같이" 
        }
}

}
```

#### INTERNAL SERVER ERROR

```json
{
    "status": 500,
    "message": "서버 내부 오류",
}
```

## 나의 책 리스트 조회
### BaseURL
25_SOPT_cyh.pem ubuntu@13.209.62.201:3000


| 메소드 | 경로                   | 짧은 설명   |
| ------ | ---------------------- | ----------- |
| GET    | /mypage/mybook/{username} | 나의 책 리스트 조회 |

### 요청 헤더

```json
Content-Type: application/json
```

###요청 파라미터
{"username":"Sopt"}

### 응답 바디

#### 책 조회 성공

```json
{
    "success": true,
    "message": "Sopt 님이 가지고 있는 책!!",
    "data": [
        {
            "image": "Server_Android/week6/public/images/cat.JPG",
            "bookname": "수학",
            "author": "수학선생님"
        },
{
            "image": "Server_Android/week6/public/images/cat.JPG",
            "bookname": "영어",
            "author": "영어선생님"
        }
    ]
}

}
```

#### INTERNAL SERVER ERROR

```json
{
    "status": 500,
    "message": "error",
}
```
