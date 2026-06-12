---
title: "Cant log in anymore, kde 4.4"
date: 2010-01-30
forum: Desktop Environments
---

### Post by Falc7 on 2010-01-30
Hi
I've been using kde 4.4 since rc1, and upgraded to rc2 when it came out. Had no problems, however  usddenly now i cant log in. I put my password in, the screen flashes black, then reloads the log in screen. I can log in using the command line interface (ctrl + f6). Can anyone help?

---

### Post by SuperSonic4 on 2010-01-30
I did have this problem before, dunno if it still applies but apparently PulseAudio is needed.

What happens if you try running startx from a terminal?

---

### Post by Falc7 on 2010-01-30
It tells me startx is not installed, shall i try installing, rebooting and then logging in?

---

### Post by SuperSonic4 on 2010-01-30
Try xinit first. You shouldn't need to reboot, simply restart KDM

---

### Post by Untitled_No4 on 2010-01-31
I had a similar problem the other day and that what fixed it was reinstalling KDM (sudo aptitude reinstall kdm).

If it tells you during the installation that kdmrc (I think that was the file) has changed and asks you whether you want to keep local changes or use the one that comes with KDM choose to use the one that comes with KDM (unless you have made changes to the file yourself, of course).

---

### Post by Falc7 on 2010-01-31
> **SuperSonic4 said:**
> Try xinit first. You shouldn't need to reboot, simply restart KDM

This, and adding more free space to kubuntu seems to have fixed the problem :)

---

