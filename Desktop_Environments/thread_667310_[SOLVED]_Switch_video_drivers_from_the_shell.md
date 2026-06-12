---
title: "[SOLVED] Switch video drivers from the shell"
date: 2008-01-14
forum: Desktop Environments
---

### Post by zhimsel on 2008-01-14
I just had to replace my video card. It was an ATI, using the restricted driver and xgl. The new one is an nVidia. How can I switch/install the correct driver for the nVidia card using the command line? (I can't login to the gui, since I have incorrect drivers) 

Also, using my old card is not a possibility as the reason I replaced it was because I accidentally overheated it. Twice =]

---

### Post by taurus on 2008-01-14
You can reconfigure your X server again from a prompt with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Pick **nv** or even **vesa** from the list of drivers until you get your X up and running again.  Then, go into System -> Administration -> Restricted Drivers Manager and install nvidia for your new graphic card.

You can start X with

```
startx
```

---

### Post by zhimsel on 2008-01-14
I reconfigured, but it still gives me an error when I load X. ("Configuration could not be loaded. You are not allow to access the system configuration") I'm using compiz-fusion with emerald if that makes any difference.

---

### Post by zhimsel on 2008-01-23
> **zhimsel said:**
> I reconfigured, but it still gives me an error when I load X. ("Configuration could not be loaded. You are not allow to access the system configuration") I'm using compiz-fusion with emerald if that makes any difference.

I figured it out. I fixed the time from the command line (it was off) and X loaded fine.

---

