---
title: "Firefox not loading after upgrading to Feisty Fawn"
date: 2007-07-04
forum: Desktop Environments
---

### Post by acrimonious on 2007-07-04
Help would be appreciated.

When I try to start firefox, I get the "loading firefox" for about thirty seconds and then no browser window opens.

Already tried completely reinstalling firefox, no difference.

If I try to open it in the terminal I get the following:

error while loading shared libraries: libgtk-x11-2.0.so.0 cannot open shared object file: No such file or directory

Thanks for your time.

---

### Post by limbourg31 on 2007-07-04
did you apt-get remove firefox first? try a reinstall then, or one of the individual libraries

---

### Post by acrimonious on 2007-07-04
> **limbourg31 said:**
> did you apt-get remove firefox first? try a reinstall then, or one of the individual libraries

Yeah, I usually use the package manager but removing it with apt-get doesn't seem to make a difference. When I reinstall I still get the same result. 

I need to find out what exactly libgtk-x11-2.0.so.0 is.

---

### Post by limbourg31 on 2007-07-04
a simle synaptic search or just copying and pasting the package in apt might work

---

### Post by limbourg31 on 2007-07-04
libgtk-x11 is the library that works with x11 window managers for the gtk toolkit, and basically without it your windows won't function properly... a sudo apt-get install ubuntu-desktop or apt-get install gnome might help.

---

### Post by acrimonious on 2007-07-04
Thanks, didn't work though. Same as before, the gnome package actually isn't there anymore, I did install the ubuntu-desktop.

Same message as before, libgtk-x11-2.0.so.0 not being there.

---

### Post by limbourg31 on 2007-07-04
it wasnt' even in synaptic? try and fix broken dependencies there or go to the gtk ftp site and download it manually and compile it there

---

### Post by acrimonious on 2007-07-04
> **limbourg31 said:**
> it wasnt' even in synaptic? try and fix broken dependencies there or go to the gtk ftp site and download it manually and compile it there

Well there are a bunch of gnome-related components in synaptic but not anything just called gnome, in terminal it says something along the lines of it's not there but is referred to by another component, it may be outdated, etc.

If I'm not mistaken ubuntu-desktop is gnome though. Unless I needed to use gnome-core or gnome-bin or something like that.

Otherwise I guess I'll get started looking for broken dependencies.

---

### Post by limbourg31 on 2007-07-04
i just thought that there may be some GTK libraries in GNOME downloads, well download some libgtk stuff in synaptic and see if that works

---

