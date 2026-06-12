---
title: "Help Grub Error!!!!"
date: 2005-12-20
forum: General Help
---

### Post by squintv on 2005-12-20
I installed Ubuntu on its own partition and use grub to boot into that or windows, but the other day i hibernated it and while it was hybernating it lost power, and when i tried to boot it back up, it came up as a Gurb error 5. so now my comp is locked.... HELP ME PLEASE!!!!

---

### Post by Gurgeh on 2005-12-20
Tried pressing ESC to get the options? Tried a bootdisk?

I pray to god someone can help u :S

---

### Post by squintv on 2005-12-20
ive pushed everything, but no help, and whats a good way to acquire a booot disc? all i can find is iso's ove like 5 discs for SP2 or something, i just want a single disc thing...and all of my boot discs are in alaska...

---

### Post by squintv on 2005-12-21
anyone else?

oh and by the way.. i just installed linux on my ipod!

---

### Post by Emerzen on 2005-12-21
If you have your install disk handy, you can try the following:

insert disk and reboot-> at prompt type "rescue" ->

mount the disk and partition that has your Ubuntu root filesystem when given the choice -> when you get to the next prompt type ->

grub-install /dev/hda  (if you have SATA drives change the h to and s)

This will reinstall GRUB to your MBR configured to the menu.lst that is in /boot/grub/menu.lst file (the one you had prior the failure).  

-----------------------------------------------------------------------

If that doesn't fix your problem you may have lost some critical data during the power outage (hibernate causes RAM to temporarilly be written to the harddisk for fast resume).  You could try booting up a LiveCD and fishing around your Ubuntu partition to detect any errors.  Probably a better idea would be to search these forums for someone more knowledgeable in that area.  At worst, you should be able to recover your important files from your Ubuntu partition and then do a clean reinstall.

---

### Post by squintv on 2005-12-21
ok, i am DLing the iso for ubuntu right now, since my discs are in alaska. but the problem is, i really really need the stuff from the WINDOWS part of the HD. i was thinking i could get a replacement HD, install windows, and convert my current one into an external and then get the files off of it, and just have one for linux and one for windows, just switch as needed.... what do ya think?

---

### Post by squintv on 2005-12-21
and is there any way i can go without having to download that HUGE FILE, im on dial up out here in the boonies, it would literallt be faster to get it shipped.... no joke!

---

### Post by briancurtin on 2005-12-21
man it must suck to be on dialup. i downloaded the Gentoo ISO, then CentOS 4 DVD ISO, then realized i dont have my blank DVDs here so then i downloaded the 4 individual CentOS 4 discs, all within about 3 hours haha

---

### Post by Emerzen on 2005-12-21
[QUOTE=squintv]ok, i am DLing the iso for ubuntu right now, since my discs are in alaska. but the problem is, i really really need the stuff from the WINDOWS part of the HD. i was thinking i could get a replacement HD, install windows, and convert my current one into an external and then get the files off of it, and just have one for linux and one for windows, just switch as needed.... what do ya think?[/QUOTE]

If you want to buy a new HD, install Windows, and convert your current drive to an external drive...that is a piece of cake (except to your pocketbook I suppose).  I had an older computer that died and I did exactly what your talking about.  I pulled out the old HD, popped it in an ADS case (WalMart ~$30) that turned it into an external HD via USB.  Windows mounts it as such and it is easy to pull your old files off then.

There is one catch however: Windows Activation.  In theory, Windows creates a "fingerprint" of your hardware when it's activated.  If you change your hardware configuration too much, it may impede being able to activate Windows.  This is in theory.  Personally, the only configuration change I haven't made to my PC is to change the motherboard, and I've never had a problem activating my Windows copy.  But, you should keep it in mind.  I reinstall Windows on average every 2-3 mo's w/o trouble by the way.

---

