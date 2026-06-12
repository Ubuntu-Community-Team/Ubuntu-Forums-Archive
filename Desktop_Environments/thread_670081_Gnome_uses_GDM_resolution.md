---
title: "Gnome uses GDM resolution"
date: 2008-01-17
forum: Desktop Environments
---

### Post by mirzmaster on 2008-01-17
Hello,

I'm experiencing a strange problem involving GDM and Gnome resolutions.  Now I've read a lot of threads about GDM using the correct resolution but Gnome using an incorrect resolution, but I wanted to preface by saying that this is not my issue.

Currently I run my Gnome desktop at 1920 x 1200.  For whatever reason, GDM runs at 1680 x 1050.  I have no problem with that.

The issue is actually that roughly half the time Gnome will also start up in 1680 x 1050 as if it took a cue from GDM, despite the fact that my default Gnome resolution is set to 1920 x 1200.  This is rectified by pressing the Ctrl-Alt-Backspace combination to restart X.  This will always correct the issue such that GDM will still display at 1680 x 1050, but the Gnome desktop will correctly use 1920 x 1200 after logging in.

Again, this issue is only encountered about half the time, and inconsistently.

Some extra info:  I am running desktop effects, but I'm hoping that won't be an issue.

Any ideas?

---

### Post by mirzmaster on 2008-01-23
I'm surprised that no one else has experienced this issue!  I wonder if just adjusting the GDM resolution will resolve the problem...

---

