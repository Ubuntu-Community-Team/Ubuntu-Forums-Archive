---
title: "Ubuntu Running on Low Graphics Mode after Python Uninstallation"
date: 2010-02-19
forum: Desktop Environments
---

### Post by zeroseven0183 on 2010-02-19
I installed Python 3.1 and then tried to remove Python 2.6 and 2.5 from Ubuntu Software Center when suddenly the screen goes black and I was forced to run Ubuntu in low graphics mode. I noticed that there were some dependencies in Python but ignored them thinking that they're included in the later version 3.1. The complete error message is

> 
**Ubuntu is running in low-graphics mode**
The following error was encountered. You may need to update your configuration to solve this.

(EE) Failed to load module "i810" (module does not exist, 0)
(EE) conf/hal: couldn't initialise context: unknown error (null)


I'm running LiveCD and wouldn't want to reinstall Ubuntu all over again as much as possible.  Is there a way to recover?

Here's what I did so far:

1. boot to recovery mode to fix broken packages, didn't fix
2. boot to recovery mode and typed sudo dpkg-reconfigure xserver-xorg, didn't fix it

When I checked the /etc/X11, I only found Xorg.conf.failsafe (and other files) but not the Xorg.conf. Here's what it contains (I don't know if it's relevant):

> 
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


---

### Post by zeroseven0183 on 2010-02-20
* bump *

---

### Post by Hero of Time on 2010-02-20
Python 3.1 is not backwards compatible with 2.x. You need python 2.6 to get everything to work again, a lot of packages use python 2.6. Best you can do is boot to normal mode, log on to a TTY and run dhclient as root if you don't have internet connectivity and use a wire, then run aptitude as root. Within aptitude, you can check which packages are broken, reinstall packages and fix your python mess-up.
Of course, if you DO get a GUI, even if it's low res, you can use Synaptic Package Manager to fix everything.

Edit:
Don't bump threads when you don't have an answer in at least a day, it's a busy forum, someone will notice this thread at some time.

---

### Post by oldfred on 2010-02-20
As hero of Time says you need python 2.6 as it runs just about everything in the background in Ubuntu.

You may be able to chroot into your system and reinstall, but you have a lot to reinstall and I do not know a specific command to correct everything, this just shows reinstalling the desktop:

Of course you must first know what partition you want to mount, in this example I'm using sda1:

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
apt-get update
apt-get upgrade
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

