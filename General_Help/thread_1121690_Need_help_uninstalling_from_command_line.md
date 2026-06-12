---
title: "Need help uninstalling from command line"
date: 2009-04-10
forum: General Help
---

### Post by Collin White on 2009-04-10
Help! and D'oh! respectively.

First off, I am running the Jaunty beta on a Dell D600 laptop.  I installed a few things via the application manager; some games, the Edubuntu educational suite, and an ATI graphic driver utility.  I think that might be the problem as when I rebooted the screen shows a garbled image and fades to white pixels.  I don't think the boot process completes as I don't hear the sound that usually plays at the login screen and typing does nothing.

I tried booting and using the utilities in the Grub manager; reverting to an earlier version or fixing problem graphics, in fact I tried every option on the list, but the end result is the same.

I booted a 8.04 Live CD and the graphics and display worked fine, so this makes me think that the ATI utility is the culprit.

So... is there a way to remove this utility or reset the default graphics from the Grub "boot to root with command line" option?

Failing that, can I partition the drive with the Jaunty install and a fresh 8.04 install from the CD with the goal of accessing my files long enough to transfer them to a stick and reinstall?  Would I be able to access them across the partition?  My main concern is that I have baby photos of my daughter that I don't want to loose.

Thanks in advance for any insight/help.

---

### Post by 505 on 2009-04-10
You can uninstall any package in a command line with the command
```
sudo aptitude remove *package*
```
However, if you have problems with your graphic card, you can first try to edit the /etc/X11/xorg.conf file. In this file, the driver is listed that is used. You can change it back to the open source version (I believe called 'ati')

---

### Post by Collin White on 2009-04-10
> **505 said:**
> You can uninstall any package in a command line with the command
```
sudo aptitude remove *package*
```
However, if you have problems with your graphic card, you can first try to edit the /etc/X11/xorg.conf file. In this file, the driver is listed that is used. You can change it back to the open source version (I believe called 'ati')

Forgive my n00bness, but can you use gedit if you boot as root from grub without loading the OS?

---

### Post by boombox1387 on 2009-04-10
> **Collin White said:**
> Forgive my n00bness, but can you use gedit if you boot as root from grub without loading the OS?

No, you'd have to use a terminal-based editor, which I have always found more than tricky.  What I'd recommend is that you boot up using a live CD, mount your Ubuntu partition, and then look in that partition for /etc/X11/xorg.conf and edit it that way.  The free 'ati' driver should work, and if that doesn't, you can try setting it to the failsafe 'vesa' driver.  It will probably look really ugly, but at least you'll hopefully be able to boot your system and fix your problems graphically.

---

### Post by CatKiller on 2009-04-10
> **Collin White said:**
> Forgive my n00bness, but can you use gedit if you boot as root from grub without loading the OS?

**nano** is a pretty straightforward command line text editor. The keyboard shortcuts to do things are listed at the bottom of the screen. ^ is a fairly standard way of representing the Ctrl key. So if you wanted to exit, for example, you'd use Ctrl-X.

---

### Post by boombox1387 on 2009-04-10
> **CatKiller said:**
> **nano** is a pretty straightforward command line text editor.

Hmm, I've never tried nano.  I'll be sure to look at that one the next time I can't graphically boot my computer :)  Thanks CatKiller.

---

