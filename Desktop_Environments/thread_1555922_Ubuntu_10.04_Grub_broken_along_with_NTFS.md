---
title: "Ubuntu 10.04 Grub broken along with NTFS"
date: 2010-08-18
forum: Desktop Environments
---

### Post by DaGeek247 on 2010-08-18
First, I had set up Ubuntu 10.04 the way I wanted it. I had it set up like this:

80 GB Drive:
39 GB Ubuntu
41 GB NTFS (for a later windows install)

It was all good. I then created a slipstreamed windows install cd, for installing windows (I have the key, so its legal.) I created the slipstreamed CD because the old one was broken. I rebooted the computer and started the windows install. But unfortunantly I have two CD/DVD drives, and it installed from the broken CD. (freezes during install prosses)

Now, I am stuck with broken windows AND no grub to boot into Ubuntu.

How do I format the NTFS partition from the Ubuntu live CD for a clean install?
then after windows is running, I want to install grub so I get both OSes.
How do I reinstall grub?

---

### Post by DaGeek247 on 2010-08-18
bump

---

### Post by stinkeye on 2010-08-18
Format from the live cd using gparted.
Install windows first then install Ubuntu.
Ubuntu will pick up your windows install and add it to the grub boot menu.

If you install windows after Ubuntu,
see this post for reinstalling grub from the livecd when windows wipes it out.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=9702777&postcount=5[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9702777&postcount=5")

---

### Post by DaGeek247 on 2010-08-18
says: (in reply to the mount procedure in the link)
> 
Mount: wrong fs type, bad superblock on /dev/sda2, missing codepage or helper program, or other error in some cases usefull info is found in syslog - try dmesg | tail or so

what do i do?

--edit-- (i started thinking)
I opened gparted and checked the files system stuff, the /dev/sda2 is an encompasment of like three different file systems (for me) so i did:
```

sudo mount /dev/sda5 -t ext4 /media/sda2

```
and it mounted fine.

after mounting i simply did the rest of the code, and rebooted. thankfully, it worked. now I will try the slipstreamed window xp install, and see where it goes!

---

### Post by stinkeye on 2010-08-19
Your supposed to substitute all the [COLOR="Magenta"]sda2[/COLOR] entries 
with the partition that ** fdisk -l** tells you where Ubuntu is installed.

---

### Post by DaGeek247 on 2010-08-19
llol, then I guess i might not have been thinking. oh well, it still worked.

---

