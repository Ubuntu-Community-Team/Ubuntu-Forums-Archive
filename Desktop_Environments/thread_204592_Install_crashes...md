---
title: "Install crashes.."
date: 2006-06-27
forum: Desktop Environments
---

### Post by macarrao37 on 2006-06-27
AMD64 3.0 / 1gb ram / X700 video / A8n-SLi

I have changed xorg.conf (ati=vesa) and the livecd works fine.. but when i try to install, it always crashes in 68%... whats happening??

---

### Post by taurus on 2006-06-27
Did you check the CD, check media option, before you boot from it?  Also, how fast did you burn the ISO image anyway?  Burning it at 4x is a good speed because high speed burning can sometimes choke the installer...

---

### Post by jvictor on 2006-06-27
I used to have this issue of install failing during the copying of files @ 23 % (jfsutils.deb) on 5.10 , it turned out to be a prob with the DVD+RW , when it freezes can u do the following ?

Go to the text mode console and type 

dmesg 

and see if theres some message that says drive not ready or something of that nature ?

Apparently I reported a bug and it got resolved with Dapper.

---

### Post by macarrao37 on 2006-06-28
Thank you.. i´ll try it again and reply tomorow...

---

