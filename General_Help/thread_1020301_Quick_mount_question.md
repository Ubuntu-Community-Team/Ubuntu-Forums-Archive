---
title: "Quick mount question"
date: 2008-12-24
forum: General Help
---

### Post by And6ate9 on 2008-12-24
How do I mount a harddrive without that darn mount icon on the desktop?

---

### Post by koffeinöverdos on 2008-12-24
There's surely a more sophisticated, exact way to fix it, but you can do it with [Ubuntu Tweak]("http://www.getdeb.net/app/Ubuntu+Tweak") from getdeb.

---

### Post by adult swim on 2008-12-24
if you arent sure of the drive's label you can run from a terminal ```
sudo fdisk -lu
``` an easy way to determine which one it is, is by the drive size.  they will be labeled as /dev/sda, /dev/sdb etc.  once you figure out which drive you want to mount, enter in the terminal ```
sudo mkdir /mnt/drive

sudo mount /dev/XXX /mnt/drive
``` where xxx is going to be sda, sdb, sdc, whatever the drive it is your are trying to mount.  you can then find the mounted drive in nautilus by navigating to /mnt/drive

---

### Post by And6ate9 on 2008-12-24
so the drive has to be mounted in the mnt folder in order for the icon not to show up on the desktop?

---

### Post by adult swim on 2008-12-24
not neccessarily.  i think i may have misunderstood your original post.  are you having trouble mounting the drive because there is not icon on the desktop, or do you want to get rid of the icon on the desktop?

---

### Post by logos34 on 2008-12-24
> **koffeinöverdos said:**
> There's surely a more sophisticated, exact way to fix it, but you can do it with [Ubuntu Tweak]("http://www.getdeb.net/app/Ubuntu+Tweak") from getdeb.

Just to be perfectly annoying, here's the more sophisticated, exact way:

> gconftool-2 --type boolean --set /apps/nautilus/desktop/volumes_visible "false"

I've been saving that one up for a week...

---

### Post by And6ate9 on 2008-12-24
I just want to get rid of the icon. It bugs me.

Adult swim eh? hope it's not crowded in that Sealab.

thanks Logos. Just out of curiosity, what else have you been saving? Would it be a way to specifically hide a partical mounted drive icon? :P

---

### Post by koffeinöverdos on 2008-12-24
> **logos34 said:**
> Just to be perfectly annoying, here's the more sophisticated, exact way:



I've been saving that one up for a week...

Oh right... gconf. I'm an idiot how did I not think of that.

---

### Post by adult swim on 2008-12-24
the sealab is fine, its meatwad im worried about!
editing your fstab to mount it in /mnt will take the drive off of your desktop and out of the places shortcuts in nautilus.  using gconf as logos suggested will remove all of them off of your desktop but i think preserve the shortcuts in nautilus.  you may try to mount the drive in /mnt with a hidden foldername like /mnt/.drive but anyone who was looking for it that had any knowledge of hidden files could find it.

---

### Post by logos34 on 2008-12-24
> **And6ate9 said:**
> 
thanks Logos. Just out of curiosity, what else have you been saving? Would it be a way to specifically hide a partical mounted drive icon? :P

seriously though, did it work for you?  It clears mine--everything except the /home folder icon and launchers

---

### Post by Logan 1229 on 2009-01-25
> **adult swim said:**
> if you arent sure of the drive's label you can run from a terminal ```
sudo fdisk -lu
``` an easy way to determine which one it is, is by the drive size.  they will be labeled as /dev/sda, /dev/sdb etc.  once you figure out which drive you want to mount, enter in the terminal ```
sudo mkdir /mnt/drive

sudo mount /dev/XXX /mnt/drive
``` where xxx is going to be sda, sdb, sdc, whatever the drive it is your are trying to mount.  you can then find the mounted drive in nautilus by navigating to /mnt/drive

Thank you adult swim, you helped me (a newbie) to solve a headache!

---

### Post by And6ate9 on 2009-01-26
sorry guys I have yet to get to it I in the middle of a multiboot and I am editing my fstabs now. So I will try it out as soon as I get that done.

Thanks again.

---

### Post by And6ate9 on 2009-03-10
well the mounting in the mnt directory works but the 

gconftool-2 --type boolean --set /apps/nautilus/desktop/volumes_visible "false"

This doesn't seem to work?

---

