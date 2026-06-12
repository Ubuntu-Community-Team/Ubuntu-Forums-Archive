---
title: "Accessing partition"
date: 2005-02-04
forum: Desktop Environments
---

### Post by paulo on 2005-02-04
Hello again. 
Dumb newbie is back with another stupid question:

Having just successfully mounted and got access to my other hard drive (windows) I now need to mount a seperate partition that exists on the same hard drive as linux, but which has files running under windows xp. I am guessing that because my origional 'c' drive was hda1, then the first partition on my 2nd drive will be hda2. Yes? No? 

I tried editing the fstab with the following:

/dev/hda2 /media/backupbrane auto defaults  0 0

and created a drive for it in media with 'mkdir' but there is still nothing in it. Can anyone enlighten me please?

Thanks,
Paulo

---

### Post by ilari on 2005-02-04
[QUOTE=paulo]Hello again. 
Dumb newbie is back with another stupid question:

Having just successfully mounted and got access to my other hard drive (windows) I now need to mount a seperate partition that exists on the same hard drive as linux, but which has files running under windows xp. I am guessing that because my origional 'c' drive was hda1, then the first partition on my 2nd drive will be hda2. Yes? No? 

I tried editing the fstab with the following:

/dev/hda2 /media/backupbrane auto defaults  0 0

and created a drive for it in media with 'mkdir' but there is still nothing in it. Can anyone enlighten me please?

Thanks,
Paulo[/QUOTE]
 The IDE-disk are name as hd* where * can be letter from a to h. The disks a and b are the master and slave at the primary interface of the 1st IDE-controller. The disks c and d are master and slave at the secondary interface of the 1st IDE-controller. Then the 2nd controller etc... In your setup, the first partition of the second disk could therefore be /dev/hdb1 or /dev/hdc1, depending on the cabling.

---

