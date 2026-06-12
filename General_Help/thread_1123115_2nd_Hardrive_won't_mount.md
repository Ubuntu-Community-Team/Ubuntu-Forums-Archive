---
title: "2nd Hardrive won't mount"
date: 2009-04-11
forum: General Help
---

### Post by mlamorey on 2009-04-11
OK, Hi, ):P
Been some time since my last Linux box died and I am getting started again. I have things up and running OK. I have just installed a 2nd hard drive as I was using my "safe" backup drive too frequently to access music since my boot disk is too small to fit everything. So, HD is in and can be seen. I re-formatted it with Gparted as ETC3 (is that the best format?). I plan to use it for about 50 Gb of permanent music and that is about all. Ubuntu can see but I do not think it is properly mounted per the below


mark@mark-desktop:/$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             37136072   2937228  32327276   9% /
varrun                  509168       100    509068   1% /var/run
varlock                 509168         0    509168   0% /var/lock
udev                    509168        64    509104   1% /dev
devshm                  509168        12    509156   1% /dev/shm
lrm                     509168     39792    469376   8% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon      37136072   2937228  32327276   9% /home/mark/.gvfs
mark@mark-desktop:/$

---

### Post by drs305 on 2009-04-11
Welcome to the ubuntu forums mlamorey,

I will assume that you mean formatted to EXT3.

Make a mount point. It normally would be in /media, where it would show on your desktop, or in /mnt, where it normally wouldn't. /media is usually reserved for removable drives, while /mnt is used for permanent drives. It doesn't really matter. I will use /mnt for this but you can substitute /media if you wish.

Find the designation of your data drive. Open a terminal with ALT-F2 and tick run in terminal. enter the following in the window. If you have never used sudo, it will ask for your password. You won't see it as you type but it's being registered:
```
sudo blkid
```
Note the sdXX designation (sda2, sdb3, etc) and the UUID. In the following commands, substitute your values for */dev/sdXX*, */mnt/mydata*, and the actual *UUID*.

Make a mount point and make yourself the owner:
```
sudo mkdir /mnt/mydata
sudo chown -R *yourusername:* /mnt/mydata  # substitute your username and mount point
```
Example:  sudo chown -R ralph: /mnt/mydatapartition
Backup and edit fstab:
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```

Add the following line and save the file. You can use *either* of these entries but the UUID from the first command is preferable:
```

UUID=17383-238a-a393-w334-333 /mnt/mydata  ext3 relatime 0 2
*or*
/dev/sdXX /mnt/mydata ext3 relatime 0 2

```

Mount the new device. If you don't get any error messages, the partition mounted to /mnt/mydata.
```
sudo mount /dev/sdXX
```

---

### Post by mlamorey on 2009-04-12
:p
Excellent. Yes, EXT3! and the directions worked. I searched the threads and found other instructions but none worked. Cheers...

I will now shut down and hope it is automatically mounted on log in / boot up.

---

