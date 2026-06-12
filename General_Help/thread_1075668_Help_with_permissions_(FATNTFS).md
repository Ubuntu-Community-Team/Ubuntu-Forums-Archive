---
title: "Help with permissions (FAT/NTFS)"
date: 2009-02-20
forum: General Help
---

### Post by WoXa on 2009-02-20
Hello all. I am running Ubuntu 8.10 interpid. I am totaly new in Linux. searched forums for hole day today but didnt find how to solve my issue. the problem is that I cant write to my storage partition (which used to be d disk in windows). I can execute and read from whole storage partition but cant write to it. I can only write read or execute to/from its subfolders no problem, though. And I cant mount or unmount it, if i try so, i get: You are not privileged to mount/unmount volume storage, message (the only way to do it is use root). I am power user, i can do everything else, but this :(

please help me people :(
cheers

---

### Post by bodhi.zazen on 2009-02-20
You set the permissions of a FAT or NTFS partition when you mount it.

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by WoXa on 2009-02-21
oh yeah,forgot to mention that i have formated it under ext3. and the fstab line for it looks like that:
/dev/sda5        /media/Storage      ext3      rw,auto,user,exec                     0       0

---

### Post by mb_webguy on 2009-02-21
If you formatted it as ext3, then it's not ntfs or FAT.  If it's either ntfs or FAT (which it can't be both at the same time), then it can't be ext3.

So... are we talking about a FAT32 partition, an ntfs partition, or an ext3 partition?  Solving your problem is going to be quite different for the first two than the third, so it would be quite helpful (which is quite an understatement) to know with which we're dealing.

---

### Post by vanadium on 2009-02-21
Indeed you should edit your topic title to correctly reflect the help you request.

First, change your /etc/fstab line to

```

/dev/sda5 /media/Storage ext3 defaults 0 2 

```
unless you have a good reason to select the options you specified. The "2" at the end will make sure the drive is checke at boot time.

In linux, you do not have permissions to write except when explicitly granted permissions. In you are the only user who is to use the sda5 permissions, you can just change ownership of the moint point to your account. If more users are to use the volume, then create directories on it, and change the respective directories. For easy access to the storage from within your home directory, you could create a symbolic link to the storage in your home directory.

Note that I did not provide stepwise detail, because this is not the "Absolute beginners" forum.

---

### Post by bodhi.zazen on 2009-02-21
If you re-formatted the drive to ext3, and that is your fstab entry, use 

chown user.users /media/storage
chmod 770 /media/Storage

uer = you log in

this information is also covered in the link I gave you.

---

### Post by WoXa on 2009-02-22
sorry guys for confusion about the topic but, erm... somehow it got changed :) when i posted this thread, topic was: "something messed up with permissions" :) 
anyway guys thanks for quick and very helpful response \\:D/
i used vanadium's /dev/sda5 /media/Storage ext3 defaults 0 2 fstab line change and seems it helpped. dunno what bodhi.zazen's option does, so i havent tried that :oops: 
btw can i someone explain me why word "defaults" changed it all? and yes a this volume needs to be used by multiple users which i guess i will have to find out my self :)
cheers again ;)

---

### Post by vanadium on 2009-02-23
If the volume is to be used by multiple users, then you can create nwe directories on the volume, and change the ownerschip

```

sudo mkdir /media/Storage/user01 /media/Storage/user02
sudo chown user01:user01 /media/Storage/user01
sudo chown user02:user02 /media/Storage/user02

```

Replace "user01" and "user02" with real user logins on your system, obviously.

As an extra, you would use the power of unix symbolic links to make the system user friendly:

```

sudo ln -s /media/Storage/user01 /home/user01/Storage
sudo ln -s /media/Storage/user02 /home/user02/Storage

```

This creates a directory "Storage" in each of the home directories of the users. They can, straight from within their home directory, go to their private directory on the volume where they have full read/right access. Your users never need to navigate out of their home directory and do not need to know of the mount point.

---

### Post by WoXa on 2009-02-24
very handy!! cheers buddy! =D>

---

### Post by WoXa on 2009-02-24
*******!! something is not right with privileges! before i formated ntfs to ext3 i could do fdisk -l no problems, now, on the other hand, i have to add sudo in front of fdisk -l. although partition file system change doesnt have anything to do with fdisk -l :confused:

please enlighten me what i have done wrong this time :p

---

### Post by bodhi.zazen on 2009-02-24
what happens if you run fdisk -l or 

/sbin/fdisk -l

? 

what error message are you getting ?

---

### Post by vanadium on 2009-02-24
fdisk -l has always required root privileges. However, I remember that "blkid" could be run as a normal user. Since Hardy (or Feisty), it also requires root permissions.

---

### Post by Slim Odds on 2009-02-24
> **WoXa said:**
> *******!! something is not right with privileges! before i formated ntfs to ext3 i could do fdisk -l no problems, now, on the other hand, i have to add sudo in front of fdisk -l. although partition file system change doesnt have anything to do with fdisk -l :confused:

please enlighten me what i have done wrong this time :p

You should always have to use "sudo" with fdisk -l unless you've done a sudo very recently. As Ubuntu remembers your sudo for a short while (I don't remember the default: maybe 10 minutes).

---

### Post by WoXa on 2009-03-02
fdisk -l gives:

Cannot open /dev/sda

and  /sbin/fdisk -l gives the same. somehow i thought i didnt need sudo for fdisk-l before formating "d disc". maybe its just me :)

---

