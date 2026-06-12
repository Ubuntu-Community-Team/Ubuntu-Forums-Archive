---
title: "Xubuntu 13.04 or Firefox 21.0 crash on certain websites"
date: 2013-06-01
forum: Desktop Environments
---

### Post by cmolinap1 on 2013-06-01
Hi,

INFO:
Asus Eee pc 701SD, 8GB SSHD, 1GB RAM. 
Previously installed OS: Xubuntu 12.10 (Quantal). Problems experienced: zero.
Actual installed OS: Xubuntu 13.04 (Raring).
Installation date: today, June 1, 2013 (GMT-6, Central America time).
Problems experienced: Firefox 21.0 or Xubuntu 13.04 crash on certain websites (in my case, specifically with one: [http://www.laprensa.com.ni](http://www.laprensa.com.ni), by the moment).

Has anyone else experienced the same problem? Any solutions?

Thanks in advance.

cmolinap.

---

### Post by zemega on 2013-06-01
Currently qtwebkit js bundled with 13.04 has been identifed to contain bug, that would make any program crash when handling heavy java script. You can either wait for a patch to be issued by Ubuntu or you can try to patch it yourself, if you know how to, which I don;t know how to (didnt manage actually). You just have to use another distro or 12.04 instead. Using another type of browser probably wont help as well.
[https://bugs.launchpad.net/ubuntu/+source/qtwebkit-source/+bug/1180731](https://bugs.launchpad.net/ubuntu/+source/qtwebkit-source/+bug/1180731)

---

### Post by cmolinap1 on 2013-06-02
zemega, thanks for answering. I was doubting about the adobe-flash plugin. 

In fact, the only reason I installed xubuntu 13.04 it was because I reinstalled xubuntu 12.10, and I found that the Thunar repository was moved and it is impossible upgrade from Thunar 1.4.0 to 1.6.2 via ppa: xubuntu-dev/xfce-4.12 

I don't need GIMP, Abiword and GNumeric. I use LibreOffice. Xubuntu 13.04 also doesn't allow install Peazip (problem with dependencies). To my Asus Eee PC 701SD, Xubuntu 13.04 is too much. If I can find a way to update Thunar, I reinstall Xubuntu 12.10 or 12.04. Thunar 1.4.0 has many problems.

Again, zemega, thanks.

cmolinap.

---

### Post by binaryhermit on 2013-06-02
I'm pretty sure the problem isn't qtwebkit's javascript engine, since Firefox uses the Gecko rendering engine which has its own javascript engine.

---

