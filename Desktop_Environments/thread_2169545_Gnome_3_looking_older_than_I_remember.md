---
title: "Gnome 3 looking older than I remember"
date: 2013-08-22
forum: Desktop Environments
---

### Post by mishaparem on 2013-08-22
I remember having Gnome 3 on a different Ubuntu machine, and it had a hot corner, an overview, a dash, etc... I just installed Gnome3 on a VM, and it looks like the older version. None of the shortcuts to the overview (Alt+F1, hot corner, windows key) bring up overview, I can't find the dash, and the entire theme looks squared out (as opposed to the rounded corners I remember) Has Gnome3 changed or am I doing something wrong?

Edit: Moar Info:

VM : Oracle Virtual Box with Guest Extensions (by Canonical/Ubuntu) installed.
Ubuntu: v12.04 LTS
Comp: Dell Precision M 4700
Host: Win 7

---

### Post by SweetAurora on 2013-08-22
I believe it's simply a graphics issue.. Gnome couldn't initialize the graphics in the VM and defaulted to Fallback Mode. Does the VM you use have good 3D support? Gnome Shell has to have 3D to work.

---

### Post by mishaparem on 2013-08-22
Oracle VirtualBox with Guest Extensions (courtesy of Ubuntu, or rather Canonical) installed. Now that you mention it, I remember having to wrangle the graphics before I got all the Gnome 3 features working on my older Ubuntu machine. I would think that the guest extensions would handle the graphics issues though, same type of comp that I had before, so if it worked there, should work here right? Running VM on a Windows (bleh) platform.

---

### Post by mishaparem on 2013-08-22
[solved] 

silly me.

Machine > Settings > Display > Enable3D

---

### Post by ibjsb4 on 2013-08-22
To mark thread solved :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

