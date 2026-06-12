---
title: "Cannot change gnome theme when using XGL?"
date: 2006-12-18
forum: Desktop Environments
---

### Post by pormogo on 2006-12-18
Hey all, after recently upgrading to 6.10  I moved back to using XGL when I found fglrx lacked support for AIGLX. I installed the xserver-xgl package from the ubuntu repositories and setup a session in /usr/share/xsession just as shown in the beryl wiki. I am able to enter the session and use everything just fine, and beryl functions correctly as well. However I am unable to change the gnome theme. It's not even using the human theme is reverts back to the default gnome theme. Does anyone know why this happens? I am unable to use any other gnome themes under XGL, even without beryl running. I can't seem to think of any reason why this would happen.

---

### Post by warmaster on 2006-12-20
I have the same problem, any ideas ?

---

### Post by mcduck on 2006-12-20
try running 'gnome-settings-daemon &' and if that helps add it to your startup programs (In System/Preferences/Session).

---

### Post by ZERO_SHIFT on 2006-12-28
I have the same problem!!

So where do I find this 'gnome-settings-daemon &'??

Thanks in advance

---

### Post by compwiz18 on 2006-12-28
Open terminal, type **gnome-settings-daemon &** in the box, and hit enter.  You can then exit the terminal.

---

### Post by ZERO_SHIFT on 2006-12-28
> **compwiz18 said:**
> Open terminal, type **gnome-settings-daemon &** in the box, and hit enter.  You can then exit the terminal.

Thanks that fixed the problem!!:D

---

