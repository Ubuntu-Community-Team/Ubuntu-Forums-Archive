---
title: "Desktop icons gone and topbar icons shifted left"
date: 2016-04-15
forum: Desktop Environments
---

### Post by hvn2 on 2016-04-15
Hi,

When using a program with CD, the whole system suddenly froze. I could do nothing else but press the power and restart (and remove the cd). Now, My desktop is now empty except for trashbin, personal map and filesystem. Also, all icons that were at the right-side of the top menu bar, are suddenly at the left-side. I can access application via the menu, and when I start applications, the top menu bar icons, shift to the right along with any application notification. I looked in .config/xfce4/desktop/icons..... and all looks ok. Can somebody please tell me what may have happened to my desktop and how I may restore it?

Thanks!

hvn

---

### Post by ajgreeny on 2016-04-15
Which version of Xubuntu?

Let's see the content of your .config/xfce4/desktop/icons..... file (in code-tags please; see my signature below for a how-to)

Finally let's see the output of command ```
ls -l Desktop
```

---

### Post by hvn2 on 2016-04-15
> **ajgreeny said:**
> Which version of Xubuntu?
Xubuntu 14.04

> Let's see the content of your .config/xfce4/desktop/icons..... file (in code-tags please; see my signature below for a how-to)
```

[xfdesktop-version-4.10.3+-rcfile_format]
4.10.3+=true

[Prullenbak]
row=1
col=0

[/]
row=2
col=0

[/home/huub]
row=6
col=0


```


> Finally let's see the output of command ```
ls -l Desktop
```
In Dutch:
ls -l Bureaublad/
totaal 0

Something seems to be wrong...

---

### Post by ajgreeny on 2016-04-15
Well at least that shows why there are no launcher icons on your desktop;  there are no .desktop files in your Desktop folder, hence nothing there to show.  The question remains, however, ie, where did they go and what deleted them?  I can only assume the freeze and hard shutdown has corrupted and/or lost those files.

Similarly the icons.... file in xfce4's config folder does not show any of the expected entries for those launcher icons.

Do you have a backup of all your /home?

---

