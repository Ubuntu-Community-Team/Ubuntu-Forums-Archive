---
title: "New computer specs, I want to know if it'll run Linux nicely!"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Maelgwyn on 2006-09-13
Hey guys,

title says it all really, so here are the specs - if any of them don't make any sense, it's not my fault I'm typing straight off the sheet!

Intel Core2Duo E6400 2.13GHz Dual Core CPU
ASUS P5B Chipset Motherboard
1Gb Dual Channel DDr 2 667 RAM
320Gb SATA2 7200RPM 16Mb Cache HDD
16x DVD +/- writer with double layer support
GeForce 7900GT 256Mb DDR3 Dual DVI/HDTV

with a 19" LCD :)

SO much better than my Pentium III Coppermine lol

---

### Post by chavo on 2006-09-13
Is this is a serious question? Or are you just gloating with your new machine?

---

### Post by Maelgwyn on 2006-09-13
it's a serious question! I don't have the computer yet - I'm saving towards it... I just want to make sure I'm not getting hardware that's going to make my Ubuntu life difficult... I'm going to have a WinXP partition for games, but I'll primarily be using Ubuntu :)

---

### Post by Circus-Killer on 2006-09-13
okay, to put it simply, a 386 machine can run linux (as in the kernel and some base packages). but i do know what you meant by the question, and the answer is yes, those specs will do fine with pretty much any distribution/desktop environment.
have fun. :rolleyes:

---

### Post by yota on 2006-09-13
Despite what previous posters said the question is well placed:

The intel 965 chipset (on wich the p5b is based) integrates no PATA controller, so asus put on board an additional jMicron controller to handle PATA drives.
Unfortunately this controller is not supported by Dapper and so is not possible (at present time) to install ubuntu by optical drives on that hardware.
It has been announced support starting by kernel 2.6.18 that hopefully will be included in Edgy.

See also this post:
[http://ubuntuforums.org/showthread.php?t=234706&highlight=p5b](http://ubuntuforums.org/showthread.php?t=234706&highlight=p5b)

---

