---
title: "America's Army problem"
date: 2005-11-14
forum: Gaming &amp; Leisure
---

### Post by sexualpotatoes on 2005-11-14
when i try to run america's army i get this


michael@mike:~$ armyops
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error


can anyone help me?

---

### Post by cdsboy on 2005-11-14
It looks like you need to install a new graphix driver or enable DRI

---

### Post by sexualpotatoes on 2005-11-14
how do i do that?

---

### Post by cdsboy on 2005-11-14
what graphix card do you have? also for the driver i would try the synaptic.

---

### Post by sexualpotatoes on 2005-11-15
ATI x800xl

keep in mind i have 64-bit, i'll try synaptic

---

### Post by sexualpotatoes on 2005-11-15
[QUOTE=sexualpotatoes]ATI x800xl

keep in mind i have 64-bit, i'll try synaptic[/QUOTE]
synaptic doesn't have it, and i have been trying to get the ati64 bit drivers to work by installing...it has been telling me to edit something in command line w/o gnome and i don't know how to stop gnome

---

### Post by cdsboy on 2005-11-15
i would guess that being on 64 bit is the problem. i'm not sure if there is a source for americas army but if there is i would suggest installing from that.

---

### Post by sexualpotatoes on 2005-11-15
[QUOTE=cdsboy]i would guess that being on 64 bit is the problem. i'm not sure if there is a source for americas army but if there is i would suggest installing from that.[/QUOTE]
couldn't find one

---

### Post by cdsboy on 2005-11-15
well i can't help ya then sorry.

---

### Post by dmn_clown on 2005-11-19
[QUOTE=sexualpotatoes]synaptic doesn't have it, and i have been trying to get the ati64 bit drivers to work by installing...it has been telling me to edit something in command line w/o gnome and i don't know how to stop gnome[/QUOTE]

Many ways to do this...

```
sudo bash
```
```
init 1
```

is just one way.  When done doing what you need to do:

```
init 5
```

Good luck with ATi's drivers, you'll need it, they really suck.  There is a reason why nVidia cards are so popular with GNU/Linux people.

---

### Post by newuser111 on 2005-11-20
read this [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

