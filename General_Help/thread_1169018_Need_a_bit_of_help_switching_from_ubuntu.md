---
title: "Need a bit of help switching from ubuntu"
date: 2009-05-24
forum: General Help
---

### Post by krisluv_18 on 2009-05-24
Hi guys,
I have an interesting problem here. My computer (that I bought off a friend at a VERY reasonable price) has a LiteOn DVDRW drive, but it is malfunctioning & will not read ANY CDs. Upon discovering this, I used "instlux" to do an easy 6.06 (Dapper Drake) install & upgrade to 8.04. I then wanted to use ubuntulite (aka U-Lite) and used the "wget http" method to install. Now it seems that u-lite is the default desktop, but all the ubuntu 8.04 files and settings are still there, almost like I installed u-lite INSIDE of ubuntu 8.04. But I'd like to completely uninstall ubuntu 8.04 and keep U-Lite. 

Any and all suggestions appreciated and welcome.

P.S. I'm dual-booting with Windows XP, which is why I didn't just wipe the whole partition clean

---

### Post by jflaker on 2009-05-24
> **krisluv_18 said:**
> ....LiteOn DVDRW drive, but it is malfunctioning & will not read ANY CDs.....

UNetBootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
UNetbootin allows you to create bootable Live USB drives for a variety of Linux distributions from Windows or Linux, without requiring you to burn a CD.

---

### Post by krisluv_18 on 2009-05-24
I tried UNetBootin, but everytime I try to use it, it always hangs on "Loading GRLDR, Starting cmain". When I looked it up, fixing it involved editing or deleting the boot.ini file in Windows. Instlux was an infinitely simpler solution at the time.

---

### Post by jflaker on 2009-05-24
when was the last time you used unetbootin?

I am trying it again as it has been a while for me....it doesn't seem that difficult, though, you may want to try the alternate ISO for your installation.

---

### Post by krisluv_18 on 2009-05-24
The most recent attempt was just last night. From what I've read, the reason it hangs is because Windows already had a "boot.ini" file, and if the system cannot find the one altered by UNetBootin, it will revert to the one made by Windows, causing it to hang...or so I think :confused:

---

