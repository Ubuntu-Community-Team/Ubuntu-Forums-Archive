---
title: "unable to login because missing disk space"
date: 2009-04-23
forum: General Help
---

### Post by slakov on 2009-04-23
Dear friends,

just an hour ago I installed my first Ubuntu. And already got stuck :( The thing is - I chose for automatic partition side by side with MustDie ©. I hoped that I would be asked about the space for Ubuntu but instead it installed itself in a very small partition. After I additionally install Gnome Partition Editor I got an error that I am missing disk space for writing authentication file. Since that I can't login in Ubuntu - getting this error message every time. What's the easiest way to solve it? (Torrenting for partition magic and repartitioning it from windows seems cumbersome).

Many thanks upfront!

---

### Post by michy99 on 2009-04-23
If you have the Ubuntu install disk, you can boot from it and use the included partitioner.

---

### Post by drs305 on 2009-04-23
Welcome to ubuntu. 

One option would to be to boot to the LiveCD and select gparted from there (System, Administration, Partition Editor). You can move the partitions around from the LiveCD.

Another option, again from the live cd, just to get it working, would be to mount the ubuntu system and delete some of the downloaded files. You would make a temporary folder, mount the system partition onto it, and then delete some files to make some space. But eventually you would probably have to repartition anyway.

I think the first option would be better but if you want to pursue the second let us know.

---

### Post by slakov on 2009-04-23
thanks for your fast reply! I booted from the LiveCD and looking at the Partition Editor. I can resize windows' partition but those which I need to resize have some keys pictures next to them and the resize option is unavailable. Is it supposed to be so?

---

### Post by Peter09 on 2009-04-23
The LiveCD may have mounted the Linux partitions automatically, you may need to unmount them.

---

### Post by slakov on 2009-04-23
That's not the case. No medias are mounted as far as I can see. Even resizing windows partition works only as putting the task but when I try to apply it fails. I wish I chose for manual partitioning during the installation.

---

### Post by drs305 on 2009-04-23
slakov,

I don't readily suggest reinstallations but in this case either your partition table needs repair or there are other issues. Do you think you could reinstall and select manual partitioning, leaving the partition you want to save alone and trying to set up the partitions again?

I know the servers are probably being hit hard for downloads but if you have the CD you could at least get a start.

---

### Post by slakov on 2009-04-23
I might consider re-installation. I  looked a bit at the documentation of gparted and suspect that the reason might be that I didn't CHKDSK NTFS partition after installing ubuntu. I try to do it now (takes damn a while). If it doesn't help I'll go for reinstall.

---

### Post by drs305 on 2009-04-23
Here are a few good resources for installations. The first is a great resource for planning an install. The second is an official installation guide - it's for 8.04 but the install is just about the same. The third is the 9.04 resource page:

[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")


[https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")

[https://help.ubuntu.com/9.04/index.html]("https://help.ubuntu.com/9.04/index.html")

---

### Post by slakov on 2009-04-23
I am still trying to solve the problem without reinstall. I succeed in shrinking the existed NTFS partition (indeed CHKDSK helped) but now I cant increase the ubuntu partition.  When I boot from LiveCD, GParted indicates that the swap partition is mounted, but when I type in bash 'umount /dev/sda6' I get a message that the device is not mounted. I am puzzled. Many thanks for any help.

---

