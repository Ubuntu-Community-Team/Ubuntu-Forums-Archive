---
title: "Lost window title bars and footers"
date: 2011-07-25
forum: Desktop Environments
---

### Post by alj on 2011-07-25
Hi,

I've recently installed Xubuntu and after a few days the application windows have lost the title bars, footers and borders. Any ideas how to sort this, or do I need to do another install?

Cheers

ALJ

---

### Post by 2F4U on 2011-07-25
Are there any errors in .xsession-errors in your home directory? Did you install or upgrade software?

---

### Post by alj on 2011-07-25
Can't find any .xsession-errors in the home directory. I did a full install, completely wiping out the old OS.

---

### Post by Toz on 2011-07-25
The xfwm window manager has probably crashed. Alt-F2 and run 
```
xfwm4 --display=:0.0 --replace
```

See also: [http://forum.xfce.org/viewtopic.php?id=6102]("http://forum.xfce.org/viewtopic.php?id=6102")

---

### Post by alj on 2011-07-25
> **Toz said:**
> The xfwm window manager has probably crashed. Alt-F2 and run 
```
xfwm4 --display=:0.0 --replace
```

See also: [http://forum.xfce.org/viewtopic.php?id=6102]("http://forum.xfce.org/viewtopic.php?id=6102")

I tried this but it didn't work. I also had a look at the link. However, in my frustration, I went into Task Manager and just killed xfce4-session ... which logged me out and when I went back in, everything was ok again. So, not sure what happened there and certainly wouldn't recommend that to anyone.

---

### Post by bikodog on 2013-03-16
> **Toz said:**
> The xfwm window manager has probably crashed. Alt-F2 and run 
```
xfwm4 --display=:0.0 --replace
```

See also: [http://forum.xfce.org/viewtopic.php?id=6102]("http://forum.xfce.org/viewtopic.php?id=6102")

worked perfect.

xubuntu 11.10
xfce 4.8

---

### Post by wildmanne39 on 2013-03-16
old thread closed!

---

