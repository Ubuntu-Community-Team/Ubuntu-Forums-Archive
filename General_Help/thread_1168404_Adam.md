---
title: "Adam"
date: 2009-05-24
forum: General Help
---

### Post by adamsomebody on 2009-05-24
Hey,

I'm really new to Linux.  I'm using the gos distribution and I'm trying to get my Lexmark E238 Laser printer to work.  It's hooked up but I just get error messages when I send something to print.

Also, if anyone out there knows what I can do to get flash videos to stop being so choppy, it would really help me out.

I'm looking forward to the day that I can contribute something here, but right now I'm eagerly learning the ropes!

---

### Post by DeMus on 2009-05-24
> **adamsomebody said:**
> Hey,

I'm really new to Linux.  I'm using the gos distribution and I'm trying to get my Lexmark E238 Laser printer to work.  It's hooked up but I just get error messages when I send something to print.

Also, if anyone out there knows what I can do to get flash videos to stop being so choppy, it would really help me out.

I'm looking forward to the day that I can contribute something here, but right now I'm eagerly learning the ropes!

A good to way to start is to give your posts a good title. One which describes the problem(s) you have. This way others, who search the forum while having a similar problem, will find your thread and hopefully also the solution.

This said, I do wish to continue with welcome to the wonderful world of Linux.

What did you do to install the printer? Just hooked it up and switched it on to let Ubuntu recognize it, or did you have to install a driver manually?

Choppy flash movies indicate a not properly working videodriver.
Open a terminal (Menu Applications - Accessories - Terminal) and type
```
lspci | grep VGA
```
and post the outcome here please.
You can do that to select the complete line in the terminal with your mouse, press Shift+ctrl+c to copy the text and paste it in your answer.

Next we need to know is info about your graphical system.
type
```
more /etc/X11/xorg.conf
```
copy the outcome like before and also post it here.

---

### Post by Liolikas on 2009-05-24
Those two links fully describe how to install printer.
[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-E238](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-E238)
[http://www.linuxforums.org/forum/linux-newbie/72673-how-do-i-install-ppd-bin-file.html](http://www.linuxforums.org/forum/linux-newbie/72673-how-do-i-install-ppd-bin-file.html)

Install adobe flash the latest from synaptic. Or from adobe page in windows way.

---

### Post by ad_267 on 2009-05-24
How did you install the flash player?

---

