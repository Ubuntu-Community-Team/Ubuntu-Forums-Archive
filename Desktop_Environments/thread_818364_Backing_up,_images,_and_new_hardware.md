---
title: "Backing up, images, and new hardware"
date: 2008-06-04
forum: Desktop Environments
---

### Post by gyzer on 2008-06-04
I am currently having hardware problems (or at least I'm 95% sure its just hardware problems) with my computer that is running hardy. I belive my problem has to do with the motherboard and I had some questions:
 
If I'm swapping out an entirly different type of motherboard, will Ubuntu detect the new hardware and load those drivers accordingly or will it be like windows where it will error out and only a fresh install of the os will make it all work?
 
Is there anyway to make an image of my hard drive that hardy is installed on? If there is what programs are best to use?
 
If I can't do an image, is there a way to backup different settings and installed programs so after I do a new install of hardy it will be as painless as possible to get back to my current state of all my settings and installed programs?

---

### Post by gyzer on 2008-06-05
is this the wrong forum to have posted this?

---

### Post by mannheim on 2008-06-06
Swapping the hard drive out of one machine and into another will just work, with a few small adjustments:[LIST=1]
[*]If the layout of the disks is different in the new machine (e.g. if the hard disk was recognized as the "first" hard disk on the old machine but is the "second" hard disk in the new machine) then you may need to reinstall grub and/or edit grub's menu.lst file. You may also need to edit /etc/fstab. (Recent versions of Ubuntu have used UUID's in /etc/fstab, which makes editing unnecessary.)
[*]You may need to edit /etc/X11/xorg.conf if your graphics hardware or monitor have changed.
[*]When I did this once, I also found that the ethernet card in the new machine was referred to as "eth1". The name "eth0" still referred to the ethernet interface of the old machine, which no longer existed on the new machine.
[/LIST]

---

### Post by gyzer on 2008-06-06
Yeah the hardware on it is going to be the same outside of the sound and ethernet which are on the board. 
 
I assume if I want to put in a newer video card that I should leave it alone for the initial swap and then install it afterwards?
 
Also how would I reinstall grub if it doesn't work?

---

### Post by mannheim on 2008-06-06
> **gyzer said:**
> 
Also how would I reinstall grub if it doesn't work?

If the hard disk is going to be /dev/sda in the new machine, and if the root partition on that hard disk is /dev/sda1, then reinstalling grub would be something like this. Boot from the Live CD, then do:
```

sudo mkdir /mnt/my-disk
sudo mount /dev/sda1 /mnt/my-disk
sudo grub-install --root-directory=/mnt/my-disk /dev/sda
```

There are more detailed how-tos posted elsewhere on these forums.

---

### Post by gyzer on 2008-06-06
Actually that seems very straight forward. 
 
Thanks for the info. Now all I need is the time to actually do all this lol

---

### Post by gyzer on 2008-06-11
Out side of the /home directory, are there any other directories that can have settings that I'd want to back up?
 
Also where are themes saved?

---

### Post by gyzer on 2008-06-11
Also, where are the favorits stored for firefox, and where is your emailed stored for Thunderbird?

---

