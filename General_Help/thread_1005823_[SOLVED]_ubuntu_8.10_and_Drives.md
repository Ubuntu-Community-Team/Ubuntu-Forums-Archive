---
title: "[SOLVED] ubuntu 8.10 and Drives"
date: 2008-12-08
forum: General Help
---

### Post by maustin2 on 2008-12-08
After installing the system and performing an upgrade I am getting the following info from the partition manager

first hard drive is sdb
second hard drive is sdc
usb flash drive is sda

Initially these were all in the correct sequence. I am not sure what changed the sequence. I am not able to mount the usb or see the second hard drive except in the partition manager. The usb will not automount any more.

I have attempted to correct this condition by editing fstab to no avail.

Help is needed!!!:confused:

---

### Post by drs305 on 2008-12-08
If you post the results of the following commands perhaps we can help you out:
```

sudo blkid
cat /etc/fstab
mount

```

If you fstab references /dev/sdX instead of UUID's I would strongly recommend switching over. We can help with that as well.

---

### Post by maustin2 on 2008-12-08
The results fo the three commands  are in sequence below.
Thanks for the reply.

/dev/sda1: UUID="62329c5c-9073-48a5-a5bb-9a0e1e2704f9" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="efd0bff4-8943-420f-b47e-ec0714cea2c7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="4be6b525-61a5-4c4a-9207-eb08dd9e98bf" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="44897b94-cfeb-4d95-b83d-744412dfd095" 
/dev/sdc2: UUID="58357d85-18d5-4db5-af8c-bfc65740ce3c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="6d9eb3b2-bc69-49fe-8791-7f0f80ce144f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc4: UUID="604596f0-19a5-4bb1-b740-748bb7107f83" SEC_TYPE="ext2" TYPE="ext3" 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=efd0bff4-8943-420f-b47e-ec0714cea2c7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=44897b94-cfeb-4d95-b83d-744412dfd095 none            swap    sw              0       0
/dev/sdb1							
UUID=4be6b525-61a5-4c4a-9207-eb08dd9e98bf   		  ext3  		  	     0	     2
/dev/sdb2
UUID=58357d85-18d5-4db5-af8c-bfc65740ce3c		  ext3				     0       2
/dev/sdb3
UUID=6d9eb3b2-bc69-49fe-8791-7f0f80ce144f		  ext3				     0       2	
/dev/sdb4
UUID=604596f0-19a5-4bb1-b740-748bb7107f83		  ext3				     0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdc1
UUID=62329c5c-9073-48a5-a5bb-9a0eIe2704f9 		  ext3


/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/monty63/.Private on /home/monty63/Private type ecryptfs (rw,ecryptfs_sig=27f26f028ce60f37,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,user=)
gvfs-fuse-daemon on /home/monty63/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=)

---

### Post by drs305 on 2008-12-08
This fstab needs some serious work!   ;-)  The only device that appears to be correctly mounted is / (which I guess if you can have only 1, this is the one to have).

Where there are usually comments designating the following mountpoints, either the comment # symbol is missing or there is no mount point designated. One of the problems with fstab is that the comments are not updated, so you can't really trust them to be accurate. I have updated the comments to reflect the current designations of your devices. These (sda1, sdb1, etc) can change, so never rely solely on the commented device name when editing fstab.

I have updated the fstab to the standard conventions, but there are still things that need to be worked out. There are no mountpoints designated for most of the devices, and these will have to be entered where indicated.

I have created the standard comments on the line before each entry, and they match the results of the blkid command. Here is where we are at the moment:

First, mountpoints. Anywhere you see a [COLOR="Sienna"]/mountpoint[/COLOR] you are going to have to change this to something else. Normally the mountpoints are in /media, so for the first one you may make it something like "/media/mydata". Next, you will probably want to change the ownership of the mountpoint to yourself. Finally, you may want to change the permissions. The command I use will be to give you unlimited access, your group rx, and others none (750).

So, you need to make or designate (if they already exist), mountpoints for sda1, and sdc 1,2,3,4. Do this for each one. I am assuming your username is 'monty63':
```

sudo mkdir /media/pick.a.name.for.mountpoint
sudo chown -R monty63: /media/pick.a.name.for.mountpoint
chmod -R 750 /media/pick.a.name.for.mountpoint

```
Example:
sudo mkdir /media/mydata
sudo chown -R monty63: /media/mydata
chmod -R 750 /media/mydata
Note: You can put all the mountpoints on the same line and run the commands just once if you wish, e.g.  sudo mkdir /media/mydata  /media/myfiles  /media/myplaces )

Next, make a backup of your current fstab then open it for editing. I'm assuming gedit but if you are using kubuntu it would be 'kdesudo kate':
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```

Replace the entire contents with:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0

# /dev/sdb1
UUID=efd0bff4-8943-420f-b47e-ec0714cea2c7 / ext3 relatime,errors=remount-ro 0 1
# /dev/sdb5
UUID=44897b94-cfeb-4d95-b83d-744412dfd095 none swap sw 0 0

# /dev/sda1
UUID=62329c5c-9073-48a5-a5bb-9a0eIe2704f9 [COLOR="Sienna"]/mountpoint1[/COLOR] ext3 defaults,users 0 2

# /dev/sdc1
UUID=4be6b525-61a5-4c4a-9207-eb08dd9e98bf [COLOR="Sienna"]/mountpoint2[/COLOR] ext3 defaults,users 0 2
# /dev/sdc2
UUID=58357d85-18d5-4db5-af8c-bfc65740ce3c [COLOR="Sienna"]/mountpoint3[/COLOR] ext3  defaults,users 0 2
# /dev/sdc3
UUID=6d9eb3b2-bc69-49fe-8791-7f0f80ce144f [COLOR="Sienna"]/mountpoint4[/COLOR] ext3 defaults,users 0 2
# /dev/sdc4
UUID=604596f0-19a5-4bb1-b740-748bb7107f83 [COLOR="Sienna"]/mountpoint5[/COLOR] defaults,users ext3 0 2

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

```

Once you have made the mountpoint entries, save the fstab file and run the following:
```

sudo mount -a

```
If there are no errors, you won't see anything and all the partitions will be mounted. I've made a bunch of changes and may have overlooked something. If you get any error messages, post them here and we can tweak the fstab.

Note: The usb drive should mount on it's own and not need an fstab entry. I would prefer placing a # symbol in front of the entire usb line (the line immediately below # /dev/sda1) and see if you can get it to mount without having it listed in fstab.

---

