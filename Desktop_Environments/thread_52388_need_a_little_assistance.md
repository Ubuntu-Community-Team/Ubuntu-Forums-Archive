---
title: "need a little assistance"
date: 2005-07-27
forum: Desktop Environments
---

### Post by aleahey on 2005-07-27
basically i had a fat32 hard drive i threw in to my linux box. i converted it to ext3 with mkfs, and now i get a "bad superblock" error when fstab attempts to mount. 

/dev/hdb5       /backup    ext3    user      0       0

is the last line in my fstab. what i need to know is what is the proper method of formatting a drive in ext3 (in case i did it improperly) and what is the proper line in fstab to have it read/writable for all users. 

ive attempted to search the forums, im not lazy :P, but i cant seem to find an answer to my specific problem.

gracias in advance.

---

### Post by varunus on 2005-07-27
Try using a partition program instead of just mkfs.  Though, it seems like it should have worked...a partitioner would be a cleaner way to reformat it.  Try the following one, its graphical:
[http://www.ubuntuguide.org/#gparted](http://www.ubuntuguide.org/#gparted)

Make sure to enable the extra repositories as describes on the UbuntuGuide.

---

### Post by aleahey on 2005-07-27
dammit!! i looked at the guide too, only looked under mounting.

many thanks man :)

---

### Post by aleahey on 2005-07-27
worked perfectly, but i still cant write to it, what should the "user" portion of the fstab be so that a non-root user can write to it?

thanks again :)

---

### Post by aleahey on 2005-07-27
[QUOTE=aleahey]worked perfectly, but i still cant write to it, what should the "user" portion of the fstab be so that a non-root user can write to it?

thanks again :)[/QUOTE]
 woops nm, just had to chmod the folder it was mounted to. thanks =]

---

### Post by aleahey on 2005-07-27
hm, now when i put files to the folder, it writes for a while and then gives me an i/o error saying i dont have permission to write to this read-only device. whats up?

when i try to chown the folder /mnt/backup to my regular user, i get:

chown: Changing ownership of "/mnt/backup" : Read-only filesystem.

---

### Post by majikstreet on 2005-07-27
About Fstab, here is a good article about it: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

That may help.....

---

