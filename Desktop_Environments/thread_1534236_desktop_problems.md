---
title: "desktop problems"
date: 2010-07-19
forum: Desktop Environments
---

### Post by Drenriza on 2010-07-19
when booting up the system it promts for user and pass.

After entering username and password followed by enter the system looks like its going to start. But no, it loads a white page for a couple of seconds and then go back to the section where you enter username & password. Why? the user and pass was correct.

If i hit ctrl + alt +f1 and use the same username and password i can login with the CLI. But not in the graphical login prompt.

How does such a problem gets fixed?

---

### Post by mikewhatever on 2010-07-19
Start by posting the hardware specs: CPU, RAM, _graphics card model_.

---

### Post by Drenriza on 2010-07-19
VGA compatibe controller: VIA Technologies, inc. CX700/VX700 [S3 UniCharome Pro] (rev 03)

VIA Esther processor 1200Mhz


I had no problems after install. But then i did an
sudo apt-get autoremove
rebooted
And now :(

---

### Post by Drenriza on 2010-07-19
Solved.

I had maxed out the disk with 100%. And then it was not able to load the desktop-environment.

---

### Post by mikewhatever on 2010-07-19
Autoremove doesn't remove anything from the default installation. Try remembering what was removed before that.
In case removed packages are the problem, put the Ubuntu cd into cdrom, login from console, and then:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo reboot
```

---

