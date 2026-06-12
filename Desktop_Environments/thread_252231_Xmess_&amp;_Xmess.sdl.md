---
title: "Xmess &amp; Xmess.sdl"
date: 2006-09-06
forum: Desktop Environments
---

### Post by lukew on 2006-09-06
Hi,

I am petty sure my ati graphics card is configured ok as I can do the fglrxinfo and glxgears and they report ok, however I could only get xmame.sdl to work and not xmame-x etc.

I have tried xmess but whenever I type xmess or put xmess into the path of gkxmame (i run gnome) my screen goes black and I have to log back in.

I am trying to install xmess.sdl but get the following issues.

Before I carry on down the dependancie problem, has anyone done what I am tring to do or can you give me advice on how to get xmess to work from the ubuntu repos?

Could any one give me any advice before I upgrade to libc6? (See below for dep error on instaallation of xmess.sdl and xmess-common. I downloaded them from [http://ftp.debian.org/debian/pool/non-free/x/xmame/](http://ftp.debian.org/debian/pool/non-free/x/xmame/).

Thanks for any advice you can give.

Luke



foomin@foobuntu:~$ sudo dpkg -i xmess-common_0.106-1_all.deb xmess-sdl_0.106-1_i 386.deb
(Reading database ... 148769 files and directories currently installed.)
Preparing to replace xmess-common 0.106-1 (using xmess-common_0.106-1_all.deb) . ..
Unpacking replacement xmess-common ...
Preparing to replace xmess-sdl 0.106-1 (using xmess-sdl_0.106-1_i386.deb) ...
Unpacking replacement xmess-sdl ...
dpkg: dependency problems prevent configuration of xmess-sdl:
 xmess-sdl depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
dpkg: error processing xmess-sdl (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xmess-common:
 xmess-common depends on xmess; however:
  Package xmess is not installed.
  Package xmess-sdl which provides xmess is not configured yet.
dpkg: error processing xmess-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xmess-sdl
 xmess-common
foomin@foobuntu:~$

---

### Post by lukew on 2006-09-07
Hi,

Should I have put this in the gaming section? 

Can anyone tell me if there are any plans to include xmess.sdl in the universe repos?

Thanks

Luke

---

