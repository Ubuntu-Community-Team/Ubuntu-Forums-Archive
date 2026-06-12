---
title: "Choose S.O. on reboot"
date: 2006-09-23
forum: Desktop Environments
---

### Post by rockz on 2006-09-23
When i used suse (kde) i had a option to reboot directly on a specified SO without choose it on grub. Can I do that in Ubuntu? There is a software that do this or some special configuration?

---

### Post by bernied on 2006-09-23
What's an SO? Do you mean OS - operating system?

---

### Post by rockz on 2006-09-23
err... my mistake, its O.S. (operating system)

---

### Post by bernied on 2006-09-23
Are you trying to dual-boot? If you give information on the following:
- the other OS that you want to boot
- the disk setup (how many disks, how many partitions on each, where each OS is on the disks) - if you don't know this, post the output of 'sudo fdisk -l'
- your current boot configuration - post the output of 'cat /boot/grub/menu.lst'
then someone here might be able to help you

---

### Post by rockz on 2006-09-23
I can select other OS on grub, but i want to reboot the system directly to other OS.

---

### Post by skymt on 2006-09-23
You can use the "grub-reboot" command, like this:```
sudo grub-reboot 1
```That command would, on my system, reboot me to recovery mode (the second entry in my grub menu). The number (1 in this case) specifies which grub menu entry you want to choose, counting from zero.

EDIT: As far as I know, there's no way to do this from a GUI. Someone get the GDM developers on the line!

---

### Post by drlock on 2006-09-23
The grub-reboot command would be great if it worked.  The best I can tell it has been disabled. I have tried a number of times:
sudo grub-reboot 8
and
sudo grub-reboot 7

It reboots, but always defaults to 0.  Any ideas?

---

### Post by rockz on 2006-09-23
This command change the grub menu order? Because i cant use grub menu (usb keyboard problem) and i want to start ubuntu in next reboot, after i using grub-reboot (number).

---

### Post by Ramses de Norre on 2006-09-23
I just wrote a little script to give you a GUI to it: ```
#!/bin/bash

OS=`zenity --list --radiolist --text "Select Operating System" --title "Grub reboot" --column "" --column "" FALSE Ubuntu FALSE "Recovery Mode" FALSE Windows`

case $OS in
    Ubuntu)
        grub-reboot 0
        exit 0
    ;;
    Recovery\ Mode)
        grub-reboot 1
        exit 0
    ;;
    Windows)
        grub-reboot 7
        exit 0
    ;;
    *)
        echo "An error occured, check syntax"
        exit 1
    ;;
esac
exit 0

```

But if grub-reboot doesn't work this wont work either.. You'll need to change it a bit to fit your system.

---

### Post by knn on 2006-09-25
This is why grub-reboot doesn't work:

```
#!/bin/sh -e

echo <<EOF
This cannot run! Support removed from last release.

Unfortunately, when GRUB was update to 0.97 version, the available
patch to add support to this utility to run wasn't update.
EOF
exit 1

```

These are the first few lines of the script. The rest is there, but it won't work :(

---

### Post by skymt on 2006-09-25
Well. That's shoddy. :confused: 

Why remove a useful feature? Why keep the script anyhow? It makes no sense at all.

---

### Post by knn on 2006-09-25
It seems the patch didn't work with the updated grub.

---

### Post by bernied on 2006-09-26
There's another way to get around this problem. It's a bit messy but it works for me.

I have a dual-boot system, and I want to leave the default boot option as windows for my linu-phobic housemates, so it's good to have a setup where I can choose to boot linux as part of the windows shutdown process.

In my /boot/grub/menu.lst I have this:
```
default 0
timeout 0
hiddenmenu
title Reload menu
root (hd0,0)
configfile /grubmenu.std

```Where (hd0,0) is my windows partition.
So this loads essentially a different menu.lst from the Windows root directory. I keep two different versions of this file, and copy the one to grubmenu.std I want to load, just before shutdown, using a DOS batch file.

The only thing is, you have to copy the menu.lst with the windows default back to grubmenu.std, once you've started linux. So I have a short bash script called by rc.local to do this at linux startup.

So, it's a bit of a hack, but it does work nicely.

---

### Post by skymt on 2006-09-26
Now *that's* just cool. Great hack!

---

