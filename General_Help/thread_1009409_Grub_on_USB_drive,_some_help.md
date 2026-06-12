---
title: "Grub on USB drive, some help?"
date: 2008-12-12
forum: General Help
---

### Post by Outspiration on 2008-12-12
Okay, first off all, I'm just experimenting. This is all for fun. Some kids play games, I like this. Only answer what I'm asking, don't spoil the rest for me. First I try on my own. Then I google. This is my last resort :)

Now what is my status:
I have a 4 gig FDD
-2 gig partition (Ubuntu 8.10, persistent)
-1 gig partition (empty, soon to be BartPE)
-200 meg partition (empty, soon to be GParted)
-700 meg partition (emty)
All FAT32

In the 2G partition I have installed grub, with 1 reference:
```

title     Ubuntu 8.10, Persistent
root      (hd0,0)
kernel    /casper/vmlinuz

```

Now when I try to boot this, grub comes up fine, I select the only thing to be selected, and boot. Lots of text passes, as if normal, then it stops, saying:"Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)"

What am I doing wrong?

Ps: device.map is ```
(hd0) /dev/sdc
```,and was created that way by the grub-install

---

### Post by zwygart on 2008-12-15
Seems that we have the same fun. Is use a 16G flash drive for datas and OS's. Seems that your are beginnig, so I will tell you my experiences. Grub is installed correctly, so nothing to say abaout this. I have ran succesfully on my drive Puppy4.00, PuppyNOP, UbuntuLiveCD8.04, UbuntuLiveCD8.10, GentooInstallCD, UBCD, SystemRescueCD. Not all at the same moment but severals. (I try to always have one puppy, one ubuntu). I got kernel panics on backtrack3, ophcrack, gparted and others I forgot (maybe slaxmint, archlinux, etc). I never tried to make persistance. So my explication to the problem is that the OS don't found from where he was started. I extracted the content of ISO's so the OS searched on CD drive and not on flashdrive. Some OS (like ubuntuLiveCD) only works, they know from where they came. Others it helps to add the argument root=/dev/sd?? wich says where are the other file (Installed ubuntu on my desktop). Sometimes it depends on the computer you boot from (BIOS ability, etc). But some OS I never found how to boot them (backtrack3, ophcrack, gparted). I also don't have a lot of time to spend search, but I am still learning. 

I think it is a problem with the OS, pass some arguments to the kernel like root=ROOT DEVICE, or edit files of the OS (/etc/fstab, /etc/initrd, etc). It should have solutions, if you found someones tell me about it.

Your menu.lst have to be modified. Check at this [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html) and edit your /boot/grub/menu.lst file or /grub/menu.lst

---

