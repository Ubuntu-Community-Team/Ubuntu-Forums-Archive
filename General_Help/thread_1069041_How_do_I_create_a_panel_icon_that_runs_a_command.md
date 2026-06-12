---
title: "How do I create a panel icon that runs a command?"
date: 2009-02-13
forum: General Help
---

### Post by jimmy the saint on 2009-02-13
I have a thinkpad T61, which suffers from [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/193970").  Essentially, once the hardware wireless switch is turned off (or on depending on how you look at it), disabling wireless, turning it back on does not revive wireless.  In order to do, I have to enter 
```
sudo rmmod iwl3945 && sudo modprobe iwl3945
```
to reset it.

I have tried to create a panel launcher to run the command.  I have played with the commands a little replacing sudo with gksudo, only having one (gksudo) and various other things.  The problem is, it will always unload the module (rmod) but never reload it (modprobe).  Is there a way to pull this off?  

The Ubuntu team is apparently not going to fix this for intrpid and according to the last comment, it is not yet fixed in jaunty.  I really don't spend the next year having to open a terminal to run that command every time I use that kill switch.  I'm a student and it gets a bit of use.

If someone has another suggestion to automate this I would love to hear it.

Thanks
JTS

---

### Post by geirha on 2009-02-13
The && operator is handled by the shell, either bash or sh. When running from a launcher though, the command is not run by a shell, and the && is not interpreted. Try specifically running those commands in a shell:
```
gksudo -- sh -c "modprobe -r iwl3945 && modprobe iwl3945"
```

---

### Post by jimmy the saint on 2009-02-17
I hate bumping a solved thread like this (I miss the thanks) but I had to.  I couldn't figure this out for a while, and that && business wouldn't have dawned on me.  This bug has driven me nuts, but its not so bad having to click an icon.  

Thanks man

---

