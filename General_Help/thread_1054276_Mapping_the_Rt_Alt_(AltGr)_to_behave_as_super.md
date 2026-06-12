---
title: "Mapping the Rt Alt (AltGr) to behave as super"
date: 2009-01-29
forum: General Help
---

### Post by krishnarao on 2009-01-29
Hi,
I use linux on a thinkpad X31 which has a pc-101 keyboard with no win/super key. Can anyone help me map the right alt (altgr) which I never use, to behave as a win/super key.
thanks,
Krishna

---

### Post by krishnarao on 2009-02-02
Doesn't anyone here use a thinkpad without win keys?

---

### Post by simion314 on 2009-02-02
> **krishnarao said:**
> Doesn't anyone here use a thinkpad without win keys?

I have a laptop that has win key but I do not need it. If it is a default in compiz or other application try to change those defaults.

---

### Post by krishnarao on 2009-02-02
I know that I can change the shortcuts in compiz itself. Twisted it may seem but I still want to map the AltGr to behave as Win key.

---

### Post by krishnarao on 2009-02-02
Very Easy.
Use xev to find out the keycode.
Create a file called .xsessionrc with this line:
xmodmap -e "keycode 108 = Super_L"
substitute with keycode in your case.
Works like a charm.

---

### Post by robobot on 2009-02-02
Here's a thread from a little while ago talking about the same problem with the same model of computer.

[http://ubuntuforums.org/showthread.php?t=1035750]("http://ubuntuforums.org/showthread.php?t=1035750")

This should help you.

---

