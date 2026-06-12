---
title: "UBUNTU 7.04 ATI FireGL and CPIZ.. A real PIA"
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by ricardoec on 2007-08-16
I have to post this, which I suppose it has been posted ONE THOUTHAND times but I am frustrated after several weeks of trying to get this combination to work.

Here is the Issue:

I have a HP nw8440 wth 2GB of RAM.. and a famous ATI FireGL ( x1600) video chip and, of course, an au-to-date UBUNTU 7.04 (with the 2.6.20 lowlatency kernel though - UbuntuStudio)

the end: I CANNOT GET COMPIZ to work.

After fighting with all Howtos on ATI, even fighting to get rid of the Mesa drivers, recompilig the Kernel with latest ATI drivers..the Treviño repositories... the installation guides, Googlein one million times.... I am still onn the loose.

Now, there is a psot where it reads that my x1600 chip is not supported !!!!!!... is this true???.... how can it be if this is a very powerfull and new HP workstation with a Video that just makes Vista dance. !!

here is my chip:...here is my problem... please help

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6474 (8.38.6)


Cheers

---

### Post by Hotaru on 2007-08-16
I have X1650 chip and have problems as well. I don't event get as far as to installing Compiz Fusion. I've installed fglrx drivers, they work, I've direct rendering, but everytime I try to install and setup XGL it's no use - my XGL session is so slow, that I can't do anything on it - the wallpaper takes ages to load, minimise and unminimise is slow as hell, even when typing in a search query in firefox a new letter appears once every 3 seconds! :(

Maybe it's something with the XGL itself? I was recently using this How-To: [ How To : Compiz Fusion for ATI cards + Xgl in Feisty]("http://ubuntuforums.org/showthread.php?t=488385&highlight=ati+xgl+install"), and it still doesn't work.

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: ATI
client glx version string: 1.3
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6334 (8.34.8)
```

---

### Post by ricardoec on 2007-08-16
Ivé never heard of that chip, but still, the same issues... no support for ATI.

I have another comp whicha a plain vanilla clone with an Integrated Intel chip, and the i810 drivers work like a charm... I just dont understand this whole mess to get a decent driver working.

Now, you may try to upgrade your driver, it shows you are 8.34.8. 

Iam tuck... again, pls the Ubuntu or AMD people, please get into this thread,

:confused:

---

### Post by Hotaru on 2007-08-16
> **ricardoec said:**
> Now, you may try to upgrade your driver, it shows you are 8.34.8. 

I've tried.

And failed.

And want to hear the funny part? Both in Ubuntu AND Windows. You can see my problem in the attachement. It's XP's Log-in screen, but it looks the same in Ubuntu.
The last Windows driver that handles my card correctly is 7.4 (from April). The fglrx driver I have is the most recent that handles this card correctly. It's something they screwed up within the driver and don't know how to make it work again. I've been exchanging mails with ATI support team for two months now and their only advice is "stick to the driver that works. And hope".

Thinking about it... maybe it's because of my old fglrx driver that XGL works like crap...?


EDIT:
Ok, I know why XGL works so sluggish. I get this error message:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
```

The solution for this is to install the most recent driver, which - ironically - doesn't work for me! Well, that would be it for me and 3D desktop... -_-

---

