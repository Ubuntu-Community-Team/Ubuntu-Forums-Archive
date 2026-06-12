---
title: "Screen capture"
date: 2006-07-18
forum: Desktop Environments
---

### Post by clapton on 2006-07-18
As anyone knows a program to screen capture on ubuntu?
Istanbul doesn't work well on 6.06.
Something similar to camstudio for windows.
Camstudio is open source know, but code is only compatible for windows, I take a look, and have MFC.

---

### Post by reclusivemonkey on 2006-07-18
> **clapton said:**
> As anyone knows a program to screen capture on ubuntu?
Istanbul doesn't work well on 6.06.
Something similar to camstudio for windows.
Camstudio is open source know, but code is only compatible for windows, I take a look, and have MFC.

[http://www.ubuntuforums.org/showthread.php?t=215586&highlight=istanbul](http://www.ubuntuforums.org/showthread.php?t=215586&highlight=istanbul)

---

### Post by m0biu5 on 2006-07-18
I think there was something like vnc2swf.. check it out..

---

### Post by clapton on 2006-07-19
THx for the tips.

---

### Post by OneSeventeen on 2006-07-24
I too have had no luck with istanbul, but I did find an app called [xvidcap](http://xvidcap.sourceforge.net/) which seems to do a nice job once you get the hang of it.

It even lets you choose a window to record in, and you can record audio and all that good stuff too.

The .deb on sourceforge worked fine for me, but once again, it took a while to figure out, and it didn't install a manual or anything, which makes it even more difficult.  =P

---

### Post by reclusivemonkey on 2006-07-25
> **OneSeventeen said:**
> 
The .deb on sourceforge worked fine for me, but once again, it took a while to figure out, and it didn't install a manual or anything, which makes it even more difficult.  =P

I take it you didn't look at the instructional videos on the site then which told you to look at the man page first ;-)

---

### Post by clapton on 2006-07-26
```
xvidcap: error while loading shared libraries: libpng.so.2: cannot open shared object file: No such file or directory
```

it was installed with repository 

deb [http://www.jarre-de-the.net/computing/debian/](http://www.jarre-de-the.net/computing/debian/) stable main

---

### Post by reclusivemonkey on 2006-07-26
> **clapton said:**
> 
it was installed with repository 

deb [http://www.jarre-de-the.net/computing/debian/](http://www.jarre-de-the.net/computing/debian/) stable main

Which is for Woody...

> 
What you'll find here are debian packages (*.deb files) backported to the stable (woody) release.
I started compiling such packages after running into troubles when individual packages from the
unstable release pulled unstable libc releases along with them.

Try the deb from Sourceforge which OneSeventeen said worked for him.

---

### Post by tropcky on 2007-08-26
or u can try thes 
open the terminal and type
sudo apt-get install recordmydesktop                         ( thats  2 install it )
then when u wanna record just type 
recordmydesktop
and it will start captureing 
bvut i dont how 2 make it stop and save it lol will i will be happy when some body help me in that

---

### Post by patambrosio on 2007-09-01
> **tropcky said:**
> or u can try thes 
open the terminal and type
sudo apt-get install recordmydesktop                         ( thats  2 install it )
then when u wanna record just type 
recordmydesktop
and it will start captureing 
bvut i dont how 2 make it stop and save it lol will i will be happy when some body help me in that

do Ctrl+c to make it stop.
to easethe use of record my desktop, there's a GUI for it just:

***sudo apt-get install gtk-recordmydesktop***

just click record for record, and when you want to stop, click on the square box in your tray and it will start encoding.

[a full guide to screen capture in ubuntu is here.]("http://ubuntuchocolate.wordpress.com/2007/09/01/howto-screen-capture-in-ubuntu-feisty-fawn/")

---

