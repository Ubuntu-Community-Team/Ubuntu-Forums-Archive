---
title: "Using xubuntu, but want to try Ubuntu, have ubuntu cd"
date: 2009-03-25
forum: Desktop Environments
---

### Post by samsam_eli on 2009-03-25
I currently have xubuntu installed on my computer, but I have seen it mentioned that the desktop which follows the Ubuntu software is easier for former windows users.

I am a complete newbie in linux so use small words when explaining:-)
I want to try the Ubuntu without deleting anything from my computer, like it's done with windows. Only, I have a xubuntu running, but I don't want to delete that. Just try the Ubuntu.

Also, if i like the Ubuntu, I want to install that without loosing anything of my work on the computer. 

Can anyone help me? :-D

---

### Post by bigbencg on 2009-03-25
The only difference between xubuntu and ubuntu is the desktop environment, ubuntu uses Gnome.  Gnome can be installed along with Xfce, or KDE for that matter but will use about 1.2GB of HD space.  

To install Gnome open a terminal and enter the following command

```
sudo apt-get install gnome
```

Enter your password, and your terminal will fill with stuff and will ask if you want to proceed and use x amount space.  type y and the installation will commence.  Now you can walk away for a while.  Once completed log out, at the login screen there should be an option that says "Session".  Click session, Gnome should be listed, select Gnome and log in.  

Presto you are using "ubuntu"

Or you can just boot from the ubuntu CD and have it format the drive and install, but you will lose everything you have done in your current installation.

---

### Post by bigbencg on 2009-03-26
Did you try it?  Did it work?

Don't leave me hangin!

---

### Post by Snow Keld on 2009-03-27
you can also search for "ubuntu-desktop" under the synaptic package manager.


although, you being an ex-windows user i would suggest that xubuntu has no difference to the gnome desktop as far as making the switch over from windows easier.


what are the specs of your computer (processor/ram)

cuz xubuntu runs faster, i use it for this reason over any other, although i may go back to gnome once i buy a better comp.


ultimately it is up to you, but if you would like to take my opinion (if you are looking to try different versions of linux) to repartition your hard drive a bit...

you can do this by getting Gparted and using that.
given that your hard drive is large enough and that the partition your files are currently saved on is not too big...

remember not to touch the partition your files are saved on unless you back them up first.

make a partition big enough for your all your files using an ext2 or ext3 file system, then open a terminal and type in 'sudo thunar' and copy everything inside the home directory (but not home itself) to the new partition.. although thunar is not very good in my experience for detecting other partitions, i use nautilus in xfce ...

now you have all your files on the new partition, remember which partition it is and you can now make a boot/install disk with any distro of linux on it and install in.

when you install it do custom partitioning, select the partition that you made for your files and /home directory and choose the filesystem type that it is (installer should tell you, or you should remember from when you made it) and tell it to mount partition as /home, DO NOT tell it to format the partition, YOU'VE ALREADY DONE IT.
now you make a new partition thats large enough for the operating system (5 or 6 gigs for most, i'd recommend 8 gigs though) and choose the filesystem type, tell it to format the partition and tell it to mount as /


then you can continue to install, i've had problems with GRUB using both debian and red hat based distros on the same machine, just so you know (ubuntu is debian, so is knoppix, mint linux, and more).
you should make sure its debian before you choose a distribution, and i was confused by open suse, but dont be, it boots as if red hat and uses .rpm package files like red hat, it would not boot using the grub installed by a debian OS and its grub would not boot a debian OS.



now, using this setup, you choose your operating system in the grub menu but your filesystem, and all your user files stay the same (including user settings given they are looked for by the new system, like if you customize xubuntu and you then boot on mint linux xfce version your desktop will look the same, although applications may be very different pending on the OS.

_______________________________________________________

sorry for getting a bit complicated on you, but for a new linux user i would think that you should take a look at MANY linux distributions before choosing one permanently, i started out with mandriva and LOVED it, but after checking out other distrobutons i found what i like, right now i'm liking ubuntu best, but i have the newest full DVD install for knoppix and will be installing (the way i described above) it tomorrow to see if i like it better than ubuntu.
i came to ubuntu as my second distro and since then tried about 10 other ones, so far ubuntu still wins.

slower comp gets xfce
faster comp gets gnome
and i havent come to like kde yet, it seems so strange to me, even though i used it with mandriva as my first linux distro...

---

### Post by nebileix on 2009-03-27
Another option will be thru VirtualBox. It allows u to virtualize another operating system in the current one. You can get it from running the command > $ sudo apt-get install virtualbox-oseAfter that, just create a virtual hardisk and install as usual. If u need help, try to google it. Theres tons of help online.

---

### Post by samsam_eli on 2009-10-04
> **bigbencg said:**
> Did you try it?  Did it work?

Don't leave me hangin!

It didn't work. I got a long message with something about broken package.

The other suggestion didn't work either

---

### Post by XubuRoxMySox on 2009-10-04
Try this. Open a terminal and type

```
apt-get install ubuntu-desktop
```

After it has downloaded and installed, then log out. When you go to log back in, find "Options" and click on it, and select "Change Session." You can then choose Xfce (Xubuntu) or Gnome (Ubuntu).

-Robin

---

### Post by bagy on 2009-10-04
Insert ubuntu cd and boot...

---

