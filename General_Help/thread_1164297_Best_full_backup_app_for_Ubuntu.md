---
title: "Best full backup app for Ubuntu"
date: 2009-05-19
forum: General Help
---

### Post by TitanTiger on 2009-05-19
I just had to reinstall my 9.04 system because it decided it just wouldn't boot any longer.  Now that I've got all my settings and wireless config done again, I don't want to have to do this again so I want to do a full backup image that can be used as disaster recovery.  What's the best app out there for doing this?

---

### Post by exutable on 2009-05-19
Acronis True Image and Norton Ghost are really good programs.  Unfortunately you have to pay for both of them.

Exutable

---

### Post by bhishan on 2009-05-19
Keep works for me.

---

### Post by TitanTiger on 2009-05-19
I see a program called Keep in Synaptics Package Manager, but it says it's a "backup system for KDE."  Is that the one and will it work fine with GNOME?

---

### Post by Cheesemill on 2009-05-19
[CloneZilla]("http://clonezilla.org/") is a free open-source alternative to Ghost / True Image

Cheesemill

---

### Post by logos34 on 2009-05-19
if you need ext4 support on jaunty, then definitely Clonezilla, if you prefer FOSS apps.  Or Partimage (ext2/3).

---

### Post by colau on 2009-05-19
+1 for clonezilla.
I will try with this.

---

### Post by TitanTiger on 2009-05-19
> **logos34 said:**
> if you need ext4 support on jaunty, then definitely Clonezilla, if you prefer FOSS apps.  Or Partimage (ext2/3).

When I go to download Clonezilla, I only see ones for i386 architecture.  Anyone know if the experimental version (only one that supports ext4) is available in amd64?

---

### Post by logos34 on 2009-05-19
> **TitanTiger said:**
> When I go to download Clonezilla, I only see ones for i386 architecture.  Anyone know if the experimental version (only one that supports ext4) is available in amd64?

it doesn't matter--it's a live cd, it'll run fine, so just get the i386

it's what I use (x64 here too)

---

### Post by nowhere@cox.net on 2009-05-19
As an alternative, you could just use dd to make an image of your fresh install. This would be best to do before you add any data files such as videos and such so that they aren't taking up a lot of space in your image file.

My suggestion is to boot from the LiveCD and plug a large external usb drive. Then check your drive names:
```
sudo fdisk -l
```
You will be able to determine which /dev/sdx drive is your main system drive which should not be mounted because you booted from the LiveCD. 

Next you can take an image of your main drive
```
dd if=/dev/sdx of=/media/ExternalDrive/name_of_your_image.iso bs=10M
```

If you need to reverse the process, you boot from the LiveCD, do the fdisk to confirm drive assignments then do 
```
dd of=/dev/sdx if=/media/ExternalDrive/name_of_your_image.iso bs=10M
```

This will overwrite the entire drive with your backed up image.  

Keep this in mind...

EDIT: One note is that this will copy all blocks on the hard drive so it's not the best choice for very large hard drives...

---

### Post by TitanTiger on 2009-05-19
Clonezilla seems to have worked without a hitch.  Hopefully I'll be in good shape if things go squirrely again.  Thanks!

---

### Post by 7tisix on 2009-06-13
Clonezilla works very well.  If you do advanced restore options, don't replace grub.  If you do it on accident, no worrys, just restore again and don't click the grub option (if you GUI).

Also, you can save the backup and restore commands for later use, so you can quickly make and image or quickly back up.

I would recommend separate partitions for /home and /, this way you can create small "snapshots" of your system state.

---

