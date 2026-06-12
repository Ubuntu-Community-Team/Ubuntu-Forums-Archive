---
title: "Solution to Legacy Nvidia problem"
date: 2005-12-17
forum: Gaming &amp; Leisure
---

### Post by Sico on 2005-12-17
Hello, this is my first post and first time using linux in years.  I got my cd's from ship-it today and decided to try out Ubuntu.  Great OS and I love the forums, full of great info.  I had no problem setting up my favorite game, getting the sound to work, setting up the mouse... BUT, I could NOT get the GL version to work.  I had tried the drivers (archive) at nvidia, I had tried adding the legacy drivers, I had tried editing /etc/X11/xorg.conf and I was ready to give up.  Glad I didn't!!!

*** NOTE *** in /etc/X11/xorg.conf both glcore and dri are commented out from the MODULE section and  driver = nvidia under DEVICE***  This was done before hand in my attempts.

Here is the solution that worked for me:  (please let me know if this works for others that have this problem)

I simply went :  System>Administration>Synaptic Package Manager

Next, I organized my packages by those Installed (click on the title bar in the list)

Next I removed ALL nvidia* entries, as well as any legacy*nvida* entry.

Next I rebooted, X failed (great... but I expected it)

As X failed, and I was put into a terminal.  After logging in I typed:

```
 sudo apt-get install nvidia-glx-legacy
```
```
sudo halt
```

Then when I rebooted my computer I FINALLY (YES! :KS  ) got the nvidia logo.
I ran glxgears from terminal, YES.  I ran my favorite game, hi-res with the GL binary, YES!!!!!!!!  So as I frag away in my favorite first person shooter game...I wonder if I'll ever look at windows again.  Good luck to anyone with the same problem and I hope this helps you.

Nvidia Geforce 2 Ti (manuf.  Hercules)

---

### Post by arcanistherogue on 2005-12-17
Legacy is older, right?  I might use this on my TNT2 card from god knows when, I could play doom on my server box :D

---

