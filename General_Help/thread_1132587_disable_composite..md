---
title: "disable composite."
date: 2009-04-22
forum: General Help
---

### Post by spriizha on 2009-04-22
Is there any way to disable composite? I just can't find it. Need better performance for games and etc.. Im running 9.04 beta ubuntu.

---

### Post by balaknair on 2009-04-22
Option 1: System menu> Preferences> Appearance--> Visual Effects--> Select 'None'

This turns off compositing(you can still re-enable it later)

Option 2: Install 'Compiz Fusion Icon' via the 'Add/Remove' applet in the Applications menu- use this to toggle compiz(the compositing manager) on/off as you require via an icon in the system tray.

---

### Post by spriizha on 2009-04-22
so if just disable it from vizual effects, then it's mean that its todaly runing on lowest graph ?

---

### Post by balaknair on 2009-04-22
> **spriizha said:**
> so if just disable it from vizual effects, then it's mean that its todaly runing on lowest graph ?

Compiz(the compositing manager) and Xorg with desktop effects enabled use up a fair amount of system resources, and yes, disabling Compiz can free up RAM and lower CPU/GPU usage.

---

### Post by sdennie on 2009-04-22
If you are sure you are never going to use it, you can also disable the composite extension in the X server.  In some (I'm not sure how many), this can make a difference in performance.  First:

```

grep Composite /etc/X11/xorg.conf

```

If you see this line:

```

Option		"Composite"	"Enable"

```


That means the composite extension has been explicitly enabled.  Open /etc/X11/xorg.conf and just change "Enable" to "Disable" on that line.  If you don't see that line, then add the following to the bottom of /etc/X11/xorg.conf:

```

Section "Extensions"
	Option		"Composite"	"Disable"
EndSection

```

That may not make any performance difference at all but, it's something else to try if you know you aren't going to use a compositor.

---

