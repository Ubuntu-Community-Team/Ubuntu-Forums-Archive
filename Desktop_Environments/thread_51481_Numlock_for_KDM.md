---
title: "Numlock for KDM"
date: 2005-07-24
forum: Desktop Environments
---

### Post by lordgibbness on 2005-07-24
Hi,

I successfully enabled numlock at GDM startup uisng the guide here [http://www.ubuntuguide.org/#numlockx](http://www.ubuntuguide.org/#numlockx)

I have since installed kubuntu-desktop and enabled kdm (KDE seems so much smoother).

Is there any way that I can enable numlock now that I am using KDM, as there doesn't seem to be a /etc/X11/kdm directory?

Thanks.

---

### Post by SGC on 2005-07-24
Go to:
Control center -> Peripherals -> Keyboard

Under "Numlock on kde startup" section, check "Turn on"

---

### Post by lordgibbness on 2005-07-24
Thanks for the quick reply! Just what I was after. :)

---

### Post by lordgibbness on 2005-07-25
Actually this isn't quite what I wanted... this turns on numlock after logging in. I want numlock on at the KDM screen. Anyone know how I can do this? Is it similar to the GDM tweak?

Thanks.

---

### Post by SGC on 2005-07-26
[QUOTE=lordgibbness]Actually this isn't quite what I wanted... this turns on numlock after logging in. I want numlock on at the KDM screen. Anyone know how I can do this? Is it similar to the GDM tweak?

Thanks.[/QUOTE]
 This time I'm sure this will works, 

Open the following file:
/etc/kde3/kdm/kdmrc

Add the following line between **[X-*-Greeter]** and **AntiAliasing=false**:
**N**um**L**ock=**O**n

Make sure to match the cases, Capital letters are bolded.

---

### Post by lordgibbness on 2005-07-26
Found the NumLock line in the file, which I have uncommented and changed to On.
Thanks for your help. If it doesn't work then I'm sure I'll be back again! ;)

---

### Post by SGC on 2005-07-26
[QUOTE=lordgibbness]If it doesn't work then I'm sure I'll be back again! ;)[/QUOTE]
Anytime  ;-)

---

