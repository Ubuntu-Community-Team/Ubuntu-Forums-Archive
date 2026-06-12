---
title: "Restarts from terminal but not from graphical mode"
date: 2008-10-01
forum: Desktop Environments
---

### Post by Mechine on 2008-10-01
Hi guys, this is really weird i just installed Ubuntu on my Toshiba laptop and installation went fine except for the last part where it asked me to restart and when I pressed "Restart Now" it just stayed on a black screen for 10 mins and nothing was happening so I just turn it off (from power button). And it worked well and everything  but when I try to restart it from graphic mode (click the little shut down button and then the restart button) it does the same thing, just stays on a black screen. I can however restart it from a terminal with "sudo reboot" and that works fine. Anyone know what the problem might be and how would I need to fix it? Thanks!

---

### Post by Mechine on 2008-10-01
sorry for double posting but I can't edit, no it doesn't even work from terminal all i get is a blank screen :(

---

### Post by dagoth_pie on 2008-10-01
the command to reboot from the terminal is
```
init 6
```
that starts runlevel 6  whic essentially sends the reboot signal
But I'm guessing thats not where the problem is. when you boot up the computer what stage does it get to in the boot?

---

### Post by Mechine on 2008-10-01
what do u mean what stage? it boots fine into graphical mode and everything works the problem is when i restart it it just goes to a blank screen and that's it

---

### Post by dagoth_pie on 2008-10-02
Does the computer power off completely or does the screen just blank out, I don't think I'll be of too much help, it's a little over my head, sorry

---

