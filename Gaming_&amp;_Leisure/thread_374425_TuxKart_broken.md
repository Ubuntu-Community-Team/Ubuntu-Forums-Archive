---
title: "TuxKart broken"
date: 2007-03-02
forum: Gaming &amp; Leisure
---

### Post by Weaseal on 2007-03-02
I can load tuxkart, but when I try to start the game, I get this error:
$ tuxkart
Data files will be fetched from: '/usr/share/games/tuxkart'
PW: This is an *INDIRECT* rendering context.PW: That may be bad for performance.Data files will be fetched from: '.'


   TUXEDO T. PENGUIN stars in TUXKART!
               by Steve and Oliver Baker
                 <sjbaker1@airmail.net>
                  [http://tuxkart.sourceforge.net](http://tuxkart.sourceforge.net)


Kart 0 == 'tuxkart.ac'
Kart 1 == 'geekokart.ac'
Kart 2 == 'bsodkart.ac'
Kart 3 == 'gownkart.ac'
READY TO RACE!!
tuxkart: indirect_vertex_array.c:1359: __indirect_glTexCoordPointer: Assertion `a != ((void *)0)'


This is my uname output: Linux ubuntu-1 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux

---

### Post by hikaricore on 2007-03-02
I know nothing of the error but just looking it over I'm going to guess it's a video driver issue?  Check the output of:

```
glxinfo | grep rendering
```

If you have the correct video drivers installed, it will return a **direct rendering : Yes**

---

### Post by Weaseal on 2007-03-07
$ glxinfo | grep rendering
direct rendering: No

I'm more of a BSD user, so this error message doesn't tell me much beside that it's not properly managing my video card...
I know this system has a card, although I don't know exactly which.  What commands can I use to find out: 1) what card I have, and 2) what's misconfigured?
I'd switch to Windows to check but my internet connection goes away (for the rest of the day) in just a few minutes.

---

### Post by Weaseal on 2007-03-13
The solution to this problem was installing the nvidia driver.  Seems simple enough to a newbie...why couldn't someone have saved me the headache??

---

### Post by hikaricore on 2007-03-14
I tried but you never responded while I was able to check the forums (which wasn't that long on that particular day).  So a week went by and I forgot.  Had you mentioned your video card in your first message I could have told you to install the drivers.

---

