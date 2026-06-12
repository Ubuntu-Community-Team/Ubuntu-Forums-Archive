---
title: "GNU Source Installer installion problems!"
date: 2006-06-11
forum: Desktop Environments
---

### Post by FPU4eva on 2006-06-11
ok got everything figured out to install but now when i try to install this after ./compile it runs threw and then does this:

checking for install-info... /usr/sbin/install-info
configure: error: An incompatible version of install-info has been found. If you have multiple install-info programs installed (for example on Debian systems), ensure that GNU install-info can be reached first.

you know how i could change this? thanks

---

### Post by FPU4eva on 2006-06-12
someone please help!

---

### Post by FPU4eva on 2006-06-13
plz make a suggestion

---

### Post by FPU4eva on 2006-06-13
bump

---

### Post by hayalci on 2006-07-28
I am trying to instal GNU Source Install, and I have run into the same problem. A probable fix is to compile GNU program which provides install-info, (probably the "info" program) in a seperate directory; Then give sourceinstall configure script the path to GNU install-info. I will probably try it soon.

[[ Name of the program makes it very hard to web search for solutions :-/ ]]

---

### Post by hayalci on 2006-07-31
Hi.

I filed a bug report, and my solution can be seen there. [[ don't forget to install textinfo gor "GNU install-info" ]] The cvs version will include it soon.

[https://savannah.gnu.org/bugs/index.php?func=detailitem&item_id=17235](https://savannah.gnu.org/bugs/index.php?func=detailitem&item_id=17235)

---

### Post by hayalci on 2006-08-06
At last I tested it, current cvs version of GNU sourceinstall works with ubuntu, (and probably debian) if you have the "texinfo" package installed. You can download GNU Source Installer from; [http://ftp.gnu.org/gnu/sourceinstall/](http://ftp.gnu.org/gnu/sourceinstall/)  [[ Note, the 2.2 version is released very recently, it probably includes the fix for debian/ubuntu systems, you may want to try it before the cvs release. ]]

---

