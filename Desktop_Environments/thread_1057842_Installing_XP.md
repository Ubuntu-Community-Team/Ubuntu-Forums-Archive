---
title: "Installing XP"
date: 2009-02-02
forum: Desktop Environments
---

### Post by addison.wilson on 2009-02-02
So, about a two months ago XP had a registry error and wouldn't start up and to my bad luck my copy of XP SP3 was scratched.  So, I decided to try out a Linux OS which lea me to start using Ubuntu.  Its been good and what not, but I do miss being able to play PC games effectively, cedga isn't compatible with everything yet and wine seem to have issues when it comes to playing games at max graphical settings.  So, I downloaded an .iso of XP SP3 (yes I have my original cd-key and no I refuse to pay another $300 for another copy of something I already bought).  My question is this, what do I need to do to turn the ISO I have to XP into a bootable CD so that I can install XP, and yes I know that Windows OS will not run on a non-main HD partition so I am going to have to reinstall ubuntu, but that is more or less painless since I have a bootable copy of ubuntu right next to me.

---

### Post by daniel014 on 2009-02-02
Try using Unetbootin from sourceforge.

Select the iso and it should make a usb bootable drive.

---

### Post by Zevik on 2009-02-02
First of all, please note that you will not have to reinstall Ubuntu if you partition your HD prior to install. Secondly, as long as the file is already in ISO format, you should just be able to burn it to a disc using Brasero (its in the repos and you should select the option to 'Burn Disc Image'). What you should do first is use GParted to properly partition your disc, then install XP on the new partition, then either re-install grub or use EasyBCD to reconfigure the XP boot record. Check out apcmag.com and look under the how-tos for an EXCELLENT guide on dual booting.

---

### Post by kbutcher5 on 2009-02-02
In case you have trouble setting up dual boot, I made this guide a good while back. The general stuff still apply's to grub though, happy hunting :)
[http://wiki.archlinux.org/index.php/Windows_and_Arch_Dual_Boot](http://wiki.archlinux.org/index.php/Windows_and_Arch_Dual_Boot)

As for the disc, brasero or unetbootin, would be my suggestions aswell, though I would go with unetbootin if you have usb 2.0 support (it's faster, is all).

---

