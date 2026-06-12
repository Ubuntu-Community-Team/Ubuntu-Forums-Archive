---
title: "Need Help With Installing Kiba-Dock"
date: 2009-05-05
forum: General Help
---

### Post by izizzle on 2009-05-05
Hey guys. I've been wanting to install Kiba-Dock on my Ubuntu 9.04 64-bit install, but the latest how-to I could find was for 8.10. Can anyone create a how-to for how to install Kiba-Dock on 9.04 64-bit, or at least link me to one?

Thanks!

---

### Post by izizzle on 2009-05-06
Bump...

---

### Post by izizzle on 2009-05-06
I really want to be able to use kiba dock! At this point, I'm not even sure it works with 9.04 64 bit! Can someone please lead me in the right direction?

---

### Post by izizzle on 2009-05-07
:sad:

---

### Post by xfearxnxloathing on 2009-05-16
> **izizzle said:**
> I really want to be able to use kiba dock! At this point, I'm not even sure it works with 9.04 64 bit! Can someone please lead me in the right direction?

sometimes you have to search hard to find an answer and sometimes you'll never get one, sorry dude..

ok, where as i cannot answer your question because i to am wondering the same thing, i just remembered another dock that i actually liked better.  it doesnt have the akamuru (sp) function but is a seriously stunning dock and i will be using, AWN (Avant Window Navigator)!!

i'm using 9.04, 64-bit.

to install AWN: [http://wiki.awn-project.org/Installation]("http://wiki.awn-project.org/Installation")
```
sudo apt-get install avant-window-navigator
```

thread that reminded me: [http://ubuntuforums.org/showthread.php?t=1152366&highlight=kiba-dock]("http://ubuntuforums.org/showthread.php?t=1152366&highlight=kiba-dock")

and..  if you really must have kiba-dock, try this: [http://ubuntuforums.org/showthread.php?t=972117&highlight=kiba-dock]("http://ubuntuforums.org/showthread.php?t=972117&highlight=kiba-dock")



^v^

---

### Post by rothalem on 2009-05-20
I have the same problem.

Ive been trying to install kiba dock on ubuntu 9.04 32 bit for a couple days, I had it installed, but without the akamaru working. The Kiba-dock seemed flimsy and flaky, and had no animations at all.

I followed this guide: [http://www.ubuntugeek.com/how-to-install-kiba-dock-in-ubuntu-710-gutsy-gibbon.html]("http://www.ubuntugeek.com/how-to-install-kiba-dock-in-ubuntu-710-gutsy-gibbon.html")

everything worked except ```
./autogen.sh
``` in the akamaru directory.
Please Note I tried all of these commands:
```
./autogen.sh --prefix=/usr --exec-prefix=/usr
```
```
./autogen.sh &#8211;prefix=/usr &#8211;exec-prefix=/usr
```
```
./autogen.sh
```

it gives me this output
```
checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
configure.in:51: error: AC_SUBST: `"$AKAMARU_REQUIRES"' is not a valid shell variable name
configure.in:51: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: autom4te failed with exit status: 1
autoreconf: aclocal failed with exit status: 1

```

I tried changing the variable name in configure.in but no matter what I change the name to it still gives me the same output (with the new variable name of course).
While typing this reply I just found this (reply#4): [http://ubuntuforums.org/showthread.php?t=972117&highlight=kiba-dock]("http://ubuntuforums.org/showthread.php?t=972117&highlight=kiba-dock") (includes a 64bit script, but I use 32bit)
I am going to try it out and will post my response.

EDIT: I read the bash file, and copy-pasted it in myself (so I could see what was going on), and the only difference was the line ./configure inside the akamaru directory, after the ```
./autogen.sh &#8211;prefix=/usr &#8211;exec-prefix=/usr
``` command.

That did not solve the problem, it responded with
```
bash: ./configure: No such file or directory
```

Hope it helps,
Knoppies

EDIT AGAIN: I found this [http://mintguides.blogspot.com/2008/08/howto-kiba-dock-with-physics.html]("http://mintguides.blogspot.com/2008/08/howto-kiba-dock-with-physics.html") (in the kiba-dock forums). I will try it out tomorrow, got an early morning start tomorrow, so Im going to call it a night.
This last attempt had the same response. Seems as though akamaru is not compilable on 9.04.

---

