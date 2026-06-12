---
title: "System &gt; Pref &gt;Apprearance can't find installed themes"
date: 2008-11-14
forum: Desktop Environments
---

### Post by blake82 on 2008-11-14
Hi Everyone,

The appearance preferences can't see *ANY* installed themes. There's only a custom theme that looks more like a default theme.

I've reinstalled the default themes from synaptic, I can see the themes in /usr/share/themes.... but I can't use any of them.

This all started yesterday when I accidentally filled up my ext3 partition and the system started acting really strange. I expanded the partition and all but one of the problems went away except this one.

I suspect this was triggered by the lack of space, and that there's a simple fix for it, I just don't know what it is.

Let me know if you have any thoughts.

Thanks,

Blake

---

### Post by bswilson on 2008-11-14
If you think that the disks are perhaps causing a problem, you could run an interactive file system check.  Hit Ctrl-Alt-1 to get to a non-graphical TTY, then stop the GUI, run a filesystem check, then reboot.

From a separate TTY, run these commands:

```
sudo /etc/init.d/gdm stop
```
```
sudo fsck -r
```

Then reboot.

---

### Post by blake82 on 2008-11-19
Thanks, that didn't fix it though.

The themes are installed, the problem is that appearance isn't seeing them (even though I can)

I suspect that a file that points to the themes was deleted or corrupted, where could I find this file? And how could I fix it?

---

### Post by Tomatz on 2008-11-19
Try manually installing a theme from here:

[http://www.gnome-look.org/index.php?xsortmode=down&page=0&xcontentmode=100](http://www.gnome-look.org/index.php?xsortmode=down&page=0&xcontentmode=100)

Download a **theme**

then

Just go to *preferences, appearance, install* (button) to install it.


;)

---

### Post by blake82 on 2008-11-19
Again, thanks!

---

