---
title: "Unmounting or Hidding Hard Drives"
date: 2008-04-13
forum: Desktop Effects &amp; Customization
---

### Post by Justin Holland on 2008-04-13
Ok, I am a complete newbie to the environment of Linux.  I've always been a user of Microsoft OS (though never a big fan).  I'm rusty, yet familiar with DOS, if anybody still remembers that.  Anyway, I digress.

I have an HP Pavilion laptop DV6000 series, which I have just installed Ubuntu 7.10 in dual boot with Windows XP MCE.  My problem is I have four drives on the desktop and I only wish to have the shared drive partition.  I have located the fstab file but when I edit out the partitions I don't want, the OS says I don't have the privilege to save it.  How do I go about fixing this?  Also, how can I rename the drive I want to keep mounted so that it says Shared Drive?

Please, would somebody give me step-by-step, directions that a toddler could follow.

-= Justin =-

---

### Post by SEMW on 2008-04-13
> **Justin Holland said:**
>  I have located the fstab file but when I edit out the partitions I don't want, the OS says I don't have the privilege to save it.  How do I go about fixing this? 
You need to edit the fstab file with root privileges.

To do this, open a terminal (Applications -> Accessories -> Terminal), and copy and paste into it:
```
gksudo gedit /etc/fstab
```
Type in your password, and edit it as you did before.

By the way, it might be a good idea to just comment out the lines in fstab you don't want rather than delete them, in case you want them again in the future.  To do that, just put a hash ('#') at the beginning of each line you don't want.

Oh, and before you start, make a backup of fstab (just in case), by entering into ther terminal: ```
sudo cp /etc/fstab /etc/fstab.bak
```

---

### Post by Red-Shield on 2008-04-13
well it sounds like you need super user permision when editing those types of files

---

### Post by Justin Holland on 2008-04-13
Thanks, that was quite easy and painless.  I thought I had to log in under root to be able to make the changes and I couldn't figure out how to do that.  I didn't try, but is it possible to rename the one drive in fstab?

-= Justin =-

---

### Post by SEMW on 2008-04-13
> **Justin Holland said:**
> I didn't try, but is it possible to rename the one drive in fstab?

To tell you the truth, I didn't answer that part because my experiences have been a bit self-contradictory.  I've mounted two of my hard drives in folders that are named as I wanted in fstab, so the relevant part of fstab looks like:
```
/dev/sda2       /media/Transfer   vfat     defaults  0     0
/dev/sda1       /media/Data     ntfs-3g  defaults 0 0 

```
Sure enough, the drive mounted in 'Data' drive shows up (in the Places menu and on the desktop) as "Data".  But, strangely, the one mounted in "Transfer" shows up as "21.5GB Media", rather than "Transfer"!

A solution that definitely will work would be to create a shortcut from where the drive's mounted to your desktop.  Then, since it's a shortcut, you can rename it freely.  To do that, go to /mnt or /media, wherever your drives are mounted (check in fstab if you're not sure), and drag and drop the drive you want to create a shortcut to to the desktop, *whilst holding down Ctrl and Shift*.  Then you can name the resulting shortcut whatever you like.

---

