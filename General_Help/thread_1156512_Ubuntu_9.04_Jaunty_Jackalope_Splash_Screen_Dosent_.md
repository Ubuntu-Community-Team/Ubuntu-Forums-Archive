---
title: "Ubuntu 9.04 Jaunty Jackalope Splash Screen Dosent show up"
date: 2009-05-11
forum: General Help
---

### Post by RJ12 on 2009-05-11
Well yesterday I installed Ubuntu 9.04 using Wubi and I was shocked at all the amazing things my wireless internet worked fine without me installing drivers and the screens were awesome. One of my favorite things though is the splash screen for booting up and down. It was better than Ubuntu's Splash for 8.10 (which I had under virtualbox) But After booting up the computer the second time the splash screen never appeared just a black screen. I miss the splash screen can someone help me get it back?:(:confused:

---

### Post by RJ12 on 2009-05-12
*Bump*

---

### Post by RJ12 on 2009-05-12
*Bump*

---

### Post by stathol on 2009-05-12
Hmmm...beats me. Sounds like something is screwed up/missing with respect to usplash. Here's a "shotgun" solution that should fix anything related to the boot splash:

Start a terminal and run:
```
sudo apt-get --reinstall install usplash libusplash0 usplash-theme-ubuntu
```

I'm not quite sure how usplash and GRUB interact (or don't), so you should probably also take a look at your menu.lst file (in /boot/grub). Make sure that the "splash" parameter is set for whichever kernel you normally boot.

---

### Post by albatron on 2009-05-13
I'm having almost the exact same problem, except I see some odd lines of color that flash slowly three times before staying on, like its trying to bring up the splash screen, but something like that was normal before the splash came up on ibex for this 4 year old dell pos. also i did not use wubi.

I'm a terminal noob, but I tried the first part of your solution from the recovery mode since i can't login and it told me something like "usplash is not a valid command" I also tried the graphics fix and the fsck from the recovery mode, nothing. I even reinstalled the first time this happened and checked the disk for errors before trying again. buh. I'm gonna go vent on my bass, so heres this::guitar:

---

### Post by stathol on 2009-05-13
> **albatron said:**
> I'm a terminal noob, but I tried the first part of your solution from the recovery mode since i can't login and it told me something like "usplash is not a valid command"
It sounds like you may have missed the "install" portion of that command. If you typed "sudo apt-get --reinstall usplash *[etc.]*", then it would say something about usplash not being a valid command for apt-get. You could also split that apart into 3 commands if it makes it any simpler:

```
sudo apt-get --reinstall install usplash
sudo apt-get --reinstall install libusplash0
sudo apt-get --reinstall install usplash-theme-ubuntu

```

This does the exact same thing as marking those 3 packages (usplash, libusplash0, and usplash-theme-ubuntu) for re-installation in the GUI Synaptic manager, which is the other way to go about it. I just find apt-get faster to use when you already know the package names. Of course, if you can't boot to X, you don't really have an option :/

---

### Post by RJ12 on 2009-05-13
> **stathol said:**
> Hmmm...beats me. Sounds like something is screwed up/missing with respect to usplash. Here's a "shotgun" solution that should fix anything related to the boot splash:

Start a terminal and run:
```
sudo apt-get --reinstall install usplash libusplash0 usplash-theme-ubuntu
```

I'm not quite sure how usplash and GRUB interact (or don't), so you should probably also take a look at your menu.lst file (in /boot/grub). Make sure that the "splash" parameter is set for whichever kernel you normally boot.

I still dont have a splash screen

---

### Post by johnnydopefish on 2009-05-13
Just chiming in to say that initially, my 9.04 install displayed the splash screen but out of the blue one day it decided to toggle out of "quiet splash" mode halfway through on every boot.  It goes straight to a console that starts with "Loading files needed to boot."

I don't know why this happened but toggling the "gnome splash" service doesn't do anything and grub already displays "quiet splash" in its options.

I'd be interested in a resolution as well.

---

### Post by RJ12 on 2009-05-16
*Bump*

---

### Post by reydempto on 2009-06-29
I am having the same problem. /boot/grub/menu.lst is correct, as far as i can see. i reinstalled libusplash0, usplash, and usplash-theme-ubuntu, and still, no splash.

it happened when i tried to install a different one that had tux on it lol..maybe just not compatible with 9.04?

---

