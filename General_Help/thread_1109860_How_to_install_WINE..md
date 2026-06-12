---
title: "How to install WINE."
date: 2009-03-29
forum: General Help
---

### Post by prashantvrm on 2009-03-29
I dont have a internet connection at home i am accessing from a cyber cafe.So please help me in installing the WINE in ubuntu 8.04.

I want to install WINE to run windows apps.Plz give me the full instruction so that i wont had to connect to net at home becoz i dont have it.:guitar::guitar::guitar::guitar:

---

### Post by brayden13 on 2009-03-29
[http://downloads.sourceforge.net/wine/wine-1.1.18.tar.bz2?use_mirror=waix](http://downloads.sourceforge.net/wine/wine-1.1.18.tar.bz2?use_mirror=waix)
don't ask me how to install it or compile it or whatever. but there should be a readme that tells you how to do it in the archive.

in the archive if there is a configure file in there often you have to do this: open terminal and navigate the dir you extracted the archive, then do this command.
```
./configure
```
then it would come up with a heap of junk and then stop.
MOST TIMES afterwards you do this:
```
make
```
then you would have to do:
```
make install
```
i'm not sure if that is how you do it but most of the time that is the set of commands you input.

---

### Post by 3Miro on 2009-03-29
It is kid of pointless to compile wine yourself. There is the somewhat limited version wine-1.0, which you can install the newer version with more features, but somewhat less stale. To install the newer version, follow those instructions:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Secrest on 2009-03-29
> **prashantvrm said:**
> I dont have a internet connection at home i am accessing from a cyber cafe.So please help me in installing the WINE in ubuntu 8.04.

I want to install WINE to run windows apps.Plz give me the full instruction so that i wont had to connect to net at home becoz i dont have it.:guitar::guitar::guitar::guitar:

Go to Applications on the top panel and then Add/Remove.  Search for WINE and it will come up WINE Windows Emulator.  Check it then click apply and it will download.

---

