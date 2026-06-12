---
title: "Ubuntu logs out after a few seconds of opening XBMC"
date: 2014-03-08
forum: Desktop Environments
---

### Post by sirclescratch on 2014-03-08
Since upgrading from 13.04 to 13.10 32bit, after a few seconds of opening XBMC, it freezes briefly and then sends me back to the OS logon screen.  If I log back in without rebooting, it will do the same thing no matter what I'm doing, regardless of opening XBMC.  Obviously I've tried uninstalling/re-installing umpteen times.  I found similar articles about being logged off but none of them had to do with XBMC.  I tried their resolution steps anyway, but without success.  Any help would be greatly appreciated.

---

### Post by sirclescratch on 2014-03-10
Come on Ubuntu community!  118 views and no response(s)?!?  I really don't want to re-install the OS.

---

### Post by frank18 on 2014-03-12
> **sirclescratch said:**
> Since upgrading from 13.04 to 13.10 32bit, after a few seconds of opening XBMC, it freezes briefly and then sends me back to the OS logon screen.  If I log back in without rebooting, it will do the same thing no matter what I'm doing, regardless of opening XBMC.  Obviously I've tried uninstalling/re-installing umpteen times.  I found similar articles about being logged off but none of them had to do with XBMC.  I tried their resolution steps anyway, but without success.  Any help would be greatly appreciated.

I would upgrade to 14.04 the other day i had 13.10 installed then i installed XBMC and the mouse did no move right in XBMC so i couldn't use it,i upgraded to 14.04 and mouse started work right.

---

### Post by sammiev on 2014-03-12
14.04 will not be released until April and may break easily.

@frank18, Interesting fix for your problem. :)

---

### Post by 3rdalbum on 2014-03-13
It's not so much that it "logs you off" or "sends you back to the login screen". What's actually happening is that the X server has crashed, which brings down all your graphical programs. Then X is automatically restarted, and the first thing X does is display the login screen.

What's your graphics card and what graphics driver are you using?

---

### Post by sirclescratch on 2014-03-13
I've actually desided to just do a clean install of 13.10 since I was starting to have other issues as well.  So far, good.

---

### Post by frank18 on 2014-03-14
> **sammiev said:**
> 14.04 will not be released until April and may break easily.

@frank18, Interesting fix for your problem. :)


Well i updated from 13.10 to 14.04 and so far my system has been perfect,so till it brakes i'm happy and it fixed all issues i had with 13.10. and it's only a few days away from Lts.

---

### Post by frank18 on 2014-03-14
> **sirclescratch said:**
> I've actually desided to just do a clean install of 13.10 since I was starting to have other issues as well.  So far, good.


if you have problems with xbmc with 13.10 just upgrade to 14.10 just as i did, do this.



[http://itsfoss.com/upgrade-ubuntu-1404-beta-1310/](http://itsfoss.com/upgrade-ubuntu-1404-beta-1310/)

---

