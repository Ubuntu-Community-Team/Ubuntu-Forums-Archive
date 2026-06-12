---
title: "GDM starts with no bars at all"
date: 2008-05-25
forum: Desktop Environments
---

### Post by WesleyWex on 2008-05-25
I've just reinstalled my linux PC with Ubuntu Hardy because of an additional hard drive would make me change all the partitions.

Everything was working fine until I restarted GDM so I could see synergy working, and after logon, only my desktop appeared, but no "Applications", no taskbar, no nothing!

I tried then to remove the synergy lines from /etc/gdm/Init/Default, /etc/gdm/PostLogin/Default and /etc/gdm/Xsession but nothing helped.

The desktop right-menu appears, but I cannot create a launcher, only folders and files. Alt+F2 does not bring the run dialog.

The problem here is that I don't know where to go to detect what is causing this, and I don't want to reinstall it again.

Here is a screen shot:
[[IMG]http://img359.imageshack.us/img359/1057/screenshotbd6.th.png[/IMG]]("http://img359.imageshack.us/img359/1057/screenshotbd6.png")

**Any idea?**

---

### Post by WesleyWex on 2008-05-27
Nobody?

---

### Post by Xiong Chiamiov on 2008-05-27
Try moving your gnome folder to force a new one:
```

mv ~/.gnome2 ~/.gnome2_old

```
then starting gnome again.  If this works, then you can narrow down (by copying folders and files over from your old folder) what exactly it was that caused the problem.  It takes a little bit of time, but you can find problem files that you never would have otherwise.

---

### Post by WesleyWex on 2008-05-27
> **Xiong Chiamiov said:**
> Try moving your gnome folder to force a new one:
```

mv ~/.gnome2 ~/.gnome2_old

```
then starting gnome again.  If this works, then you can narrow down (by copying folders and files over from your old folder) what exactly it was that caused the problem.  It takes a little bit of time, but you can find problem files that you never would have otherwise.

I found the issue, I don't use most of the software that comes installed with ubuntu desktop, so I was uninstalling all them, and removed the evolution-data-server-common, and gnome-panel, so X was starting but the panels didn't exist (interesting that no error was being shown).

Now I've reinstalled it and everything came back to normal.

I wonder why gnome-panel depends on something that has nothing to do with it. Well, at least it shouldn't, due to its name.

---

