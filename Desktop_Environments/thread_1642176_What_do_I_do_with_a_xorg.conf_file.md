---
title: "What do I do with a xorg.conf file????"
date: 2010-12-10
forum: Desktop Environments
---

### Post by whatthefunk on 2010-12-10
Trying to fix my screen resolution problem, I have made an xorg.conf file in the LXTerminal. Now what? How do I actually run this thing? (Am I just really stupid??)

---

### Post by sikander3786 on 2010-12-10
Which graphics card is there? Are the proprietary drivers needed and installed?

Modern X deals directly with the graphics stuff so no real need to create an xorg.conf.

```
lspci | grep VGA
```

---

### Post by whatthefunk on 2010-12-10
I have the exact problem described here:
[http://www.linuxquestions.org/questions/linux-general-1/xorg-conf-for-intel-82815-chipset-608658/](http://www.linuxquestions.org/questions/linux-general-1/xorg-conf-for-intel-82815-chipset-608658/)

I want to try the guys xorg.conf fix...

---

### Post by sikander3786 on 2010-12-10
Paste it in /etc/X11/ directory and reboot ;-)

You'll need root privileges and for that,

```
gksudo nautilus
```

The file should be named xorg.conf and be cautious while running nautilus with root privileges. Make sure you don't delete/modify anything by mistake.

---

### Post by whatthefunk on 2010-12-10
I got root privileges, opened up /etc/X11/xorg.conf and pasted in the file.  I rebooted and absolutely nothing happened.  The computer shut down and restarted like normal.
 
> The file should be named xorg.conf
 
How do you name this file?  Do I rebbot like normal by going through the shutdown menu?

---

### Post by sikander3786 on 2010-12-10
xorg.conf is the file name in which you paste your text ;-)

And you only need a simple reboot only. Nothing else. What did you expect that file to do?

---

### Post by whatthefunk on 2010-12-10
I was hoping that it would fix my screen resolution and mouse problem.

---

### Post by sikander3786 on 2010-12-10
Let us know which graphics card is there and did you install any drivers for that?

```
lspci | grep VGA
```

---

### Post by whatthefunk on 2010-12-10
Intel 82815 CGC
 
When I run lspci -n and paste the output at [http://kmuto.jp/debian/hcl/index.rhtmlx](http://kmuto.jp/debian/hcl/index.rhtmlx) it tells me that I have an XFree86 driver for the graphics card.

---

