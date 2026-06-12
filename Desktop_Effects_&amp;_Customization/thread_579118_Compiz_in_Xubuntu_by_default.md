---
title: "Compiz in Xubuntu by default"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by apauloisdead on 2007-10-18
How do i make Compiz and emerald load at startup with xubuntu?

Right now i have to do compiz --replace

---

### Post by Gen2ly on 2007-10-18
now I'm pretty sure xfce has got compositing support.  Why do you want to add compiz?

---

### Post by the yawner on 2007-10-18
> **Dirk.R.Gently said:**
> now I'm pretty sure xfce has got compositing support.  Why do you want to add compiz?

Mmm... Probably because xfwm4 does not have a cubet. Anyway, I'm pretty sure there's a similar autostart thing in Xfce settings.

---

### Post by apauloisdead on 2007-10-18
> **the yawner said:**
> Mmm... Probably because xfwm4 does not have a cubet. Anyway, I'm pretty sure there's a similar autostart thing in Xfce settings.

How do i go about doing that?

---

### Post by sisco311 on 2007-10-18
```
sudo mousepad /etc/xdg/xfce4-session/xfce4-session.rc
```
change > Client0_Command=xfwm4 to > Client0_Command=compiz

---

### Post by Forlong on 2007-10-18
I guess saving your session while Compiz is running should do the job as well. :)

---

### Post by apauloisdead on 2007-10-18
will doing these include emerald also?

...and forlong, i have your blog bookmarked, it's a good read.

---

### Post by Forlong on 2007-10-18
> **apauloisdead said:**
> will doing these include emerald also?
If you save your session: yes.
But if you are running Gutsy (or the backported packages for Feisty) it doesn't really matter, because /usr/bin/compiz will load Emerald (if installed) with it anyway. :)

---

