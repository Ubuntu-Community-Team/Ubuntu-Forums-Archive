---
title: "Troubles with Ubuntu (Studio) 18.10 Xfce on ThinkPad T400"
date: 2019-02-06
forum: Desktop Environments
---

### Post by agklimit on 2019-02-06
When I first installed this OS (clean install, no dual boot), everything worked fine until I pressed the "Software Update" option in the menu. It did the update, and after the restart the screen comes black (blank).

Just to clarify, the laptop is a ThinkPad T400 with integrated graphics only (so, no switchable graphics).

I repeated the install. I ran only "sudo apt-get update" (careful not to issue an "upgrade"). It ran fine for a while, I've even set up a vino server (because I needed to remote into this laptop), which is not an easy thing to do on Xfce, as I've learned. Anyway, I closed the system with only Suspend (not shut down, or restart). The next day, after starting, I couldn't get the Terminal to run (it came with an error, can't remember exactly what it said.) That was strange. I managed to start X Term, ran sudo apt-get update again, and then decided to be brave and ran sudo apt-get upgrade, as well (I thought that it could fix the broken Terminal.) Anyway, after restarting, again - nothing on the screen. I restarted and followed the grub Recovery Mode instruction to fix the problem (fix the broken packages). After this, it managed to boot (I got login screen) but it was all crooked and almost none of the programs would run, like everything was broken.

I have no idea how to fix this, but perhaps I'll repeat the install process with 18.04 - or even an earlier release? (Given that the laptop is a bit ancient at this point - although it works like new).

Did anyone have similar problems and/or what is the solution?

---

### Post by Autodave on 2019-02-07
I would start with your idea of installing 18.04 which is LTS.  I tend to stay away from the releases in between the LTS ones since they have new, somewhat unproven, code.  The LTS releases are way more stable.

Also: if it (LTS) doesn't work instantly, once you do get it to work, you will not have to upgrade every 6 months and risk breaking it again.

---

### Post by agklimit on 2019-02-08
Good idea, thanks.

---

