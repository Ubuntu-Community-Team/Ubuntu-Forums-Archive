---
title: "My drives won't mount by default anymore"
date: 2008-04-27
forum: Desktop Environments
---

### Post by davbren on 2008-04-27
Hey, I just install Hardy and I noticed that my windows disks and other hard drives don't mount by default anymore... This also includes an ftp I had on my desktop...

any ideas?

---

### Post by davbren on 2008-05-04
seriously I need help with this one...

---

### Post by lswest on 2008-05-04
can you post the output of ```
sudo blkid
cat /etc/fstab
```

---

### Post by davbren on 2008-05-04
/dev/hdb1: UUID="7E68A34C68A301CF" TYPE="ntfs" 
/dev/sda1: UUID="BE5478325477EB91" LABEL="Stuff" TYPE="ntfs" 
/dev/sda2: UUID="9e4676f3-53cb-48a8-aa7c-66b301e966f8" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="b61e2f54-531a-478e-963a-5ee638f4b53f" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0819" TYPE="vfat" 
/dev/sdb2: UUID="007CD88F7CD880B8" LABEL="Stock Pile" TYPE="ntfs" 
/dev/sdc1: UUID="55D123D9E79ABF54" LABEL="Movies" TYPE="ntfs" 
dave@dave-desktop:~$ 
dave@dave-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9e4676f3-53cb-48a8-aa7c-66b301e966f8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=b61e2f54-531a-478e-963a-5ee638f4b53f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by lswest on 2008-05-04
looks like the drives aren't in your fstab file, so what hard drives exactly do you want to have mounted at boot?  you can add them by doing this:
```
sudo gedit /etc/fstab
```
then add these lines (per drive) into the file
```
#/dev/[name of hard drive, e.g. hdb1]
UUID=[UUID of drive from blkid command] /media/[mountpoint]     ntfs    defaults,umask=007,gid=46 0
```

where for the mountpoint you need to find which it is in /media/ or make a new one by using ```
sudo mkdir /media/[mountpoint]
```

---

### Post by davbren on 2008-05-04
I would like all of them to mount except the "DEll Utility" and the swap partition...

Thank you for this help.

---

### Post by vvvladut on 2008-05-04
I'm having the same problem, only in Kubuntu.

You have to add a new line to your /etc/fstab file for each partition you wnt to mount automatically. I'm just not sure exactly what to write for a ntfs partition...

---

### Post by lswest on 2008-05-04
okay, so you have to open your /etc/fstab file (i posted the command above, and add these lines (just copy and paste, then tab the words so they're in line in the doc).
```

#/dev/sda1
UUID=BE5478325477EB91 /media/sda1    ntfs    defaults,umask=007,gid=46 0

#/dev/sdb2
UUID=007CD88F7CD880B8 /media/sdb2    ntfs    defaults,umask=007,gid=46 0

#/dev/hdb1
UUID=7E68A34C68A301CF /media/hdb1    ntfs    defaults,umask=007,gid=46 0

#/dev/sdc1
UUID=55D123D9E79ABF54 /media/hda1    ntfs    defaults,umask=007,gid=46 0
```
quick note here: if the folders don't exist (under /media/) then either make them using the above mentioned command, or else edit that bit to fit folders used for the hard drives prior.  Also, you may need to change your gid to match the one for your computer, not 100% on how to check what it is though.  Maybe someone else will know.

---

### Post by vvvladut on 2008-05-04
If lswest's reccomendation is correct, what you have to do is edit your /etc/fstab filelike this:

```
gksudo gedit /etc/fstab
``` 

Than it has to look like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=9e4676f3-53cb-48a8-aa7c-66b301e966f8 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda3
UUID=b61e2f54-531a-478e-963a-5ee638f4b53f none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
#/dev/hdb1
UUID=7E68A34C68A301CF /media/windows     ntfs    defaults,umask=007,gid=46 00
#/dev/sda1
UUID=BE5478325477EB91 /media/stuff     ntfs    defaults,umask=007,gid=46 00
#/dev/sdb2
UUID=007CD88F7CD880B8 /media/stock_pile     ntfs    defaults,umask=007,gid=46 00
#/dev/sdc1
UUID=55D123D9E79ABF54 /media/movies     ntfs    defaults,umask=007,gid=46 00

```

Now, if lswest is correct, then that's exactly what your new fstab should look like, so you can copy paste from here. As for me, I have to say I'm too afraid to try this yet, but if you want to go ahead and post here the results, please do! :D

---

### Post by vvvladut on 2008-05-04
...or do what lswest said...:)

I'm not too sure about that gid part either: what does that do and whay does 46 mean?

---

### Post by lswest on 2008-05-04
gid stands for "group ID" and is the number assigned to the user's default group, or the group which handles mounting, i'm not sure, and it happens to be (or used to be) 46, i'm not sure entirely.

what the line does it tell the system what drive (by the UUID) to mount, where (the /media/ bit), what it's formatted as, then what options to use.

---

### Post by tvtech on 2008-05-04
the uid and gid 

> set the owner and the group of files and directories the values are numerical the defualts are the uid and gid of the current process.    

in english   this sets the owner and the group values for all the files and directories within the mount.  the values are numerical means that each numerical value is a switch for who owns these files and can manipulate them.  this is all expounded upon in the ntfs-3g man page ```
username@localhost~$man ntfs-3g
```  this is the kernal module that allows you to natively access and write to NTFS file systems.

the gid of 46  is the standard usermode of the current process.  actually finding out what 46  is a specific switch of .... good luck if you find out the man pages always seem to lack that key information.

---

### Post by lswest on 2008-05-04
> **tvtech said:**
> the uid and gid 

set the owner and the group of files and directories the values are numerical the defualts are the uid and gid of the current process.    

in english   this sets the owner and the group values for all the files and directories within the mount.  the values are numerical means that each numerical value is a switch for who owns these files and can manipulate them.  this is all expounded upon in the ntfs-3g man page ```
username@localhost~$man ntfs-3g
```  this is the kernal module that allows you to natively access and write to NTFS file systems.

that's pretty much what i thought, and i'm just curious as to what group it actually sets it to, or is meant to set it to.  Also, i just went through my groups (system-->administration-->users and groups) and couldn't find a group with gid of 46...hmm.

---

### Post by vvvladut on 2008-05-04
davbren, did this work out for you after all?

Anyway, I'm trying this for myself. I've edited my fstab file following lwest's instructions and will post here the results as soon as I reboot.

---

### Post by vvvladut on 2008-05-04
Well, it works! However, something strange happened to the Storage Media menu in Dolphin, my two ntfs partitions are no longer accessible through there. I don't mind, as long as they're mounted automagically at start up.

---

### Post by vvvladut on 2008-05-04
I knew I should have searched these forums more carefully before tinkering with fstab... After a bit more browsing, I found what is clearly the best solution: ntfs-config:

```
sudo apt-get install ntfs-config
```

It's a clever little program that sets up your fstab for you to automount your ntfs partitions at start up. davbren, you should use it: you only have ntfs partitions to automount, as far as I can see.

---

### Post by davbren on 2008-05-05
Erm, well I'm getting a funny error... (see pic)

This is my fstab```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=9e4676f3-53cb-48a8-aa7c-66b301e966f8 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda3
UUID=b61e2f54-531a-478e-963a-5ee638f4b53f none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
#/dev/hdb1
UUID=7E68A34C68A301CF /media/windows     ntfs    defaults,umask=007,gid=46 00
#/dev/sda1
UUID=BE5478325477EB91 /media/stuff     ntfs    defaults,umask=007,gid=46 00
#/dev/sdb2
UUID=007CD88F7CD880B8 /media/stock_pile     ntfs    defaults,umask=007,gid=46 00
#/dev/sdc1
UUID=55D123D9E79ABF54 /media/movies     ntfs    defaults,umask=007,gid=46 00
```

---

### Post by davbren on 2008-05-05
ntfs-config worked a treat, thanx for all your help!

---

### Post by rudihawk on 2008-06-08
> **lswest said:**
> looks like the drives aren't in your fstab file, so what hard drives exactly do you want to have mounted at boot?  you can add them by doing this:
```
sudo gedit /etc/fstab
```
then add these lines (per drive) into the file
```
#/dev/[name of hard drive, e.g. hdb1]
UUID=[UUID of drive from blkid command] /media/[mountpoint]     ntfs    defaults,umask=007,gid=46 0
```

where for the mountpoint you need to find which it is in /media/ or make a new one by using ```
sudo mkdir /media/[mountpoint]
```

Thanks! You helped solve my problem!:guitar:

---

### Post by awilki01 on 2008-06-08
I tried ntfs-config and I get the following errors:

```

adam@adam-ubuntu:/media$ sudo ntfs-config

** (ntfs-config:32592): WARNING **: Can't find device with uuid = F89C30389C2FEFB4


** (ntfs-config:32592): WARNING **: Can't find device with uuid = B6D412BED4128133


```


These were listed in my original /etc/fstab file:
```

adam@adam-ubuntu:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=4e9c07bb-c6c5-4ee1-910f-f1bb41273f78 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/sda1
UUID=F89C30389C2FEFB4 /media/sda1     ntfs    defaults,umask=007,gid=46 0       
1
# /dev/sda5
UUID=B6D412BED4128133 /media/sda5     ntfs    defaults,umask=007,gid=46 0       
1
# /dev/sdb1
UUID=2E8E95880E43FA71 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       
1
# /dev/sdb3
UUID=0733bd47-2ec1-456e-995c-357616648f7a none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

After I ran ntfs-config, it remarked these devices as unknown in my fstab file:
```

adam@adam-ubuntu:/media$ more /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=4e9c07bb-c6c5-4ee1-910f-f1bb41273f78 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=F89C30389C2FEFB4 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=B6D412BED4128133 /media/sda5 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda1 :
UUID=2E8E95880E43FA71 /media/sdb1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda3 :
UUID=0733bd47-2ec1-456e-995c-357616648f7a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
adam@adam-ubuntu:/media$ 

```

My system only sees three partitions - one NTFS drive, the ext3 linux filesystem, and the swap space:
```

adam@adam-ubuntu:/media/disk1$ sudo blkid
/dev/sda1: UUID="2E8E95880E43FA71" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="0733bd47-2ec1-456e-995c-357616648f7a" 
/dev/sda2: UUID="4e9c07bb-c6c5-4ee1-910f-f1bb41273f78" SEC_TYPE="ext2" TYPE="ext3"

```

Any ideas how I can get Ubuntu to somehow see my other two NTFS partitions?  Is there some setup program or something I can execute to do a search for other drives?

---

