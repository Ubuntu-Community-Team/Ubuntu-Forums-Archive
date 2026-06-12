---
title: "[SOLVED] Out of Range When launching certain games..."
date: 2008-08-27
forum: Gaming &amp; Leisure
---

### Post by Jaeric on 2008-08-27
Hello all.  I have installed Tremulous as well as a few other games.  When I launch Tremulous and Super Tux, my monitor goes blank except for a white box that states "Out of Range".  I thought this was possibly due to my refresh rate so I fixed that problem, but it did not correct this.  Any suggestions would be greatly appreciated.  

Here are my particulars:

I am running Linux Mint Elyssa and Ubuntu Hardy (Separate Hard Drives)

VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

GLXGears
9125 frames in 5.0 seconds = 1824.857 FPS

---

### Post by Jaeric on 2008-08-27
Nevermind...fixed

Edited the autogen.cfg file and changed screen resolution to my desktop.

---

### Post by crispy_420 on 2008-08-30
What directory is this file in?

---

### Post by Perfect Storm on 2008-08-30
Normally they are hidden in your home directory. It's where it stores save games/user configurations etc.

eg; Tremulous

.tremulous

note the dot infront of the name - this means the file is hidden. Don't remove the dot to make it unhidden, the game(s)/applications can't find the folder then and will make a new default one.

---

### Post by crispy_420 on 2008-08-30
Think I figured it out in a different post. Try what I did here:

[http://ubuntuforums.org/showthread.php?p=5692348#post5692348](http://ubuntuforums.org/showthread.php?p=5692348#post5692348)

---

