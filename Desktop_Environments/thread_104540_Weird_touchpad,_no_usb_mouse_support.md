---
title: "Weird touchpad, no usb mouse support"
date: 2005-12-16
forum: Desktop Environments
---

### Post by Deicidus on 2005-12-16
I just installed Ubuntu (it seems really cool!), and the cursor is behaving very oddly. I can move the cursor, but sometimes it seems like it thinks I'm scrolling using the touchpad or something. It will randomly click even when I didn't tap, and if I drag a scrollbar, any mouse movement will scroll it back up. What's going on?

I also would like to disable touchpad taps being interpreted as clicks. How can I do this?

My external USB mouse will also not work. Isn't Ubuntu supposed to autodetect it when I plug it in or something?

I put all these in one post cause they're a good chance they're all caused by the same thing, since they're all mouse problems. Thanks for your help.

---

### Post by grsing on 2005-12-16
Depending on what type of touchpad you have, do a search for "Synaptics" or "ALPS" in this forum, and you'll find plenty of material to help you (to find out which one you have,  cat /proc/bus/input/devices in the terminal, look for Synaptics or ALPS).  I had similar problems (when it feels like its scrolling using the touchpad, it is, but thats what I was trying to enable, rather than disable), but got them fixed, so it can be done.

---

### Post by Deicidus on 2005-12-16
Thanks for the keyword! I didn't think to try that. I think I've almost got the problem solved now using the post at [http://www.ubuntuforums.org/showthread.php?t=101708&highlight=alps](http://www.ubuntuforums.org/showthread.php?t=101708&highlight=alps).

---

### Post by Deicidus on 2005-12-16
Scratch that. That page I gave didn't help my problem.

My USB optical mouse started working (it might have been the surface it was on, and maybe was working the whole time) and so I just tried disabling the trackpad. Instead, I stumbled upon something: when I changed the driver from "synaptic" to "mouse" it became an ordinary trackpad, with no irritating extra features full of bugs. Now it works just like I wanted, without the bugs.

---

