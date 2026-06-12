---
title: "Dell D600 WIreless 802.11g WEP Problem"
date: 2007-10-01
forum: Dell  Ubuntu Support
---

### Post by domat00 on 2007-10-01
I have a Dell Latitude D600 laptop, with a BCM4309 802.11a/b/g\Dell TrueMobile 1400, and I tried the tutorial on BCM43xx cards, but it didn't work.  I downloaded the driver for the card from Dell, but ndiswrapper needs a .inf instead of a .exe, which is what the driver's format is.

Can you give me a solution, or do I just have to google and futz with it for a week?

---

### Post by silverdarkness on 2007-10-01
The inf file you want is inside the exe file. (Its a self extracting archive)

Use:

```
unzip -a yourfile.EXE
```

to get extract the files

---

### Post by domat00 on 2007-10-01
Which file do I use with Ndiswrapper?  The .inf files are as follows:  AR\bcmwl5.inf, AR\bcmwl5a.inf, IR\bcmwl5.inf, IR\bcmwl5a.inf.  Those are all the .inf's that were extracted.

---

### Post by domat00 on 2007-10-02
Bump

---

### Post by whi+eNoi$e on 2007-10-02
If you are uncomfortable extracting in linux (and the broadcom 43xx ubuntu forum help guide I believe tells you how to do it) you can just extract on windows and drop all of the files onto a flash drive 'pre' extracted for linux.

Locate the .inf file before you move it over just to be sure you can see it and know its path.

Easy peasy...:)

---

