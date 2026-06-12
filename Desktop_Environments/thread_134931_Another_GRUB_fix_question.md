---
title: "Another GRUB fix question"
date: 2006-02-22
forum: Desktop Environments
---

### Post by pwrstick on 2006-02-22
Halo,

Me:
Ubuntu ALREADY installed
One IDE hard drive, 3 partitions:
1: WindowsXP /media/hda1
2: Ubuntu /media/hda2 (ext3)
3: Swap

In my posession:
Ubuntu x86 Breezy Badger INSTALL

Grub worked great. I'd like it back please. I've been looking at numerous posts and sites, and none seem to be working for me. (More likely: I'm not doing things correctly because I'm a nub).

Thanks for tips

P.S. Am I right to be surprised that my Ubuntu partition is not "/" or "/boot" according to install partition proggie thingie?

---

### Post by o_fortuna on 2006-02-22
[QUOTE=pwrstick]Halo,

Me:
Ubuntu ALREADY installed
One IDE hard drive, 3 partitions:
1: WindowsXP /media/hda1
2: Ubuntu /media/hda2 (ext3)
3: Swap

In my posession:
Ubuntu x86 Breezy Badger INSTALL

Grub worked great. I'd like it back please. I've been looking at numerous posts and sites, and none seem to be working for me. (More likely: I'm not doing things correctly because I'm a nub).

Thanks for tips

P.S. Am I right to be surprised that my Ubuntu partition is not "/" or "/boot" according to install partition proggie thingie?[/QUOTE]
Wait... you mean Grub doesn't work? If you install Breezy from the install CD and overwrite hda2 (that's what it's supposed to be, btw), it will delete your current Ubuntu and install Grub. Or is that not what you want?

---

### Post by cskeide on 2006-02-22
if I understand you correctly, you've already installed both ubuntu and windows, but now your grub boot menu is gone?

download the livecd, burn it, boot it, and in a terminal type:
```
sudo grub-install /dev/hda
```
reboot, and you should have grub again.

---

### Post by pwrstick on 2006-02-23
[QUOTE=cskeide]if I understand you correctly, you've already installed both ubuntu and windows, but now your grub boot menu is gone?

download the livecd, burn it, boot it, and in a terminal type:
```
sudo grub-install /dev/hda
```
reboot, and you should have grub again.[/QUOTE]

Here's the error I get:
"/dev/mapper/casper-snapshot does not have any corresponding BIOS drive."

Yes, Ubuntu was installed *after* installing XP.

XP was installed to my 40gig hard drive.  I chopped that in half, and then installed Ubuntu to the other 20 gigs.  GRUB was installed, and both OSs loaded perfectly.

Now only XP works (though I'm booted into the live CD right now), and I'm trying to fix GRUB.  (I broke GRUB when I was tinkering with the OS X 10.4.3 distro).

I'm working on moving to GNU/Linux exclusively, but that's kinda hard to do when I can't even boot into it :-)  But I should have a working install of Ubuntu installed on the second partition of this drive.

As I understand it, GRUB needs to edit my MBR?

And to answer the first post: I can reinstall Ubuntu, but I want to *learn* how to fix things.  I figure if I can get dirty in the OS I'll learn that much faster.  I'm literally just moving to GNU/Linux, so I'm pretty green.

---

### Post by pwrstick on 2006-02-23
Fixed:
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

Had to download Ubuntu LiveCD and then did everything.  Wrote to the MBR, works great  now (I'm in Ubuntu!)

Thanks for all your help!

---

