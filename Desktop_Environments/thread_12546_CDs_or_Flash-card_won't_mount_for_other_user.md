---
title: "CDs or Flash-card won't mount for other user"
date: 2005-01-25
forum: Desktop Environments
---

### Post by RU63 on 2005-01-25
I created a profile for my girlfriend, since it is her laptop.  She went to put her documents and pictures in her folders.  However, the CDs or the Flash card won't mount.  They mount under my profile, the one i created when i installed Ubuntu.

Both of our profiles are sudoers.... 

How can i get them to automatically mount on her profile?  

Thanks,

---

### Post by grj on 2005-01-25
Is your girlfriend's user-id in the cdrom group? If not add her there.

If you open 'Applications->Other->File Browser', then traverse your way to
'/dev/cdrom' or '/dev/cdrw'
right click and select 'Properties' then click the 'Permissions' tab. This will tell you what groups can read, write and execute that file(cdrom).

---

### Post by RU63 on 2005-01-26
Thanks for that.. i found out that root has permission... but i can;t change it because it says that i do not have permission.

also, I would really like to solve this by editing the fstab.

Can someone post their fstab file so i can view it and learn what needs to be done,

This is what mine looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

---

### Post by grj on 2005-01-26
Did you add your girlfriend to the cdrom group?

Your fstab looks fine to me. However, I am a newbie myself, not a guru.

You should not have to change permissions or your fstab though.

I simply pointed you to the permissions screen so you could see what I meant by permissions.

Open a terminal and type 
sudo ls /dev/cd* -l
The last character is ell.

You should see permissions all the way across.

---

### Post by RU63 on 2005-01-26
Ahh, i see.  Well it says only root has permission:

lrwxrwxrwx    1 root     root            3 2005-01-26 12:18 /dev/cdrom -> hdc


so now i must figure out how to add her to the cdrom group . . .


Thanks for helping me.  I am far from being a guru.

---

### Post by RU63 on 2005-01-26
I found it i think....  Computer >> System Config >> USer and Groups


but i would like to know how to do this in terminal...

This learning never stops . .  :)

---

### Post by mendicant on 2005-01-26
Take a look at adduser:

% man adduser

Look for the title "Add an existing user to an existing group"

% adduser <user> <group>

---

