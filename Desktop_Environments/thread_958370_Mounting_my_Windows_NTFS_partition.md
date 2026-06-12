---
title: "Mounting my Windows NTFS partition"
date: 2008-10-25
forum: Desktop Environments
---

### Post by DSL5 on 2008-10-25
ok, so I've been looking around the internet for a while for an answer for this question, but I can;t seem to find it.

Basically, I want to create a launcher that will mount my windows partition (NTFS). I don't want it automatically mounted at startup. I want a launcher that would be the same thing as going to Places > Local Disk (the name of my windows drive) which would them prompt me for my password and then mount it.

Does anybody know how to do this??

---

### Post by DoctorMike on 2008-10-25
Create a file on your desktop called Mount Drive or whatever you want the launcher to be called. Edit it using gedit so that it contains the following text:

gksu mount /dev/sda1 /media/ntfs

Change /dev/sda1 to whatever your ntfs drive is and /media/ntfs to where ever you want it mounted. Save the file.

Right click on the file, choose properties. Click on permissions, and tick the box for Allow executing file as a program.

Voila, one launcher.

---

### Post by DSL5 on 2008-10-25
it didn't work......

all that did was ask me for my password, then nothing happened...

---

### Post by DSL5 on 2008-10-28
*bump* Any ideas?

---

### Post by DSL5 on 2008-11-02
*bump* anybody know a way to do it in 8.10?

---

### Post by epswinde on 2008-11-02
install ntfs-config from synaptic, then run it, and name the mount point.
its a fun little gui frontend to editing fstab.

once you have that installed, it's in the administration menu.  just pick a name for the partition, and ntfs-config will modify /etc/fstab so that your partition mounts automatically at boot time to /media/(name)

this will allow any user to read/write this partition.  if that's not what you want, there's a number of other options.  This, however, is the easiest way (i think)

---

