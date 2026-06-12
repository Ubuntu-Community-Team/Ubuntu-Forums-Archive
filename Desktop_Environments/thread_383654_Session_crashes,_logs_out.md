---
title: "Session crashes, logs out"
date: 2007-03-13
forum: Desktop Environments
---

### Post by vyruss on 2007-03-13
Does anybody else get this? I think the latest updates to:

[B]gnome-applets
gnome-applets-data
gnome-panel
gnome-panel-data
libpanel-applet2-0[/B]

can cause my Edgy session to crash. All of a sudden my applications close and I'm thrown back to the GDM login screen.

I have downgraded all of these to **2.16.1-0ubuntu3** (the original Edgy versions) and I'm waiting to see if this will happen again.

Any thoughts?

---

### Post by taurus on 2007-03-13
You are not running out of disk space, are you?

<Ctrl><Alt>F2.  Log in and run

```
df -h
```

---

### Post by vyruss on 2007-03-13
> **taurus said:**
> You are not running out of disk space, are you?

<Ctrl><Alt>F2.  Log in and run

```
df -h
```

No, that's not the problem; I have plenty left.

---

### Post by vyruss on 2007-03-13
**Update:**

It wasn't those upgrades, the same thing happened with the older versions as well. I've now disabled **gdm** and I'm running GNOME through **startx** so that I can see what goes wrong on the console, if it crashes again.

---

### Post by vyruss on 2007-03-14
**Update 2:**

OK now I had a totally different crash. The PC just hard locked. Some random blinkenlights appeared on the screen, then it went black and nothing worked apart from the magic SysRq key combos. I am now heavily suspecting the binary beta NVidia drivers.

---

