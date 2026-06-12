---
title: "no space for installing programs"
date: 2006-05-20
forum: Desktop Environments
---

### Post by josh on 2006-05-20
hi guys!

i have a 10gb harddisk that is already full. i usally install programs by just 'apt-get install programname' now that my hard disk is full i decided to get another 10gb harddisk. i formatted it and added it to my /etc/fstab to mount as /backup. now the question is how do i tell apt-get to install it in /backup? where is the default install directory when you issue the command 'apt-get install programname'? 

thanks guys! all input is greatly appreciated!

---

### Post by aysiu on 2006-05-20
You'd want to mount it as /usr, not /backup.

It's a bit tricky, though, as you'd want to copy the entire contents of /usr to the new partition *first* and then edit the /etc/fstab

It's best to do this from a live CD.

Of course, you can always delete the contents of /var/cache/apt/archives if you want to free up space.

This can also be done from Synaptic.

---

### Post by josh on 2006-05-22
hi aysiu!

thanks for your quick reply! really appreciate your answer! thanks for helping a noob out :)

---

