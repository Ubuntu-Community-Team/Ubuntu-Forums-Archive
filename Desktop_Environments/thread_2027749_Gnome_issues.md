---
title: "Gnome issues"
date: 2012-07-16
forum: Desktop Environments
---

### Post by DeltaFee on 2012-07-16
Hey I'm not sure this is the right place but I am having issues with gnome, sometimes the icons on the Desktop disappear and opened windows crash. I am using the gnome session instead of Unity because I am not a big fan of Unity. thanks ahead of time!

---

### Post by nothingspecial on 2012-07-18
*Thread moved to **Desktop Environments**.*

---

### Post by kansasnoob on 2012-07-18
> **DeltaFee said:**
> Hey I'm not sure this is the right place but I am having issues with gnome, sometimes the icons on the Desktop disappear and opened windows crash. I am using the gnome session instead of Unity because I am not a big fan of Unity. thanks ahead of time!

It's unclear to me what desktop session you're running so please open the [terminal]("http://www.psychocats.net/ubuntu/terminal"), run this command, and post the results here:

```
echo $DESKTOP_SESSION
```

---

### Post by DeltaFee on 2012-07-20
Sorry I'm using gnome-classic.

---

### Post by kansasnoob on 2012-07-21
There are two classic sessions. The standard "Gnome-classic" session which uses the Compiz window manager, but also a "Gnome-classic (no effects)" session which uses the Metacity window manager.

I've found the standard classic session to be very buggy (nautilus crashes, panel crashes, etc) but classic (no effects) works quite well for me:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

