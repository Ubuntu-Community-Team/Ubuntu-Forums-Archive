---
title: "Silverkrok"
date: 2010-08-22
forum: Gaming &amp; Leisure
---

### Post by Sockerdrickan on 2010-08-22
[B][IMG]http://img835.imageshack.us/img835/153/silverkrok.png[/IMG]
[/B]Silverkrok is a cross-platform fishing game. The enviroment is adjusted to actual time.

I've actually been working on this since spring 2010, but it has been a slow ride because of school and such.

Source is available, under the "**Do What The **** You Want To Public License**" version 2.

The alpha release is a little rough in gameplay and it has no sound, but a beta is planned.

**Note:**
Silverkrok requires OpenGL 3.3 support, something that is  comparable to AMD HD 4350. It works on both Nvidia and AMD cards. Mesa  does not support OpenGL 3.3 yet so you need a card and official driver  from either Nvidia or AMD.

**Downloads at [www.amyto.com]("http://www.amyto.com/") Please pass this on to your friends. ;)**
[]("http://www.amyto.com")
See README.txt for controls

---

### Post by portets on 2010-08-22
looks interesting. very casual looking.

it reminds me of reel fishing. hoping to try it out

---

### Post by Woojoo//.deb on 2010-08-22
well thats realy an impressive work you did there!

i like the artwork, just look great ^^ cant wait to play it.

---

### Post by Sockerdrickan on 2010-08-23
The alpha version has been released, check it out at the website [http://www.amyto.com](http://www.amyto.com)

No Linux builds yet, however source code is available along with the win32 release. ;)

It's a bit rough in gameplay but it's a start. I'm gonna start development on the beta version shortly which will feature a long list of improvements.

---

### Post by portets on 2010-08-24
well, i got glm compiled. but i absolutely cannot figure out how to install it.
**edit:** figured it out. couldn't find instructions anywhere, but eventually figured it out.

sdl 1.3 shouldn't be too hard to make and install. does anyone know if sdl 1.3 can be installed beside 1.2?

after that i can test it out and post a how-to on getting Silverkrok running.

---

### Post by portets on 2010-08-24
when compiling silvercrock i get many errors. i was able to get rid of some by changing all of the gl3 include's to gl in the source files(it couldn't find gl3.h but finds gl.h(using nvidia binary driver)). now i get:

```
g++ -std=c++0x -O3 -L/usr/local/lib fish.cpp
g++ -std=c++0x -O3 -L/usr/local/lib framebuffer.cpp
g++ -std=c++0x -O3 -L/usr/local/lib level.cpp
framebuffer.cpp: In destructor ‘Framebuffer::~Framebuffer()’:
framebuffer.cpp:10: error: ‘glDeleteFramebuffers’ was not declared in this scope
framebuffer.cpp: In member function ‘void Framebuffer::init(int, int)’:
framebuffer.cpp:14: error: ‘glGenFramebuffers’ was not declared in this scope
framebuffer.cpp:17: error: ‘glBindFramebuffer’ was not declared in this scope
framebuffer.cpp:21: error: ‘nullptr’ was not declared in this scope
framebuffer.cpp:22: error: ‘glFramebufferTexture2D’ was not declared in this scope
framebuffer.cpp: In member function ‘void Framebuffer::bind() const’:
framebuffer.cpp:26: error: ‘glBindFramebuffer’ was not declared in this scope
framebuffer.cpp: In static member function ‘static void Framebuffer::bindDefault()’:
framebuffer.cpp:34: error: ‘glBindFramebuffer’ was not declared in this scope
make: *** [framebuffer.o] Error 1
make: *** Waiting for unfinished jobs....
fish.cpp: In member function ‘virtual void Perch::update(Fish*&, int, int)’:
fish.cpp:183: error: ‘nullptr’ was not declared in this scope
make: *** [fish.o] Error 1
level.cpp: In member function ‘unsigned int Level::dateInt(const std::string&)’:
level.cpp:20: error: ‘nullptr’ was not declared in this scope
level.cpp: In member function ‘void Level::step(int, int, const glm::core::type::mat4&, int)’:
level.cpp:78: error: ‘nullptr’ was not declared in this scope
level.cpp:151: error: expected primary-expression before ‘[’ token
level.cpp:151: error: expected primary-expression before ‘]’ token
level.cpp:151: error: expected primary-expression before ‘&’ token
level.cpp:151: error: ‘value’ was not declared in this scope
level.cpp:151: error: expected primary-expression before ‘const’
level.cpp:151: error: expected primary-expression before ‘const’
level.cpp:151: error: unable to deduce ‘const auto’ from ‘<expression error>’
level.cpp:151: error: expected ‘,’ or ‘;’ before ‘{’ token
level.cpp:68: warning: unused variable ‘seconds’
level.cpp:151: warning: unused variable ‘timelapse’
level.cpp:228: error: expected ‘}’ at end of input
make: *** [level.o] Error 1
```

---

### Post by Sockerdrickan on 2010-08-24
> **portets said:**
> sdl 1.3 shouldn't be too hard to make and install. does anyone know if sdl 1.3 can be installed beside 1.2?

When I **make install** SDL 1.3 that I compile from the trunk found at [http://www.libsdl.org/hg.php](http://www.libsdl.org/hg.php) I get the files placed in /usr/local/* and not /usr/* So the answer to your question is yes. The makefile for Silverkrok already reflects this /usr/local/* setting. Note that you also need GCC 4.6 from about a month ago at least [ftp://gcc.gnu.org/pub/gcc/snapshots/](ftp://gcc.gnu.org/pub/gcc/snapshots/)

I'm going to upload official Linux x86 and Linux x86_64 builds to the website today for people who don't want to get down into my crazy bleeding edge dependencies.

If anyone has problem with the **graphics** then please step forward. This release focused mainly on graphics.

---

### Post by Sockerdrickan on 2010-08-24
> **portets said:**
> when compiling silvercrock i get many errors. i was able to get rid of some by changing all of the gl3 include's to gl in the source files(it couldn't find gl3.h but finds gl.h(using nvidia binary driver)).

[http://www.opengl.org/registry/api/gl3.h]("http://www.opengl.org/registry/api/gl3.h")
Save to /usr/include/GL3/gl3.h

Looks like you also need a recent version of GCC 4.6, your make output says the C++0x keyword "nullptr" is not declared.

---

### Post by portets on 2010-08-24
oh, okay. looks like gcc was my problem. thanks for the help.

---

### Post by portets on 2010-08-26
hey, you should set up an svn for this.

---

### Post by Sockerdrickan on 2010-08-30
> **portets said:**
> hey, you should set up an svn for this.

I don't have "open development" in mind right now.

A beta version will probably be released later **this** year.

If anyone wants to play with the source from any of the releases, they can grab it from the website as they wish. :D

---

