---
title: "Ubuntu8.10 repair CD"
date: 2009-01-21
forum: General Help
---

### Post by pdk on 2009-01-21
Greetings.
When the ubuntu8.10 cd boots, some process uses /dev/sda1
/dev/sda1 mounted or busy. It's definitely not mounted.
It also grabs swap devices, but i can live with that.
This means for me that I am unable to perform any raid operations using 'mdadm' as my raid is on sda1 and sdb1
Anyone have an idea how to get around this problem
Thanks
Peter

---

### Post by fjgaude on 2009-01-21
I guess you are pointing to raid1 on sda and sdb. Maybe this link helps:

[http://radu.rendec.ines.ro/howto/raid1.html](http://radu.rendec.ines.ro/howto/raid1.html)

I'll have to try a liveCD and see if I can see it using any of my hard drives.

---

### Post by pdk on 2009-01-22
> **fjgaude said:**
> I guess you are pointing to raid1 on sda and sdb. Maybe this link helps:

[http://radu.rendec.ines.ro/howto/raid1.html](http://radu.rendec.ines.ro/howto/raid1.html)

I'll have to try a liveCD and see if I can see it using any of my hard drives.

Thanks Frank.
I found the rescue disk chooses one of your drives to use as swap. I only have 2.
The trick is ....   swapoff -a  which releases the drive.

There is also another serious  problem that I have with the rescue cd.
If I cold boot the system it will only boot as far as an initramfs file system. 
after... 
loading files
cp cannot create /root/var/log no such file or directory
mount /root/dev on /dev/static/dev    "
      /sys on /root/sys                "
However if I boot the os (which is working at the moment)  and restart the machine, the rescue cd will boot correctly.
Peter

---

### Post by fjgaude on 2009-01-22
Well, from many a standpoint raid1, booting from such, is not employed by many folks. Because? Because of the issues when you can't boot or a drive fails.

My instructor said, reinstalling an OS is easy, but the data has to be protected at all times... so, use a fast drive for booting and raid5 or 6 for everything else. And always have backups of data. I have three, one online, another near-line, and finally, one off-line.

Get my drift?

---

