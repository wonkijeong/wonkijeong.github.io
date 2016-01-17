---
layout: post
title: Jekyll로 블로그 만들기
---

---

## 1. 준비

Ruby와 Ruby Development Kit(MinGW) 을 설치한다.  
Ruby: <a href=http://rubyinstaller.org/downloads/>http://rubyinstaller.org/downloads/</a>

Ruby 설치 시 PATH를 자동으로 등록해 주는 것이 좋다. (설치 시 옵션)

- MinGW는 windows 상에서 GNU software들을 쓸 수 있게 포팅한 도구로서, RubyGem을 같이 설치함으로써 jekyll과 기타 markdown package들을 쉽게 설치하여 사용할 수 있다.
<br><br>

## 2. Jekyll 설치
Ruby Dev Kit을 설치한 폴더의 <strong>msys.bat</strong> 을 실행하면 아래와 같은 화면이 뜸.  
<img src="/public/images/run_devkit.png">

아래와 같이 입력하여 jekyll을 설치.  
<div class="highlight">
<span class="no">$ </span> <span class="nc">gem install jekyll </span>
</div>
입력하면 아래와 같이 설치된다.  
<img src="/public/images/install_jekyll.png">

- Jekyll은 <i>_config.yml</i> 등의 설정 파일들과 페이지의 여러 resource를 이용하여 정적인 페이지들을 간편히 만들어주는 도구이며, localhost에 자동으로 publishing하는 기능도 있어서 웹 서비스 환경을 조성하지 않고도 간단히 페이지들을 만들 수 있다. 
<br><br>

## 3. 내 블로그 만들기
내 블로그가 저장될 폴더를 생성한다.  
<div class="highlight">
<span class="no">$ </span> <span class="nc">mkdir blog </span> <br>
<span class="no">$ </span> <span class="nc">cd blog </span> <br>
<span class="no">$ </span> <span class="nc">jekyll serve </span> <br>
</div>

그럼 아래와 같이 메시지가 뜬다.  
<img src="/public/images/jekyll_serve.png">  

오류 없이 실행되었다면 브라우저로 접속하여 확인할 수 있다. (기본 port는 4000)  
<img src="/public/images/run_blog_1.png">  
현재 blog 폴더에 아무 것도 없기 때문에, 위와 같이 기본 화면만 뜨게 된다.  
<br><br>

## 4. 블로그에 theme 입히기
Jekyll theme 무료 제공 사이트  
<a href="http://jekyllthemes.org/">http://jekyllthemes.org/</a>  

여기에 여러 theme들이 제공되며, demo로 살펴보고 원하는 것을 다운받자.  
압축을 풀고 아까 생성한 blog 폴더<font color="blue">([RubyDevKit]/home/[Username]/blog)</font>에 theme 파일들을 복사한다.  
이 블로그는 Aigars Dzerviniks님이 만든 __brume__이라는 이름의 테마를 사용하였다.  
<a href="http://jekyllthemes.org/themes/brume/">http://jekyllthemes.org/themes/brume/</a>  

그런데 파일을 복사하고 jekyll serve를 실행하면 아래와 같은 에러가 발생한다.  
<img src="/public/images/jekyll_error_1.png">  

brume 테마를 실행하기 위해서는 redcarpet이라는 패키지가 필요한데, 설치되어 있지 않아서 발생한 에러이므로 redcarpet을 설치한다.  
(다른 테마에서는 redcarpet대신 또다른 package가 필요할 수도 있다.)  

<div class="highlight">
<span class="no">$ </span> <span class="nc">gem install redcarpet </span><br>  
<span class="no">$ </span> <span class="nc">jekyll serve </span><br>
</div>

실행하고 브라우저로 접속하면 테마가 적용된다.  
<img src="/public/images/run_blog_2.png">  

## 5. 블로그 설정 및 포스팅하기
받은 테마별로 설정방식은 조금씩 다를 수 있으므로 jekyllthemes 사이트에서 자신이 받은 테마의 usage 항목을 참고한다.  
기본적으로 __site__ 폴더에는 jekyll을 통해 생성된 결과물이 저장되고,
__posts__ 폴더에는 블로그 포스팅이 개별로 저장된다.  
(게시 날짜를 파일명에 써 줌으로써 자동으로 게시물이 정렬된다)

마크다운을 사용하는 포스트를 편집하기 위한 툴로서,
__visual studio code__를 추천한다. 아래 링크에서 다운  
<a href="https://code.visualstudio.com/">https://code.visualstudio.com/</a>  
<br><br>

## 6. Disqus를 이용한 댓글 기능 추가
Disqus에서 댓글 기능을 불러와 내 블로그에 embedding 시킬 수 있다.  
<a href="http://disqus.com">http://disqus.com</a>  

회원 가입을 하고 로그인을 한 뒤, 오른쪽 위의 설정 버튼을 눌러 __'Add Disqus to Site'__를 클릭한다.  
<img src="/public/images/disqus_1.png">  

사이트 이름과 URL, 카테고리를 입력하고 'Finish registration' 버튼을 클릭한다.  
<img src="/public/images/disqus_2.png">  

댓글을 위한 HTML 태그를 입력하기 위한 플랫폼을 선택해야 하는데, 우리 블로그는 어떤 사이트에 종속된 것이 아니므로 __Universal Code__를 선택한다.  
<img src="/public/images/disqus_3.png">  

코드가 나오면 이를 복사하여 적절한 위치에 삽입한다.  
<img src="/public/images/disqus_4.png">  

__brume__ 테마의 경우 __layout__ 폴더의 __post.html__ 파일의 하단에 위 코드를 삽입하게 되면
모든 포스트 밑에 댓글 기능이 추가된다.
<br><br>

## 7. GitHub에 블로그 등록하기
완성된 블로그를 GitHub에 등록할 수 있다.  
먼저 github에 접속하여 __+ New repository__ 버튼을 눌러 새로운 repository를 생성한다.  
<img src="/public/images/github_1.png">  

Repository의 이름은 __[UserID].github.io__로 설정해야 블로그 개설이 가능하다.   
<img src="/public/images/github_2.png">  

생성하면 아래와 같이 빈 repository가 생성된다.  
<img src="/public/images/github_3.png">  

GitHub Desktop 툴을 다운받아 설치한다.  
<a href="https://desktop.github.com/">https://desktop.github.com/</a>  

Git CMD를 실행하고, blog 폴더로 이동한다.

<div class="highlight">
<span class="no">C:\> </span> <span class="nc">cd c:\RubyDevKit\home\Wonki\blog </span><br>
<span class="no">C:\RubyDevKit\home\Wonki\blog> </span>
</div>

아래 명령어들을 차례로 입력하여 Git repository에 블로그를 commit한다.

<div class="highlight">
<span class="nc">git init </span><br>
<span class="nc">git remote add origin [저장소URL] </span><br>
<span class="nc">git add . </span><br>
<span class="nc">git commit -m "Initialize blog" </span><br>
<span class="nc">git push origin master </span><br>
</div>

브라우저에서 아까 생성한 __[GitHub ID].github.io__로 접속하면 블로그가 게시되었음을 확인할 수 있다.

---