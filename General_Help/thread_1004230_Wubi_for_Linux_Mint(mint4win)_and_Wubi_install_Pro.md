---
title: "Wubi for Linux Mint(mint4win) and Wubi install Problem"
date: 2008-12-07
forum: General Help
---

### Post by merlwiz79 on 2008-12-07
I have used wubi to compile mint4win, that will come out with Linux Mint 6 Final.
**Wubi and mint4win installs:**
Yes, you can install Ubuntu with wubi and Linux Mint with win4mint on the same Windows installation. (**only tested in XP**)
It will require work but you can do it.
1st the last one to be installed will overwrite the others entry in windows boot manager.
2nd you can't add the others entry back.(that I know of at this time)
3rd if you uninstall one it removes both the entry from windows boot manager and the mbr files.(can't boot into the installed distro)

**How to get both installs work:**
Install 1 then reboot into it to complete the install.
Install the 2nd and reboot and let it complete the install.
Edit the last installed menu.lst to include the entry from the other one installed.
Select the entry in Windows boot manager that loads grub4dos.
Hit Esc and select the distro you want to run.

**Fix Windows boot manager after a Distro is uninstalled:** (**XP Only**)
1st copy these files to C:\ and any other drive a version Windows is installed on.
mint4win:
{DRIVE}:\mint \winboot\wubildr.mbr
{DRIVE}:\mint \winboot\wubildr
wubi:
{DRIVE}:\ubuntu \winboot\wubildr.mbr
{DRIVE}:\ubuntu \winboot\wubildr

XP
Add c:\wubildr.mbr="DISTRO_NAME" to boot.ini
Example: c:\wubildr.mbr="Xubuntu"

Vista:
Try EasyBCD --> Add entry --> Linux --> Wubi
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by krisskross on 2009-02-19
Unfortunately the install of Mint6 32bit won't do.
I copied the mint4win from the iso to C:\ and put the iso into the mint\install folder where the download should go.

Installation starts, box reboots and on it went. But:
It stops after partitioning. Close before finishing the install procedure it crashes with an installation error.

I also tried mint4win --32bit -same result

To verify it's not the box causing the trouble, I tried xubuntu with wubi810 which runs it's installation flawless.

I guess there must be a bug somehow in the mint4win wubi. Could you provide a fixed version and as interim solution a way to get the mint4win do what it is suppsoed to do, please?

---

