---
title: "Dual Boot 9.10 with Win XP"
date: 2010-03-01
forum: Desktop Environments
---

### Post by raunhar on 2010-03-01
I amusing my PC with dual boot (Ubuntu 9.10 with WIn XP). Till Ubuntu 9.04 there was no problem as when ever I had to reinstall WIn XP, I would use Grub Boot CD to reinstall Grub.
But what is the procedure for GRUB 1.97 Beta 4.
In case of Win XP reinstall, can I use the old GRUB bootable CD or do I have to create a new one for GRUB 1.97. If yes, then from where can I get it.

---

### Post by oldfred on 2010-03-01
If you upgraded from 9.04 you still have old grub and need to use an older version of a liveCd to reinstall grub. If you did the clean install you can use the liveCD you downloaded to reinstall grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Windows boot loader basically only looks for a boot flag on a partition adn jumps there. You can also download a basic boot loader for windows from linux.

Restore basic XP style boot loader to sda (not lilo boot loader)
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by raunhar on 2010-03-02
9.10 was a clean install.
Now I am planning to reinstall 9.04 and then upgrade.

---

### Post by Hero of Time on 2010-03-02
Using the old Grub is not a good idea. It's best to just stick with Grub2. You can fix your Grub2 bootloader the same way you used to do the old Grub loader. Not much has changed for that part.

See [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7) for example, method 2) is what you will use.
This [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1306488](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1306488) will give you some more info too.

---

