---
title: "windows drives in thunar file manager"
date: 2008-11-01
forum: Desktop Environments
---

### Post by jittopjose on 2008-11-01
hello friends
i have installed xubuntu-desktop in existing ubuntu installation. now i cant see the windows partitions. where can i find that. previously i could see it in 'computer folder'. but could not see computer folder in xubuntu. any idea about that?
thank you
jittos....

---

### Post by jittopjose on 2008-11-03
anybody have any idea about it?

---

### Post by efpc2003 on 2008-11-03
i'm using xubuntu 8.04.1 and, the system is up to date (update-manager says...) and i have the same problem, and i don't know what to do, the problem start 10 days ago +/-...
fstab? mtab? ¿?¿?¿?¿?¿?


**_SOLVED!!!!!!!!!!!!_**

First, read this... "Re: How to access other drives in Xubuntu? 
download ntfs-config, search for: "ntfs configuration tool", ntfs-3g must be installed, if don't... install it (I'm using xubuntu 8.04.1 and it works)"

with sudo thunar i changed permission read/write acces to "my self/own user" and then go to Application->System->ntfs configuration tool (ntfs-3g)... verify "2 check boxes" and restart

---

### Post by e_1_off on 2008-11-04
Almost same story. I use Ubuntu at home, together with Windows istalled by wubi. And I used to have an Ubuntu on flash, installed by Unetbootin. Both easily mounted Windows' NTFS drives. But when I put Xubuntu on flash, it did not found and so could not mount Windows' drives. Though, when you open the "search" window, these drives can be seen there as the places to search in. I wanted to install Xubuntu at my working computer, it has less then 256 Mb RAM. But now I doubt. Can anyone tell me, would it see and mount the Windows' drives if installed by wubi.

---

### Post by e_1_off on 2008-11-05
OK, I've found the way to reach them. This is just a GUI problem. Possibly you can mount them by console, but I am VERY new to Ubuntu and Linux, so in console commands I am absolute zero. But there is a way to reach them by GUI. As I said, they are visible in the search program (it is called Catfish). You start it from the places menu (search item) or from the applications menu (applications>accessories>catfish). Then go to the search location dropdown list and choose "other" option. There chose the drive you need to access and open it. It will open, show its' contents AND after that it can be found in the "media" folder where it is supposed to be. I've started Xubuntu from the live flash, so I can't say whether the effect is permanent, of it should be done every time you start the system. Anyway, I think it's a glitch in GUI and it will be corrected by upgrades.

---

### Post by Nano_ext3 on 2009-03-03
Correct, the slimmed down XFCE (remember thats what it was designed for) interface does not show windows drives under places.  I suggest manually mounting the drive , or if more than one, created a script file, email me if you need help making that.  

Basic Syntax is:

sudo su

mount /dev/sda# /mnt/


*WHERE # will be your NTFS partition.  This can be found out by running "fdisk -l" while being root, your windows partition(s) will have NTFS file system in the category under filesystem.  Knowing the size of your partition or drive is a plus too.  (Note: sometimes sda can be hda)

*you can also mount the drive to a folder in mount.  While root, do "mkdir /mnt/WindowsDrive" then mount "/dev/sda# /mnt/WindowsDrive"  I say this because if you mount more than one drive to mount, your going to have things all messed up and garbled, if it even lets you get that far.

if it wont mount, try forcing it by appending "-o force" to the end

---

### Post by hurt138 on 2009-03-03
XFCE does not manage devices the same way gnome does and simply assumes you are going to handle that stuff on your own.

If you still want the auto features of gnome and use the interface of XFCE you may want to try having it load the gnome settings daemon.

You should be able to do this by putting a file in your .xinitrc file with the following:

```

gnome-settings-daemon &

```

---

