---
title: "ownership of USB ext3 external disk"
date: 2009-05-04
forum: General Help
---

### Post by simiasota on 2009-05-04
Hello,
I have ext3 formatted external USB disk.

- Why is it ext3? because I use it with rsync to make exact backup copies of my documents/directories

I would like to have it auto-mounted every time I plug in the cable to my principal linux box, and also have it mounted with my uid/gid, so I can write and read from it.
So I first changed ownership (chmod -r user:group /media/disk) of the file system from the mount point down. user and group are mine, for example 501:501. 

I would also like to move to another linux box (a secondary one) where I could have a different uid/gid (ex: 1001:1000), and mount the disk so that the ownership reflects my uid under this second linux box, different from the principal one.

I went through udev rules, fstab options, but nothing worked.
At this point I'm thinking that it is not possible at all, unless I have the same uid/gid in all the linux boxes i plug it in.

Is there any suggestion on what I could try?

francesco

---

### Post by alyawn on 2009-05-11
I have this same issue, only it's not with ext3, but with hfs+. I'm attempting to simply plug-in an external drive that is shared between many Macs and Xubuntu users and I'd like it to mount with full write privileges like it does on the Mac. I would think that this would be the default behavior, but it doesn't seem to be and I can't find anything regarding user privileges and the "Removable Storage and Media" settings anywhere. I can chown to get it to work, but it seems like this should be handled automatically. Where can I suggest this as a feature?

---

