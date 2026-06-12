---
title: "USB Unmountable"
date: 2009-01-07
forum: General Help
---

### Post by Spamiser on 2009-01-07
hello all, i am new to the site and am practising Unubtu/Linux in Uni. This is my first year of study, so go easy on me lol

i have also been studying basic commands for the last hour on my laptop lol


heres my problem, when im in uni i put in a USB pen drive, when i try to topen it, it says its Unmountable (try opening it through the GUI not the CLI).....however, a few restarts of the comp fixes this lol.......but id love to learn how to fix this problem and instead open it through the CLI

all help is welcome :)

thanks,
dan

---

### Post by cmnorton on 2009-01-07
What command are you using to mount the drive on the command line?

---

### Post by Spamiser on 2009-01-07
> **cmnorton said:**
> What command are you using to mount the drive on the command line?

i didnt try the command line, im too new :(

im trying to access it by the GUI, so through the computer file


but would like to know a few commands that would open it without a problem, if you dnt mind :)

---

### Post by cmnorton on 2009-01-07
> **Spamiser said:**
> i didnt try the command line, im too new :(

im trying to access it by the GUI, so through the computer file


but would like to know a few commands that would open it without a problem, if you dnt mind :)

I've clearly got to research the message, because CLI stands for command line interface.

---

### Post by Spamiser on 2009-01-07
> **cmnorton said:**
> I've clearly got to research the message, because CLI stands for command line interface.

yeah, CLI.....i guesse i should be saying Terminal lol

any ideas how to topen it via the Terminal?

---

### Post by cmnorton on 2009-01-07
On your menus, perhaps Applications, find the icon for terminal and put it on a bar or your desktop. You'll use it.

You need a physical mount point. Start with /media. See what's there already, but if you need to create one for this memory stick:

sudo mkdir /media/usb_mem

You'll need to know the file system that's on it: If you are never going back and forth between Linux and Windows, put ext2 on the stick. I've been told it's nutzy to have a journaling file system on a USB stick. If FAT32 or NTFS is the file system, then just try

You should enter df to make sure /dev/sdb1 is not already in use. Assuming this is your only usb device 

sudo mount /dev/sdb1 /media/usb_mem

In this case, I did not have to provide the file system type. It just mounted. You can use any mount mount that's under /media, unless it is in use. I'm a believer in having several unique mount mounts.

---

