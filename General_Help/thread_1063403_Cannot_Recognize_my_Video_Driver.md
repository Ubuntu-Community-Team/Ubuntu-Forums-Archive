---
title: "Cannot Recognize my Video Driver"
date: 2009-02-07
forum: General Help
---

### Post by Arnack on 2009-02-07
I have a Nvidia Geforce 8600 GTS and i'm trying to get the newest driver installed into my Ubuntu (newest version). When I go to the Hardware Drivers, I pick then newest driver, restart and Ubuntu says before startub that there is something wrong with my video card driver, and that I must start in default graphical configuration.
How do I select my drivers for my graphic card?

---

### Post by Arnack on 2009-02-07
So anyone have any ideas? Are you understanding?

---

### Post by paydaydaddy on 2009-02-07
From where are you trying to get/install the drivers?

---

### Post by Arnack on 2009-02-07
system>administration> hardware drivers.
I pick the recommended driver, it says I have to restart, I restart, and at startup Ubuntu says that there is a graphical error, and it gives me some options that don't work, and I end up having to go into Ubuntu with low scale graphic mode for this session.

---

### Post by mb_webguy on 2009-02-07
Have you tried using EnvyNG?  Use "sudo apt-get install envyng-core" to install the graphical version, then "envyng -t" to run it.  Choose the appropriate options from the menu, and it will automatically detect and install the appropriate driver for your nVidia card.

---

### Post by Arnack on 2009-02-07
I tried, but after installing it does not show up in applications>system tools (there is no system tools)

---

### Post by mb_webguy on 2009-02-07
You have to run envyng from the command line, using the command "envyng -t".  The GUI version for Gnome isn't currently functional.

---

### Post by Arnack on 2009-02-07
It says:
sudo: envyng: command not found

---

### Post by mb_webguy on 2009-02-08
Did you install the envyng-core package?  "sudo apt-get install envyng-core"

---

### Post by Arnack on 2009-02-08
Sorry about that, I installed everything. I installed the first driver it gave me, and it asked me to restart, which I did, and I still have the same problem.
But it does say in the Hardware Drivers window:
Nvidia Driver is is activated but not currently in use.

---

### Post by Yellow Pasque on 2009-02-08
Please don't crosspost; it's very confusing for people trying to help you.
[http://ubuntuforums.org/showthread.php?t=1063430](http://ubuntuforums.org/showthread.php?t=1063430)

---

### Post by Arnack on 2009-02-08
Sorry, I thought the other forum would be more useful to post in, just couldn't figure out how to delete.
I read that this version (the newest of Ubuntu) i'm using it not compatible with my Video card, so people suggest to downgrade to the other version of ubuntu, so I put the iso file on my flash drive and tried to boot from the flash drive and got this error:
disk I/0 error replace the disk, and then press any key

---

