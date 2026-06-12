---
title: "strange desktop happenings"
date: 2009-02-10
forum: General Help
---

### Post by braveheart2 on 2009-02-10
you see it? its like when you drag left click and it stayed there :confused: it doesn't seem to cause problems but its still strange.

---

### Post by overlord.gaurav on 2009-02-10
Maybe a reboot will fix it !?

---

### Post by braveheart2 on 2009-02-10
> **overlord.gaurav said:**
> Maybe a reboot will fix it !?

:guitar::lolflag: yes it will...but it continues to happen and gets annoying, so i need a permanent fix not just to ignore it.

---

### Post by Yashiro on 2009-02-10
Try adding the bolded section to the relevant area of your xorg.conf.

> Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
...
**	Option	    "XAANoOffscreenPixmaps" "true"**
...
EndSection

---

### Post by braveheart2 on 2009-02-10
> **Yashiro said:**
> Try adding the bolded section to the relevant area of your xorg.conf.

dude i have no idea where to put that or how....im new:(

---

### Post by SeanTater on 2009-02-10
It's not that difficult, actually, but you can post the content of xorg.conf instead if you like.

---

### Post by braveheart2 on 2009-02-10
> **SeanTater said:**
> It's not that difficult, actually, but you can post the content of xorg.conf instead if you like.

how do i get the xorg.conf ?

---

### Post by Yashiro on 2009-02-10
Press Alt+F2.
Type gksudo gedit /etc/X11/xorg.conf
Scroll to the appropriate section of the text file.
Lets's say just below the 'Driver' entry.
Make a gap.
Paste in the text I bolded.
Close the file, when asked to save, say yes.
Then log out.

It may help. If not, you can just repeat this procedure but remove the line you added. 
No harm done.

---

### Post by jjpcexpert on 2009-02-10
> **braveheart2 said:**
> you see it? its like when you drag left click and it stayed there :confused: it doesn't seem to cause problems but its still strange.

It looks as if you need to up your screen Hertz, refresh rate.

My second post here.

And secondly, in KDE desktop effects I have been able to use my GPU's 3d capability right from the control-center.

:KS :popcorn: :lolflag: :P

---

### Post by braveheart2 on 2009-02-10
> **Yashiro said:**
> Press Alt+F2.
Type gksudo gedit /etc/X11/xorg.conf
Scroll to the appropriate section of the text file.
Lets's say just below the 'Driver' entry.
Make a gap.
Paste in the text I bolded.
Close the file, when asked to save, say yes.
Then log out.

It may help. If not, you can just repeat this procedure but remove the line you added. 
No harm done.

that text file is empty....

---

### Post by Yashiro on 2009-02-11
You typed it wrong. :)
Caps matter.

---

### Post by braveheart2 on 2009-02-11
> **Yashiro said:**
> You typed it wrong. :)
Caps matter.

still empty...im typing exactly the way he shows it.

---

### Post by Yashiro on 2009-02-11
I doubt it.
Do a file search for xorg.conf because it cannot be blank.

---

