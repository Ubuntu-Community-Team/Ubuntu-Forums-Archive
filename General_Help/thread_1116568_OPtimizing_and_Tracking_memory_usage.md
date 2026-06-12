---
title: "OPtimizing and Tracking memory usage"
date: 2009-04-05
forum: General Help
---

### Post by santoshgokak on 2009-04-05
I have Ubuntu 8.04 on Intel(R) Pentium(R) D CPU (2.8 GHZ).
i have recently upgraded my RAM from 512M to 1.5G.But after doing so , still the machine is not performing better.i keep track of memory usage via "free -m" command and System Monitor applet.

Even i have a firefox window open with 2 tabs and a terminal ,the output from "free -m" is as below

[SIZE="2"]
             total       used       free     shared    buffers     cached
Mem:          1510       1131        379          0        126        629
-/+ buffers/cache:        375       1135
Swap:          972          0        972[/SIZE]

What process may be eating up so memory?
what are other ways for tracking memory usage?
what are various ways in which i can optimize ubuntu to perfoma best as a desktop machine?BTW i also do quite some development on it ;)

---

### Post by kerry_s on 2009-04-05
dude your doing just fine, unused ram is wasted ram.

> What process may be eating up so memory?
what are other ways for tracking memory usage?
what are various ways in which i can optimize ubuntu to perfoma best as a desktop machine?

try installing htop> **sudo apt-get install htop**

you can use lighter programs to get better performance. 

i use a light window manager and a mix of light gnome and xfce4 programs. my laptops old, it's 450mhz 256mb ram.

---

### Post by santoshgokak on 2009-04-05
Looks like a lightweight and very interpretive tool.Installed it.
Thanks dude .:D:D

---

### Post by kerry_s on 2009-04-05
> **santoshgokak said:**
> Looks like a lightweight and very interpretive tool.Installed it.
Thanks dude .:D:D

forgot to mention, it's mouse clickable to. ;)
in the settings you can adjust the view.

---

### Post by mcduck on 2009-04-05
> **santoshgokak said:**
> 
-/+ buffers/cache:        375       1135

375 MB RAM usage with full-blown desktop and Firefox isn't really too bad. :)

If you want less than that you'll pretty much have to use some more lightweight desktop environment/window manager than Gnome, and some  lightweight browser. But you still have plenty of free RAM to play with and the system hasn't even touched the swap yet so I really wouldn't worry about the memory usage.

---

### Post by Sylslay on 2009-04-05
Hardwere problem with memory controlers?
Try take out old 512Mb of ram and run only new 1Gb ram.
Than see it will performe beter and checked again " free -m"

---

