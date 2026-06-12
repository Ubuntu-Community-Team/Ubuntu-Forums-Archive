---
title: "Unity doesn't work on 10.10"
date: 2011-04-03
forum: Desktop Environments
---

### Post by Ginosal on 2011-04-03
Hi. I've got Ubuntu 10.10 with the following kernel: 2.6.35-28-generic . Unity doesn't work for me! I've downloaded it and all required packages, but when I start a session with "Ubuntu netbook edition", I only get an empty desktop! No left panel, no upper panel, no icons... nothing at all! I've attached a text file with the output of the command 'unity' in a terminal. Thank you!

---

### Post by Krytarik on 2011-04-03
Unity (normal, not 2D) depends on hardware accelerated video. Otherwise, it looks like you are experiencing it.

In "classic" Gnome, are you able to run desktop effects?

What video card/chip do you have?

Check with
```
lspci |grep VGA
```
if you don't know.

What driver are you running?
How did you install those?

---

### Post by Ginosal on 2011-04-03
> **Krytarik said:**
> Unity (normal, not 2D) depends on hardware accelerated video. Otherwise, it looks like you are experiencing it.

In "classic" Gnome, are you able to run desktop effects?

What video card/chip do you have?

Check with
```
lspci |grep VGA
```
if you don't know.

What driver are you running?
How did you install those?

Desktop effects work fine on Gnome, all of them! The chip is: ATI Technologies Inc RS690 [Radeon X1200 Series]. I've never installed drivers, i think they were installed automatically when I installed Ubuntu for the first time. If I try to open "Hardware drivers", it's empty. But it's also empty on my notebook, on which unity works fine. Thank you!

---

### Post by Krytarik on 2011-04-03
Unfortunately your card isn't covered by the proprietary driver anymore.
But you may try upgrading to the Open Source Edge Driver to get the most possible performance:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Ginosal on 2011-04-04
> **Krytarik said:**
> Unfortunately your card isn't covered by the proprietary driver anymore.
But you may try upgrading to the Open Source Edge Driver to get the most possible performance:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

Thank you... but then why do gnome effects work?

---

### Post by Krytarik on 2011-04-04
> **Ginosal said:**
> Thank you... but then why do gnome effects work?
Maybe because Unity requires a higher performance than the Gnome desktop effects. I really don't know, since I can't even install it at my Lucid system.

---

### Post by FrankenCub on 2011-04-05
Is there a list of what video cards will be supported for Unity 3d to work correctly ?

---

### Post by Copper Bezel on 2011-04-05
> Hi. I've got Ubuntu 10.10 with the following kernel: 2.6.35-28-generic . Unity doesn't work for me! I've downloaded it and all required packages, but when I start a session with "Ubuntu netbook edition", I only get an empty desktop! No left panel, no upper panel, no icons... nothing at all! I've attached a text file with the output of the command 'unity' in a terminal. Thank you!

The package Unity in 10.10 is a completely separate package from the one in 11.04. It's based on Mutter, not Compiz, and I don't think it was ever switched in the 10.10 release cycle. If you've downloaded and installed the Ubuntu 11.04 version, it's not going to jive with Ubuntu 10.10. The 10.10 version isn't really worth playing with, either, especially with 11.04 going to full release status in less than a month. If you want to do Unity, it's going to be simplest to upgrade to 11.04. 

That said, if your graphics card isn't supported anymore - well, maybe it's best to play with a LiveCD first, yes?

---

