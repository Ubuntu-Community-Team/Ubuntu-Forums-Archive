---
title: "GRUB write failure - please, help"
date: 2005-11-25
forum: Desktop Environments
---

### Post by OCBlue on 2005-11-25
Hi, I'm new to Ubuntu ant to Linux too (used Slackware long ago - forgot everything :) )

Tried to install Ubuntu to my P4 with two S-ATA drives. Ubuntu partition should've been #1 on sdb (?) or disk two. First partition on disk one has WinXP. 

Booted from CD, everything went OK until GRUB write. It just hung (?). No error message.

Reloaded, tried again - had to create partitions and reinstall Ubuntu (why?). Totally confused now. 

Sorry if it all sounds stupid - I probably got used to easy and automatic installs <sigh>.

---

### Post by teaker1s on 2005-11-25
don't panic and don't give up look at these
[here]("https://wiki.ubuntu.com/FakeRaidHowto")

and

[here]("http://ubuntuforums.org/showthread.php?t=92861&highlight=ubuntu+sata")

---

### Post by OCBlue on 2005-11-25
Oh, my...

Well, thanks for suggestions, but it didn't work. I fished out my old PS/2 mouse and disconnected all USB devices. Didn't help. Then I restarted and disabled the whole USB thingie in BIOS, but that didn't help either. 

If anyone would have any idea...

Here some info about my system:
Processor - Intel Pentium 4 3.0 GHz (Socket 478) Northwood D1
FrontSide Bus - 200 MHz
Memory - 1536 MB PC3200 DDR-SDRAM 200 MHz
Motherboard - AsusTeK P4P8X - Intel 865P+ICH5 - AGP 3.0
BIOS - American Megatrends (AMI)
Video - nVidia GeForce FX 5600XT (256 MB, AGP 8x)
Monitor - Sony CPD-200SFT
Drive - S-ATA ST380013AS (76 GB) and S-ATA ST3300831AS (279 GB)*
Network - 3Com Gigabit LOM (100 Mbps)

* -The first partition on this is supposed to have Ubuntu, the first partition on smaller disk has WinXP.

Hope somebody helps me. It ain't critical, but there's so much of that weekend :)

---

### Post by OCBlue on 2005-11-26
Hello, anybody? Hasn't it happened to anyone else? I was unable to find any other suggestions on the topic.

---

### Post by psusi on 2005-11-26
[QUOTE=OCBlue]Hello, anybody? Hasn't it happened to anyone else? I was unable to find any other suggestions on the topic.[/QUOTE]

Try checking the other terminals for more detailed error messages.  Press alt-left arrow or right arrow to cycle through them.  One of them probably will show more detailed output as to what is going wrong.

---

### Post by paddyg on 2005-11-26
[QUOTE=OCBlue]Hi, I'm new to Ubuntu ant to Linux too (used Slackware long ago - forgot everything :) )

Tried to install Ubuntu to my P4 with two S-ATA drives. Ubuntu partition should've been #1 on sdb (?) or disk two. First partition on disk one has WinXP. 

Booted from CD, everything went OK until GRUB write. It just hung (?). No error message.

Reloaded, tried again - had to create partitions and reinstall Ubuntu (why?). Totally confused now. 

Sorry if it all sounds stupid - I probably got used to easy and automatic installs <sigh>.[/QUOTE]
you should have sda and sdb...

Could you post your sata partitions. Here's mine
```
sda1 ntfs windows
sda2 extended
sda5 ext3 /boot
sda6 swap
sda7 ext3 /
sda8 ext3 /home
sda9 ext3 /usr
```
Where did you try to install Grub?

---

### Post by OCBlue on 2005-11-26
Well, I only remember layout in "windows" terms:
Disk 1 - partition 1 ntfs (windows boot), partition 2 ntfs
Disk 2 - partition 1 ext3 (ubuntu), partition 2 swap (ubuntu), partition 3 ntfs, partition 4 ntfs. 
I did not try to install Grub anywhere, I mean it probably tried to go the place it's supposed to (default one). I'm installing from Ubuntu 5.10 CD.

---

### Post by OCBlue on 2005-11-26
OK. More info as PSUSI suggested. Did installation attempt again. Hung at the same exact place. Did alt-arrows. Here are a few last lines from visible terminals (consoles?):

...
[lots of stuff like "main-menu [4946]: DEBUG: with]
Menu item 'grub-installer' selected
configure grub-installer, status:2
cinfigure kernel-installer, status:0
virtual package kernel-installer
configure created-fstab, status:0
virtual package created-fstab
(nothing after this)

and another one

...
suggested packages:
     grub-doc grubconf
the following NEW packages will be installed:
     grub
(end)

That's it. Any ideas? I'm totally lost. But glad to learn all the things Ubuntu installs by heart (already) and this clever thing of alt-arrows during install. Still no working Ubuntu on my system, though...

---

