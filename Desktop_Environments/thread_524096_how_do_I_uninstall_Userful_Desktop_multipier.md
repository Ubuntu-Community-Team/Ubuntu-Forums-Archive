---
title: "how do I uninstall Userful Desktop multipier?"
date: 2007-08-12
forum: Desktop Environments
---

### Post by Sleepstalker on 2007-08-12
I don't like the nag screen and really don't have much use for it . Alas I am a total Noob and can't figure out how to uninstall this app. Also somehow an icon which looks just like my icon called computer has shown up on my desktop...yes the computer icon under places...I can't make it go away.....:confused:

---

### Post by misfitpierce on 2007-08-13
what desktop multiplier?

---

### Post by local8 on 2008-01-21
sudo dpkg -r desktop-multiplier    :guitar:

---

### Post by fhmanas on 2008-06-01
> **Sleepstalker said:**
> I don't like the nag screen and really don't have much use for it . Alas I am a total Noob and can't figure out how to uninstall this app. Also somehow an icon which looks just like my icon called computer has shown up on my desktop...yes the computer icon under places...I can't make it go away.....:confused:

Hi, where you able to remove the Computer folder icon on your desktop as I also have it after removal of Userful.  

I want remove it as well.

---

### Post by dje on 2008-06-01
Press Alt + F2 and type:
```
gconf-editor
```
Then in gconf editor navigate to /apps/nautilus/desktop and untick 'computer_icon_visible'

hope that helps,
dje

---

### Post by fhmanas on 2008-06-01
> **dje said:**
> Press Alt + F2 and type:
```
gconf-editor
```
Then in gconf editor navigate to /apps/nautilus/desktop and untick 'computer_icon_visible'

hope that helps,
dje

Great! That did it.  Strange, that the first time i looked there that 'computer_icon_visible' was unticked.

Anyway, that removed it.

Thanks

---

