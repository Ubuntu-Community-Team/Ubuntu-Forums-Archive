---
title: "KDE Fonts are HUGE!"
date: 2008-03-01
forum: Desktop Environments
---

### Post by mikaelsnavy on 2008-03-01
Hello,
I am trying to install a LinuxMCE computer hooked up to my Hi-Def TV. The problem is, once it installed, the KDE fonts are HUGE, like 1/3 the screen high. I cant really change any settings from the GUI. I have a Radeon X1600 graphics card and a 28" Sanyo TV.
Thanks,
Mikael Stadden

---

### Post by cosmin1086 on 2008-03-10
Same problem here. Any solutions? .. in gnome i had a similar problem with window titles but I was able to change the settings in Appearance. KDE is currently unusable as it is because I cannot make anything out.

---

### Post by mali2297 on 2008-03-10
Press Ctrl-Alt-F1 to get to a terminal. From there, try
```

sudo /etc/init.d/kdm stop
startx -- -dpi 96

```

Does it work?

---

### Post by cosmin1086 on 2008-03-10
I tried that but it says command not found. I believe it has to do with GDM being installed and currently in use. I did a *sudo dpkg-reconfigure gdm* and switched to kdm, but still same problem. If i do *gdm stop *and then startx it just comes up with gnome....

---

### Post by cosmin1086 on 2008-03-10
whoops, i looked in the directory and it was acutally:
kdm-kde4....will try again and post back.

---

### Post by cosmin1086 on 2008-03-11
It worked! Thank You

---

### Post by mali2297 on 2008-03-11
> **cosmin1086 said:**
> It worked! Thank You

Then, to make this permanent, see post #28 or #29 from this [thread]("http://ubuntuforums.org/showthread.php?t=583159?postcount=#28") (depending on whether you use gdm or kdm).

---

