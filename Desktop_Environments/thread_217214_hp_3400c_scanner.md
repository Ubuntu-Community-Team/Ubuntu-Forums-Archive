---
title: "hp 3400c scanner"
date: 2006-07-16
forum: Desktop Environments
---

### Post by operationsone on 2006-07-16
Hi,

My scanner is a hp 3400c. It's not supported on the version of sane that comes with Ubuntu. I have completely removed the version that comes with the system and compiled sane 1.0.18 (stable version, has the backend for my scanner, which is niash). However, it still cannot detect my scanner (it's an USB scanner). By reading the manpages I've found that sane needs libusb 0.1.6 or newer, however the version of libusb that comes with ubuntu is 0.1.4. The problem is that when i try to remove libusb 0.1.4 a LOT of applications that depend on it will also be removed. Is there a way to install the new library without having to lose all the apps together with it (that would just break my system).

Thank you for your patience :)

---

### Post by operationsone on 2006-07-16
Well, I solved my problem :) compiling the new libusb, compiling sane 1.0.18 and restarting the computer solved my problems. The scanner now works.

If anyone is interested:
[http://libusb.sourceforge.net/](http://libusb.sourceforge.net/)
[http://www.sane-project.org/](http://www.sane-project.org/)

---

