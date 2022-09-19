# Introduction
newsapi API 이용해 뉴스
* Component Language : JavaScript
* design : Photoshop

# Description
단일 페이지로 구성, 상단 헤더부분 카테고리 및 검색창으로 구성

# Creation Period
2022-07-21 ~ 07-24

# finished version
![1](https://user-images.githubusercontent.com/102776957/190958766-53d4a0b5-95e2-49fa-af0a-c3c3381e77c1.jpg)
![3](https://user-images.githubusercontent.com/102776957/190960059-f6572d99-4ca0-471d-8f32-6aba71f30cdf.jpg)

# Features
* fetchAPI 처리

# Development(important part)

* 검색창을 검색을했을때 검색내용이 객체로 저장 또는 클릭시 다시 가져올수 있습니다.
* JSON.parse(sessionStorage.getItem("recentSearchArray") SessionStorage에서 가져와 JSON을 통해 변환
* sessionStorage.setItem("recentSearchArray", JSON.stringify(recentSearchArray)) JSON을 이용해 String 형식으로 만들어 SessionStorage에 저장 
```C
let parseData = JSON.parse(sessionStorage.getItem("recentSearchArray"));
      if (parseData !== null) {
        recentSearchArray = [...new Set(parseData)];
      }

      const parseSessionStorage = function (parsingTxt) {
        sessionStorage.setItem("recentSearchArray", JSON.stringify(recentSearchArray));
        parseData = JSON.parse(sessionStorage.getItem("recentSearchArray"));
        recentSearchArray = [...new Set(parseData)];
        console.log(recentSearchArray);
        let tempHtml = "";
        recentSearchArray.forEach(function (item, idx) {
          if (parsingTxt === item) {
            tempHtml += `<li class="on" data-search="${item}">${item}</li>`;
          } else {
            tempHtml += `<li data-search="${item}">${item}</li>`;
          }
        });
        recentSearchList.innerHTML = tempHtml;
      };
```
![2](https://user-images.githubusercontent.com/102776957/190959687-75ce0b19-5de4-451c-9b07-61f04cbd66f2.jpg)


# Error
* newsAPI localhost에서는 모두 잘 작동했지만 Netlify에 사이트를 배포한 후 "리소스 로드 실패: 서버가 426(업그레이드 필요) 상태로 응답
* API를 https://gnews.io/ 로 전환해서 Netlify에 배포 성공 (GNews는 검색당 기사 10개, API 호출 100개로 제한)
