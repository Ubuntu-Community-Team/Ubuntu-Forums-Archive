---
title: "How to set my KUbuntu to auto-mount windows partitions?"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Cool_dude_Prav on 2005-04-09
Plz help me.
I want KUbuntu to auto-mount the FAT32 partitions I have( hda3, and hda5 to hda8 )

Also i want it to appear on my desktop as valid drives as in Windows... 

Tnx..

---

### Post by localzuk on 2005-04-09
You need to edit the file /etc/fstab

For the listings for those items you need something like:

/dev/hda3      /media/hda3     vfat    defaults    0 0

Then you will have those items in your filesystem, it is as simple as creating a link to them wherever you want it...

---

### Post by PhilD on 2005-04-09
[QUOTE=Cool_dude_Prav]Plz help me.
I want KUbuntu to auto-mount the FAT32 partitions I have( hda3, and hda5 to hda8 )

Also i want it to appear on my desktop as valid drives as in Windows... 

Tnx..[/QUOTE]

This is covered well in the ubuntu starter guide at [http://ubuntuguide.org/](http://ubuntuguide.org/)  It is not even necessary to reboot.

I take it these are *local* partitions, ie. Windows partitions on the same machine that you are running Ubuntu on. In that case you need the part of the guide under "Windows" -> "How to mount/unmount Windows partition (NTFS) manually, and allow all users to read only?" onwards. FAT is covered under there too.

I would not recommend placing these drives on your desktop. They are system-level things so you should place them somewhere global so that all users can use them. I thought the standard place in Linux was /mnt, but the guide seems to use /media. Either will do.


If you want to access Windows drives on other computers you will need to install Samba - this is also covered in the guide.

Hope this helps,

---

### Post by Cool_dude_Prav on 2005-04-10
Tnx @Phil.. me got it right ;)
Tnx again...

---

### Post by Cool_dude_Prav on 2005-04-16
[QUOTE=PhilD]This is covered well in the ubuntu starter guide at [http://ubuntuguide.org/](http://ubuntuguide.org/)  It is not even necessary to reboot.

I take it these are *local* partitions, ie. Windows partitions on the same machine that you are running Ubuntu on. In that case you need the part of the guide under "Windows" -> "How to mount/unmount Windows partition (NTFS) manually, and allow all users to read only?" onwards. FAT is covered under there too.

I would not recommend placing these drives on your desktop. They are system-level things so you should place them somewhere global so that all users can use them. I thought the standard place in Linux was /mnt, but the guide seems to use /media. Either will do.


If you want to access Windows drives on other computers you will need to install Samba - this is also covered in the guide.

Hope this helps,[/QUOTE]
 Hey ppl!!!

That dint work!!!

I get error that fs is mentioned as wrong type (vfat)

Actually the partitions hda5 to hda8 are logical partitions of extended partition hda4...
So what should I enter as the type of Fs in fstab??

Please help me...

---

