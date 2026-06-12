---
title: "Update Problems"
date: 2005-09-16
forum: Desktop Environments
---

### Post by JayMan8081 on 2005-09-16
Since the last set of updates released earlier this week for 5.04 I have been unable to install the xlibs update.  I get the following error when I try to update it:
> 
E: /var/cache/apt/archives/xlibs_6.8.2-10.1_all.deb:  unable to stat `./etc/X11/xkb/keycodes/digital' (which I was about to install): Input/output error

I checked in /etc/X11/xkb/keycodes/ and when I do an ls -l I get the following:
> 
jhorsman@jhorsman:/etc/X11/xkb/keycodes$ ls -l
ls: digital: Input/output error
ls: powerpcps2: Input/output error
ls: riscpc: Input/output error
ls: sun: Input/output error
ls: xfree86: Input/output error
ls: xfree98: Input/output error
ls: sgi: Input/output error
total 4
-rw-r--r--  1 root root 435 2005-04-05 12:02 README

Does anyone have any suggestions or has seen this same issue?  TIA.

---

