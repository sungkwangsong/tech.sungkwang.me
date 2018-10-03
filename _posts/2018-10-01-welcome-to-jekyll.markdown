---
layout: entry
title:  다시 블로그, 다시 GitHub Pages 로
date:   2018-10-01
categories: story 
author: 송성광
author-email: tech@sungkwang.me
description: blog.saltfactory.net 으로 운영하던 기술블로그를 tech.sungkwang.me 로 이전하여 기술블로그를 새롭게 시작하게 되었습니다.
publish: true
permalink: /open-blog-on-github
---

연구소에서 약 2년간 긴 프로젝트를 진행하는동안 블로그를 운영할 시간이 없었다. 쌓여가는 정보와 경험했던 지식들은 코드나 메모장에 고스란히 녹아있지만 그것을 온라인으로 옮겨서 작성할 시간적 여유가 전혀 없었다. 프로젝트가 끝나는 순간부터 나는 다시 블로그를 운영해야겠다는 생각을 계속 하고 있었다.

기존에 운영하던 [블로그](https://blog.saltfactory.net/)는 Ghost 오픈 소스를 직접 설치해서 운영하였다. 하지만 운영하던 Ghost 오픈소스가 버전 업그레이드 되면서 기존과 다른 입력기를 사용해 한글 입력이 되지 않는 문제가 발생했다. [커뮤니티를 통해서 직접 질문도 남겼지만](https://forum.ghost.org/t/korean-input-problem-in-ios-mobile-browsers/1797) 돌아오는 대답은 기약없이 기다리는 것 밖에 없었다. 난 Ghost에 대한 큰 실망을 가지고 다른 블로그 플랫폼을 조사했지만 내가 원하는 것을 만족하는 것은 없었다. 난 다음과 같은 기능을 제공해주는 서비스를 찾고 있었다.

- Markdown  지원하기
- 자체 광고를 포함하지 않기
- 관련 글이라며 다른 사람이 작성한 글들이 내 목록이나 글타래로 노출되지 않기
- 개인 도메인 연결 지원하기
- 백업 지원하기
- 테마는 많지 않아도 되지만 컨텐츠를 집중할 수 있도록 자체 서비스들이 섞이지 않기
- 한글입력 을 완벽하게 지원하기

가장 마지막까지 갈등하고 고민했던 서비스는 [Medium](https://medium.com/) 이였다. 언젠가부터 국내 개발자들도 대거 [GitHub Pages](https://pages.github.com/) 에서 Medium 으로 이전을 많이하고 있었기 때문에 나도 대세에 따라 Medium 으로 가려고 했으나 이 서비스의 가장 큰 문제점은 바로 PC로 방문하게 되면 한글 font 가 모두 **명조체**로 출력되는데 정말 가독성이 떨어지다 못해 너무 아름답지 못하게 보이기 때문이다. 모바일 디바이스에서는 한글도 깔끔하게 나오는데 유독 PC 화면에서는 정말 보기 어렵기 짝이 없다. 또 하나의 문제점은 Medium 에서 더이상 **도메인** 서비스를 하지 않는다는 것이다. 이것은 꽤 큰 이슈를 야기 시키는데 대부분 개발자들은 내가 심각하게 생각하는 이슈를 별로 중요하게 여기지 않는것 같다. 그 문제는 바로 **URI**의 문제이다. 

예를 들어서 다음과 같이 개인 도메인 기반으로 서비스를 하고 있다가 다른 블로그 서비스나 설치형 블로그로 이관할 때, 기존의 링크 주소를 그대로 컨텐츠를 이전할 수 있다. 

```
https://tech.sungkwang.me/2018/10/01/hello-world.html
```

다시 말해서, 누군가 자신의 인터넷 문서에 내 글을 참고하고 있거나 링크를 포함하고 있다면 이 주소가 아닌 다른 주소가 될 경우 내 URI를 참조하고 있는 모든 문서를 죽은 링크를 가지게 되어버린다. 

```
https://medium.com/@sungkwangsong/hello-world.html
```

이였던 글을 내가 다른 블로그 서비스로 이전하게 되면 이 도메인은 더이상 없는 도메인이 되어 버릴것이 참조하고 있는 링크들은 모두 잘못된 링크로 되어 버린다.

이런 이유로 개인적으로 custom domain 서비스를 지원하지 않는 블로그는 아예 후보로 두지 않는다. 하지만 이 두 문제를 제외한 Medium의 기능은 정말 편리하다. 

결국 난 다시 가장 개발자스런 **GitHub Pages**를 사용해서 블로그를 운영하기로 마음먹었다. 예전과 달리 지금은 Node.js, Go, Python 등 여러가지 언어로 만들어진 static website generator가 존재하지만 가장 익숙한 [Jekyll](https://jekyllrb.com/)을 사용하기로 결심했다. 일단 [GitHub 에서 Jekyll을 공식적으로 지원](https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/)해서 처음 환경설정만 끝내고 저장소에 push 하고 난 뒤 단순히 글만 작성하면 GitHub 에서 자동으로 빌드해서 static website를 만들어주기 때문에 모바일에서도 작성가능하고 편리한 기능들이 많기 때문이다. 

보통은 연구노트나 일기를 [Day One](https://dayoneapp.com/)을 사용해서 Markdown으로 작성하고 있기 때문에 특히 다른 Markdown 입력기를 사용하고 있지 않다. 

**GitHub** 과 **Jekyll** 을 사용해서 블로그를 운영하면서 가장 큰 고민중에 하나는 디자인을 어떻게 해야하는가? 이다. 이 부분은 개인적으로 GitHub 으로 운영중인 블로그중에 가장 가독성이 좋고 미려한 디자인을 가진 사이트의 소스를 Fork 해서 필요한 내용은 수정해서 사용하는 것이 좋다고 생각했다. 이금 이 사이트는 [Spoqa 기술블로그](https://spoqa.github.io) 를 folk 해서 코드를 수정해서 운영하고 있다. 개인적으로 WebFont를 사용하는 것을 선호하지 않지만 우선은 [Spoqa Sans](https://spoqa.github.io/spoqa-han-sans/ko-KR/)로 만들어진 이 테마는 그대로 두기 위해서 WebFont를 사용해보기로 했다. 하지만 운영중에 깜빡거림이나 성능 이슈가 발생하면 언제든지 WebFont를 제거하고 템플릿을 리펙토링할 예정이다. 블로그를 spoqa 기술블로그 레이아웃을 사용해서 운영하면서 몇가지 수정한 내용은 PR을 보내거 이 블로그를 통해 공유할 예정이다.

그리고 가장 중요한 공지사항이 있다.

## 공지사항

> blog.saltactory.net 이 tech.sungkwang.me 로 개편과 함께 블로그 주소가 변경되었습니다.

지금까지 연구활동을 하면서 실명을 사용하지 않고 닉네임(alias)를 사용해왔는데 이젠 부모님께서 기도로 지어주신 본명을 사용해서 연구활동을 계속하기로 결심했다. 결심하게된 이유는 여러가지가 있지만 가장 나다운 삶을 살아가고 싶은 이유도 있다. 나의 아이텐티티를 가지고 말이다. 그래서 한달에 커피한잔 안먹고 [sungkwang.me](https://sungkwang.me/) 도메인을 구입했다. 그리고 기술블로그와 개인블로그를 따로 운영하기 위해서 기술블로그는 [tech.sungkwang.me](https://tech.sungkwang.me/)로 운영하기로 결심했다. 

앞으로 좋은 내용을 가지고 이 블로그를 채워할 예정이다. 

> 여러분의 응원과 관심이 연구활동에 큰 도움이 됩니다.
