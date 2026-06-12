---
title: "Another Dual boot question"
date: 2005-12-07
forum: General Help
---

### Post by bslusser on 2005-12-07
I just can't seem to get ubuntu and windows to cooperate. I have one harddrive partioned in half one for windows the other for ubuntu.i installed windows first, everythings great, then ubuntu... after grub takes over i always get error loading operating system. ive never been able to access my ubuntu and can still boot into windows with the help of ultimate boot cd. also I tried this before with lilo with similiar results.  any ideas?

---

### Post by atoponce on 2005-12-07
[quote=bslusser]I just can't seem to get ubuntu and windows to cooperate. I have one harddrive partioned in half one for windows the other for ubuntu.i installed windows first, everythings great, then ubuntu... after grub takes over i always get error loading operating system. ive never been able to access my ubuntu and can still boot into windows with the help of ultimate boot cd. also I tried this before with lilo with similiar results.  any ideas?[/quote] Sounds like your master boot record (MBR) is getting corrupted during install.  How are you setting up your Ubuntu partition, and how much hard drive space are we talking about here?

---

### Post by bslusser on 2005-12-07
its a 100gb drive, first 45 gb for windows, rest for ubuntu. for ubuntus partition it was 1.5gb for swap and the rest for root.

---

### Post by atoponce on 2005-12-07
Can you boot at all into Ubuntu with a command line present?

---

### Post by bslusser on 2005-12-07
Ive tried everything just to get to that but cant get any console. should i download the live cd?

---

### Post by atoponce on 2005-12-07
[quote=bslusser]Ive tried everything just to get to that but cant get any console. should i download the live cd?[/quote] Download and burn a Knoppix disc, rather than the live Ubuntu CD.  I learned earlier in these forums that Knoppix aoutmatically mounts your pratitions, and places them on the desktop, while the Ubuntu Live CD does not, and you would have to mount them manually (which really isn't that hard).  Once mounted, you should be able to fix your MBR, reboot, and boot both Windows and Ubuntu.

---

### Post by bslusser on 2005-12-07
turns out I was already downloading the ubuntu live cd so after that booted up nicely, i tried to run grub-install /dev/hde (happens to be my main drive) and i get an error that says:

/dev/mapper/casper-snapshot does not have any corresponding BIOS drive

i tried it with the --recheck option and still no go :(

---

### Post by bslusser on 2005-12-07
bump.  anyone have any ideas? i can access my ubuntu installation with the livecd but cannot install grub

---

### Post by atoponce on 2005-12-08
Can you post the results of "fdisk -l"?

---

### Post by mherring on 2005-12-08
I have had similar issues--I have solved it temporarily by making a boot floppy during install of Ubuntu.....When it asks to put Grub on the HD, just say "no"---then it will tell you that you have to put it on a floppy.
Same issue with 5.04

Search on my posts, and you'll find the other thread on this--including one suggestion I have not yet tried.

---

### Post by bslusser on 2005-12-08
Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        5602    44992552+   c  W95 FAT32 (LBA)
/dev/hde2            5603       11973    51175057+  83  Linux
/dev/hde3           11974       12161     1510110    5  Extended
/dev/hde5           11974       12161     1510078+  82  Linux swap / Solaris

---

### Post by bslusser on 2005-12-08
bump, anyone? i dont know how to fix my mbr with the live cd, nothing seems to work

---

