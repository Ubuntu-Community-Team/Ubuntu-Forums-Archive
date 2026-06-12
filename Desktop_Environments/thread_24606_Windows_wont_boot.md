---
title: "Windows wont boot"
date: 2005-04-07
forum: Desktop Environments
---

### Post by Runewalsh3 on 2005-04-07
Hi, I recently dual-booted ubuntu Hoary and Winxp. I have set up GRUB as the bootloader, but when I try to select MS windows, it just hangs. The full text is:
Booting 'Windows XP Home Edition'
root (hd0,0)
Filesystem type unknown, partition type 0x7
save default
make active
chainloader +1
_ <- It blinks

WinXP partiton is active, and I think it's bootable but I'm not sure. It's really important that I have access to XP right now, I have homework and a couple of projects that I need to print out on my canon i450, which as far as I know is windows/mac compatable only (checked on linuxprinting.org)

---

### Post by Xian on 2005-04-07
I can't say what the actual problem is, but if you need to get into XP right away then do this:

Boot from the Windows XP CD, press the key "R" in the setup in order to start the restoration console. Select your Windows XP installation from the list, and enter the administrator password. Enter the command "FIXMBR" at the input prompt and confirm the next question with "y". Finally, use "exit" to restore the computer.

You will have to reinstall grub later on to set back up your dual-boot config.

---

### Post by Apex on 2005-04-07
[QUOTE=Runewalsh3]Hi, I recently dual-booted ubuntu Hoary and Winxp. I have set up GRUB as the bootloader, but when I try to select MS windows, it just hangs. The full text is:
Booting 'Windows XP Home Edition'
root (hd0,0)
Filesystem type unknown, partition type 0x7
save default
make active
chainloader +1
_ <- It blinks

WinXP partiton is active, and I think it's bootable but I'm not sure. It's really important that I have access to XP right now, I have homework and a couple of projects that I need to print out on my canon i450, which as far as I know is windows/mac compatable only (checked on linuxprinting.org)[/QUOTE]
 Go into your bios and change the hard drive mode from Auto to LBA.  Its a grub bug.  Hopefully I caught you before you took a Xian's advice....

---

### Post by Runewalsh3 on 2005-04-08
Thanks a lot, I will ty this when I get home. Will switching my bootloader to LILO make it work? I dont have any particular preference as far as bootloaders go.

---

### Post by Apex on 2005-04-09
[QUOTE=Runewalsh3]Thanks a lot, I will ty this when I get home. Will switching my bootloader to LILO make it work? I dont have any particular preference as far as bootloaders go.[/QUOTE]

I would stick with grub.  I have no real rationalization for it, aside from it stays true to the native ubuntu.  Lilo would probably be fine, but only old timey distros are still loyal to lilo.  Its all about progress baby! \\:D/

---

### Post by bored2k on 2005-04-09
[QUOTE=Runewalsh3]Thanks a lot, I will ty this when I get home. Will switching my bootloader to LILO make it work? I dont have any particular preference as far as bootloaders go.[/QUOTE]
 There is no reason why you shouldn't give it a shot. If it doesnt, go back to grub ASAP ;).

---

### Post by c_dog on 2005-04-09
[QUOTE=Runewalsh3]Hi, I recently dual-booted ubuntu Hoary and Winxp. I have set up GRUB as the bootloader, but when I try to select MS windows, it just hangs. The full text is:
Booting 'Windows XP Home Edition'
root (hd0,0)
Filesystem type unknown, partition type 0x7
save default
make active
chainloader +1
_ <- It blinks

WinXP partiton is active, and I think it's bootable but I'm not sure. It's really important that I have access to XP right now, I have homework and a couple of projects that I need to print out on my canon i450, which as far as I know is windows/mac compatable only (checked on linuxprinting.org)[/QUOTE]

Couple of things you might try to fix this. Make active is a one word command in GRUB  'makeactive'. Also you might want to use 'rootnoverify(hd0,0)' since if your XP is on an NTFS partition, GRUB not going to be able to verify it anyway.

---

