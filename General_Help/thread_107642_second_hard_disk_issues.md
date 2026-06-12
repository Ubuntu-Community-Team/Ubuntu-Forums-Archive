---
title: "second hard disk issues"
date: 2005-12-23
forum: General Help
---

### Post by dcast on 2005-12-23
Hi, I installed a second hard disk I had lying around 10 gig maxtor 5400 rpm I beliieve. I formatted it, made a folder in my home folder which I use as its access path ( I only want to use this drive for storing media like music and video). Whenever I reboot it it disables itself and there is no access path. I can enable it again and change the access path again and all the files are still there but this is annoying. How can I make it automount and not change the settings?
Help is appreciated, Happy Holidays

---

### Post by rcerreto on 2005-12-23
Sorry if this is a silly question: did you set an entry into /etc/fstab to mount the partition at boot time?

---

### Post by dcast on 2005-12-23
not a silly question because no lol. How do I do that?

---

### Post by rcerreto on 2005-12-23
sudo gedit /etc/fstab

add a line like:

/dev/hdb1   </path/to/where/you/like/to/mount/it>   <fstype>   defaults   0  0

not shure about /dev/hdb1 that assumes that your 2nd disk is connected as slave on the primary IDE channel. Is it?

<fstype> depends on how you formatted the disk: vfat, ext2, ext3, reiserfs, ....

At first only root will be able to acces the mounted partition.
cd into </path/to/where/you/like/to/mount/it> and:

sudo chown -R <your-user-id>  </path/to/where/you/like/to/mount/it>

---

### Post by dcast on 2005-12-23
thanks a lot thats pretty straight forward

---

### Post by lolocaust on 2005-12-24
hmm, i think it would be a good idea to somehow have an option in the disks manager that would automount a particular disk when it's enabled.

---

