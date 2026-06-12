---
title: "SDLMAME 1.2.3u1"
date: 2008-02-19
forum: Gaming &amp; Leisure
---

### Post by RemmyLee on 2008-02-19
[Came out 6 days ago]("http://rbelmont.mameworld.info/?page_id=163"). Pay no attention to the date on the page. It's the day the site was created, not the last update. :)


> Build instructions
==================

Linux: make sure you have SDL and it's development packages installed via 
apt-get, yum, emerge, or whatever your distro of choice uses. On Fedora 4 or 
later, 'yum install SDL SDL-devel' will get you going assuming you already 
have GCC. If you already can compile XMAME/XMESS with the SDL target you're 
good to go. Just edit the makefile, change the options as necessary, and 
type 'make'.

For native 64-bit x86-64, you should build with PTR64=1 (or uncomment it 
in the makefile).

For Linux/PPC (including the PlayStation 3) you should build with 
BIGENDIAN=1 (or uncomment it in the makefile).

NOTE: you will now need OpenGL headers and libraries as well.  If you're 
running either ATI or NVIDIA's binary-only drivers you've definitely got them.
Otherwise you may need to install the "MesaGL" and "MesaGL-devel" packages.  

NOTE: if you do not have hardware accelerated OpenGL you should not try to 
enable it, it'll just go horribly slow.

---

### Post by disturbedite on 2008-02-19
its version 0.123, not 1.2.3.

but you know sdlmame is in the official ubuntu repo right?

---

### Post by RemmyLee on 2008-02-19
Oops. Fixed the title. All I see in the official repos is xmame sdl.

---

### Post by disturbedite on 2008-02-20
you're probably on gutsy right?  i'm on hardy.  it may be that sdlmame has not been uploaded/backported to gutsy yet...
ah yes, i checked, they're not in gutsy yet or any other version for that matter.
you can also get the same packages of sdlmame here:
[http://wallyweek.altervista.org/](http://wallyweek.altervista.org/)

---

