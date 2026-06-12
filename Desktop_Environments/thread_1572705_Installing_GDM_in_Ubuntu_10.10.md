---
title: "Installing GDM in Ubuntu 10.10"
date: 2010-09-11
forum: Desktop Environments
---

### Post by Inventech on 2010-09-11
Is there a different way to install GDM themes in 10.10; I don't see the 'login window' option under system > administration?

---

### Post by nilarimogard on 2010-09-11
Those GDM themes stopped working a long time ago (starting with Ubuntu 9.10 or 9.04, I don't remember exactly). They are not compatible with the new GDM.

---

### Post by _snikkerz_ on 2010-10-09
That isn't true, although it does take a little more work. This link worked for me in 10.10. [http://www.zimbio.com/Ubuntu+Linux/articles/3QDP9PPt1Ai/how+change+login+screen+background+Lucid+lynx](http://www.zimbio.com/Ubuntu+Linux/articles/3QDP9PPt1Ai/how+change+login+screen+background+Lucid+lynx)

---

### Post by theanalyst on 2010-10-09
You can't change the whole theme of login window, which was a feature of GDM in older ubuntu versions, like 8.04. You only have the option of changing the background. I guess it is something to do with Gnome rather than Ubuntu.

---

### Post by _snikkerz_ on 2010-10-11
I am able to change the colors, fonts, etc... NOT just the background. and it stays those colors on reboot. Thanks and good luck!

---

### Post by nilarimogard on 2010-10-13
> **_snikkerz_ said:**
> I am able to change the colors, fonts, etc... NOT just the background. and it stays those colors on reboot. Thanks and good luck!

When you know how the real GDM themes used to look, changing the background and colors means nothing :P

---

### Post by LordDelta on 2011-03-27
[http://ubuntuforums.org/showthread.php?p=10605710#post10605710](http://ubuntuforums.org/showthread.php?p=10605710#post10605710)

This seems to work...

Basically they re-wrote gdm, so the old custom ui are no longer possible with the newer gdm, so you have to install the old gdm-2.20. Probably not for the faint of heart.

---

