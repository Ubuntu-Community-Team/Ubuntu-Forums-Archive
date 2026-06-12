---
title: "How to restore/repair permissions on root files (I messed them up by mistake)"
date: 2005-12-15
forum: General Help
---

### Post by Mguel on 2005-12-15
Hi, yesterday I made ubuntu unusable by a mistake (changed permissions on all files on root)

I was changing permissions of some files I have copied from a ntfs partition, so I was at **/home/user/ntfs-files** and used the **chmod 660 ***

As I forgot to use sudo I received a permission denied error, so I repeated the command with sudo
**sudo chmod 660 ***
But didn't realize that I was no longer on /home/user/ntfs-files :confused: , but on the **root directory**... :shock: 

After that, panels on gnome closed and nothing responded well... 

Rebooted and couldn't login... I got an error about /bin/bash (as far as I remember). So now I'm back on windows while posting this :cry: 

I hope there is a way to repair the mess (using the install cd, or with other method), but I hope I don't have to make a clean install from 0.

Best regards,
Mguel

---

### Post by varunus on 2005-12-15
Can you try rebooting in "rescue mode" (its an option in GRUB) and see if that works?  If it doesn't, you'll have to get a live CD...

Boot from the live cd, mount your partition, and change permissions...

Huh, I'd suggest just reinstalling...You could easily just mess things up even further with permissions, as certain things need to have certain permissions...

You could try changing everything to 777.

---

### Post by schilcha on 2005-12-15
Wow, that's a pretty effective way to stab your system!

I guess, you can try to boot from live CD to fix the basic permissions (at least in /bin /etc /lib /boot) so you can boot at least a minimal (rescue) system. Just take the permissions from the live CD as template.

I would then try to reinstall all packages with apt-get (I'm not really a master of apt-get, so I can't tell you more that to read the man-page) and hope that the permissions are corrected in this way. (just to make sure, backup your /etc directory, as your settings might get lost)

However, varunus is perfectly right that (depending on your configuration) reinstalling might be the cheapes and safest approach.

Good Luck!

P.s. There are several ways to effectively kill your system -- I've already discovered some of them ;-)

---

