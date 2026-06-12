---
title: "Installed Ubuntu for a friend now things messed up"
date: 2009-03-08
forum: General Help
---

### Post by hallbrian on 2009-03-08
Hi i installed Ubuntu 8.10 for a friend the other day, did a duel boot with vista and ubuntu, had to resize the vista partition first took awhile.

at the end of the resize i got an error not sure what that was now, but looking at the partition editor it all look fine it resize vista and made to partitions for ubuntu

so went a head and installed ubuntu to the new partition all went ok
rebooted and grub can up - list-

Ubuntu 
Ubuntu rec
vista

as he is new to ubuntu he still wanted to use vista, but when i go to load vista just get "starting" nothing happens, load ubuntu fine and can see files on the vista partition all boot file are there and so is bootmgr

here is some info if anyone can help..

sudo fdisk -l

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               3       15648     5632000   27  Unknown
/dev/sda2   *      17209
mike says:
 3      868250   250616880    7  HPFS/NTFS
/dev/sda3           15649      172089    56318760    5  Extended
/dev/sda5           15649      153646    49679275   83  Linux
/dev/sda6          153647      172089     6639475   82  Linux swap / Solaris
```

sudo blkid

```

 /dev/sda1: UUID="C68C9B3F8C9B28C7" TYPE="ntfs" 
/dev/sda2: UUID="64A49F00A49ED440" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: UUID="6733f62a-9d34-4de0-b29a-6a0318f29843" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="c4eee05c-6ba8-4b18-b34f-54dbb64e83ed" 
```

sudo df -h

```

 ilesystem            Size  Used Avail Use% Mounted on
/dev/sda5              47G  5.3G   39G  12% /
tmpfs                 504M     0  504M   0% /lib/init/rw
varrun                504M  208K  504M   1% /var/run
varlock               504M     0  504M   0% /var/lock
udev                  504M  2.9M  502M   1% /dev
tmpfs                 504M  296K  504M   1% /dev/shm
lrm                   504M  2.0M  



 502M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda2             240G  138G  102G  58% /media/Vista

```

i see there is no * next to sda2 under boot or any other thinking this may be a problem.

am hope i can do something without reinstalling vista as he has no restore disc and looking in cat /etc/fstab

there is no second vista/horn to surguest that there is recovery partition

any help would be great, coz i did say he would be able to till use vista and learn about linux on ubuntu..

cheers
Brian

---

### Post by Neo_The_User on 2009-03-08
```

sudo fdisk /dev/sda
sudo fdisk -a /dev/sda2

```

Good luck. You can use the ubuntu live cd, gentoo minimal cd, gentoo live cd, or the arch linux cd to do those commands in. They all have fdisk on them.

---

### Post by hallbrian on 2009-03-08
umm can u tell me what these commands do as i am not there at the min and will have get him to do it, as he is a linux noob..

and does he have to do this from a live cd can he not do this within ubuntu installed on the system

manythanks

Brian

---

### Post by Neo_The_User on 2009-03-08
```

man fdisk

```

I recommend doing everything that has to do with partitions on a hard drive, should be done on a CD.

fdisk -a toggles boot partition
fdisk /dev/sda sets the directory of what fdisk is in.

---

### Post by miegiel on 2009-03-08
> **Neo_The_User said:**
> ```

sudo fdisk /dev/sda
sudo fdisk -a /dev/sda2

```

Good luck. You can use the ubuntu live cd, gentoo minimal cd, gentoo live cd, or the arch linux cd to do those commands in. They all have fdisk on them.

I'm guessing he also needs to toggle the boot flag on on another partition :twisted:

@hallbrian
The windows partition might be fubar, If you can access it from linux start backing up important stuff. After that try repairing the partition, maybe you won't need to reinstall windows. :-\" Can't really say what might have gone wrong since you can't remember the error message (got to love cameras)

---

### Post by hallbrian on 2009-03-08
Cant really do much till he gets back to me with the output for the above commands..

the resize took over 4hours to do and it got all the way to the end before i got the ever message, i was using ubuntu live cd to partition the dive..

Say i can fix sda2 partition could i do that via ubuntu intsall ver or live ver and how would i go about doing that. told him already to start backing up things he need, hopefuly if i can get the vista partition fixed and bootable nothing will be lost.

Thanks again

Brian

---

### Post by miegiel on 2009-03-08
in linux fsck is the 1st place i'd look, not sure if it can check ntfs :twisted:

---

