---
title: "GUI doesnt load after installing nvidia drivers"
date: 2008-12-02
forum: General Help
---

### Post by Anonymous111 on 2008-12-02
I just installed ubuntu and it said i needed to update the drivers for my nvidia card.  I installed them, then when i restarted my computer the GUI wouldnt load and it came up with a command line interface or whatever u call it.  Is there any way to fix this?

---

### Post by NT4usB on 2008-12-02
From the tty (command line interface) (log in and)```
sudo dpkg-reconfigure -phigh xserver-xorg
``` enter your password when prompted.
Then...
```
startx
```
or...
```
sudo /etc/init.d/gdm restart
```

---

### Post by Anonymous111 on 2008-12-03
command generated an error...

---

### Post by Anonymous111 on 2008-12-05
crap....well, i reinstalled ubuntu and it worked fine....until i tried to install the drivers again.....but i actually realized that GNU was running the whole time, nvidia just couldnt find my display....also something about my graphics card not being in PCI slot.....although i have both my nvidia geforce 8500 GT's in the correct slots.....(is this a problem with running SLI on linux?)

so...is there anyway anyone can help....?

---

### Post by NT4usB on 2008-12-05
huh?
You're running two graphics cards?
I don't know what, if anything special is required to run two cards. I'd probably start with one, get it working, then install the other.
Tried Envy? It's in the repos...

ed: and no, two cards is not a problem in Linux. Check out the [youtube video]("http://www.youtube.com/watch?v=1DWzuIreDGA") of Ubuntu running six flat panels.

---

### Post by Anonymous111 on 2008-12-06
Actually, it was a problem with the graphics cards.   I tried taking the secondary one out  and now ubuntu runs fine.   

Is there any way to get it to work with both cards?

(Two Nvidia GeForce 8500 GT's on a MSI P7N SLI motherboard)

---

### Post by Anonymous111 on 2008-12-07
Help, anyone?

---

