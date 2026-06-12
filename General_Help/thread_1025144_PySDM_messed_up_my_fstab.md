---
title: "PySDM messed up my fstab"
date: 2008-12-29
forum: General Help
---

### Post by eriffo on 2008-12-29
I installed PySDM a while ago in order to get some partitions to mount on startup, but it didn't work. What's worse, it messed up my fstab (and I didn't have a backup of it... I know, don't mention it). My FAT32 simply wouldn't mount, my NTFS would mount as read-only, and I think something is wrong with the SWAP partition. Also, the root partition now shows up on my desktop and on nautilus as "7.3 GB Media". I played around with fstab a bit, and got the FAT32 and NTFS partitions working more or less ok, I think (the labels changed, so now some launchers don't work, but that's not a big deal). 
But what really worries me is the SWAP partition. I can't hibernate; I get a message that says "swsusp: cannot find swap device", which I'd never seen before. Also, Ubuntu has been runnig slow ever since, which I think is due to the swap's not working.

I'd hugely appreciate any help as to how to go about fixing this mess.

Here's some info which might be helpful:
sudo fdisk -l
```
Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        3537    28362757+   7  HPFS/NTFS
/dev/sda3            3538        6493    23744070    5  Extended
/dev/sda4            6494        7112     4972117+  db  CP/M / CTOS / ...
/dev/sda5            3538        5473    15550888+   b  W95 FAT32
/dev/sda6            5474        6362     7140861   83  Linux
/dev/sda7            6363        6493     1052226   82  Linux swap / Solaris

```

sudo blkid
```

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-081C" TYPE="vfat" 
/dev/sda2: UUID="22F056BFF05698BD" LABEL="NTFS" TYPE="ntfs" 
/dev/sda4: LABEL="DellRestore" UUID="44F3-2F6D" TYPE="vfat" 
/dev/sda5: LABEL="FAT32" UUID="4890-80CF" TYPE="vfat" 
/dev/sda6: UUID="e379fdde-fd82-45a2-9cc5-8400990f781d" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="c63aeea9-ad3d-48c4-8b93-21e0b57779d3" 

```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> 	<mount point>   	<type>  		<options>      										 <dump>  <pass>
proc                                       /proc          proc         defaults                                                                                                    								0  0  
# /dev/sda6	UUID=e379fdde-fd82-45a2-9cc5-8400990f781d  /   ext3   relatime,errors=remount-ro              									      	0  1  
# /dev/sda7	UUID=c63aeea9-ad3d-48c4-8b93-21e0b57779d3  none       swap     sw    	0  0  
/dev/scd0	/media/cdrom0  	udf,iso9660  user,noauto,exec,utf8 		0  0  
UUID=22F056BFF05698BD	/media/sda2    	ntfs auto,rw,defaults	0  0  
/dev/sda1	/media/sda1    	vfat  noauto  	0  0  
/dev/sda4	/media/sda4    	vfat 	noauto  	0  0  
UUID=4890-80CF	/media/sda5 	vfat  auto,defaults,user,umask=0,iocharset=iso8859-1,shortname=mixed,utf8		0  0  
/dev/sda6	/media/sda6  	ext3  defaults    0  0  
/dev/sda7	/media/sda7    	swap noauto  0  0  

```

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
varrun                756M  112K  755M   1% /var/run
varlock               756M     0  756M   0% /var/lock
udev                  756M   68K  755M   1% /dev
devshm                756M   12K  756M   1% /dev/shm
lrm                   756M   39M  717M   6% /lib/modules/2.6.24-21-generic/volatile
/dev/sda2              28G   22G  5.6G  80% /media/sda2
/dev/sda5              15G   15G  175M  99% /media/sda5
/dev/sda6             6.8G  5.8G  715M  90% /media/sda6
gvfs-fuse-daemon      6.8G  5.8G  715M  90% /home/riffo/.gvfs

```

---

### Post by dcstar on 2008-12-29
> **eriffo said:**
> I installed PySDM a while ago in order to get some partitions to mount on startup, but it didn't work. What's worse, it messed up my fstab (and I didn't have a backup of it... I know, don't mention it).
........
I'd hugely appreciate any help as to how to go about fixing this mess.
........
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> 	<mount point>   	<type>  		<options>      										 <dump>  <pass>
proc                                       /proc          proc         defaults                                                                                                    								0  0  
[B]# /dev/sda6	UUID=e379fdde-fd82-45a2-9cc5-8400990f781d  /   ext3   relatime,errors=remount-ro              									      	0  1  
# /dev/sda7	UUID=c63aeea9-ad3d-48c4-8b93-21e0b57779d3  none  [/B]     swap     sw    	0  0  
/dev/scd0	/media/cdrom0  	udf,iso9660  user,noauto,exec,utf8 		0  0  
UUID=22F056BFF05698BD	/media/sda2    	ntfs auto,rw,defaults	0  0  
/dev/sda1	/media/sda1    	vfat  noauto  	0  0  
/dev/sda4	/media/sda4    	vfat 	noauto  	0  0  
UUID=4890-80CF	/media/sda5 	vfat  auto,defaults,user,umask=0,iocharset=iso8859-1,shortname=mixed,utf8		0  0  
/dev/sda6	/media/sda6  	ext3  defaults    0  0  
/dev/sda7	/media/sda7    	swap noauto  0  0  

```


```
gksudo gedit /etc/fstab
```

And remove the comments on the highlighted lines, then reboot.

---

### Post by eriffo on 2008-12-29
Thanks for the quick reply!
Did it. Now fstab looks like this:
> 
# /etc/fstab: static file system information.
#
# <file system> 	<mount point>   	<type>  		<options>      																								 <dump>  <pass>
proc                                       /proc          proc         defaults                                                                                                    																0  0  
/dev/sda6	UUID=e379fdde-fd82-45a2-9cc5-8400990f781d  /   ext3   relatime,errors=remount-ro              									      	0  1  
/dev/sda7	UUID=c63aeea9-ad3d-48c4-8b93-21e0b57779d3  none       swap     sw    	0  0  
/dev/scd0						/media/cdrom0  	udf,iso9660  	user,noauto,exec,utf8 																									0  0  
UUID=22F056BFF05698BD		/media/sda2    	ntfs        		auto,rw,defaults																										0  0  
/dev/sda1						/media/sda1    	vfat         		noauto                          																									0  0  
/dev/sda4						/media/sda4    	vfat 			noauto  																												0  0  
UUID=4890-80CF				/media/sda5 		vfat  		auto,defaults,user,umask=0,iocharset=iso8859-1,shortname=mixed,utf8									0  0  
/dev/sda6						/media/sda6  	ext3    		defaults     																											0  0  
/dev/sda7						/media/sda7    	swap   		noauto          																											0  0  


But it didn't fix it. Still can't hibernate.

---

### Post by eriffo on 2009-01-01
Any other suggestions?

---

### Post by TransitMan on 2009-01-01
```
# /etc/fstab: static file system information.
#
# <file system> 	<mount point>   	<type>  		<options>      										 <dump>  <pass>
proc                                       /proc          proc         defaults                                                                                                    								0  0  
[B]# /dev/sda6	UUID=e379fdde-fd82-45a2-9cc5-8400990f781d  /   ext3   relatime,errors=remount-ro              									      	0  1  
# /dev/sda7	UUID=c63aeea9-ad3d-48c4-8b93-21e0b57779d3  none       swap     sw    	0  0  [/B]
/dev/scd0	/media/cdrom0  	udf,iso9660  user,noauto,exec,utf8 		0  0  
UUID=22F056BFF05698BD	/media/sda2    	ntfs auto,rw,defaults	0  0  
/dev/sda1	/media/sda1    	vfat  noauto  	0  0  
/dev/sda4	/media/sda4    	vfat 	noauto  	0  0  
UUID=4890-80CF	/media/sda5 	vfat  auto,defaults,user,umask=0,iocharset=iso8859-1,shortname=mixed,utf8		0  0  
/dev/sda6	/media/sda6  	ext3  defaults    0  0  
/dev/sda7	/media/sda7    	swap noauto  0  0
```

You have two listings for /dev/sda6 and /dev/sda7
Remove the first two listings I have **BOLDED THE TEXT ON**, save and reboot.
Then tell us what happened.

---

### Post by eriffo on 2009-01-01
fstab now is:
> 
# /etc/fstab: static file system information.
#
# <file system> 	<mount point>   	<type>  		<options>      																								 <dump>  <pass>
proc                                       /proc          proc         defaults                                                                                                    																				0  0  
/dev/scd0						/media/cdrom0  	udf,iso9660  	user,noauto,exec,utf8 																									0  0  
UUID=22F056BFF05698BD		/media/sda2    	ntfs        		auto,rw,defaults																										0  0  
/dev/sda1						/media/sda1    	vfat         		noauto                          																									0  0  
/dev/sda4						/media/sda4    	vfat 			noauto  																												0  0  
UUID=4890-80CF				/media/sda5 		vfat  		auto,defaults,user,umask=0,iocharset=iso8859-1,shortname=mixed,utf8													0  0  
/dev/sda6						/media/sda6  	ext3    		defaults     																											0  0  
/dev/sda7						/media/sda7    	swap   		noauto    			


but nothing happened. :(

---

### Post by Loosewheel on 2009-01-01
eriffo,
I don't know what PySDM is, but the man page for fstab says: "Each filesystem is described on a separate line". And here is a working fstab file: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aac5c61b-ec7e-467a-b557-f646478e0ed5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=661b0305-bb78-475f-a715-de4555078f73 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Notice that "/dev/sda1" is commented out, and below it is the file system, mount point, etc....all on one line.

---

### Post by TransitMan on 2009-01-01
OK. I've gone through what you have, compared it to my fstab and came up with the below in the code box.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>   <options>   <dump>  <pass>
proc  /proc  proc defaults 0  0         
/dev/scd0	/media/cdrom0  	udf,iso9660  user,noauto,exec,utf8 		0  0  
# Entry for /dev/sda2 :
UUID=22F056BFF05698BD	/media/sda2    	ntfs auto,rw,defaults	0  0  
# Entry for /dev/sda1
/dev/sda1	/media/sda1    	vfat  noauto  	0  0  
# Entry for /dev/sda5
/dev/sda4	/media/sda4    	vfat 	noauto  	0  0  
# Entry for /dev/sda5
UUID=4890-80CF	/media/sda5 	vfat  auto,defaults,user,umask=0,iocharset=iso8859-1,shortname=mixed,utf8	0  0  
# Entry for /dev/sda6
UUID=e379fdde-fd82-45a2-9cc5-8400990f781d  /   ext3   relatime,errors=remount-ro        0  1  
# Entry for /dev/sda7
UUID=c63aeea9-ad3d-48c4-8b93-21e0b57779d3  none  swap sw  0  0

```

Give it a go and post back.

---

### Post by eriffo on 2009-01-01
Thanks, TransitMan!
Gave it a try, and it stopped the root partition from showing up on the desktop. The FAT32 and NTFS partitions seem to be working fine as well.
But still no luck with swap; can't hibernate. The error it shows is:
> 
swsusp: Cannot find swap device try swapon -a

Did that and it yields:
> 
swapon: cannot canonicalize /dev/disk/by-uuid/c63aeea9-ad3d-48c4-8b93-21e0b57779d3: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/c63aeea9-ad3d-48c4-8b93-21e0b57779d3: No such file or directory

And the swap partition now shows on blkid as
> 
/dev/sda7: TYPE="minix" 

when it used to be
> 
/dev/sda7: TYPE="swap" UUID="c63aeea9-ad3d-48c4-8b93-21e0b57779d3"


---

### Post by TransitMan on 2009-01-01
> **eriffo said:**
> Thanks, TransitMan!
Gave it a try, and it stopped the root partition from showing up on the desktop. The FAT32 and NTFS partitions seem to be working fine as well.
But still no luck with swap; can't hibernate. The error it shows is:

Did that and it yields:

Ok, re-edit fstab and change this:
```
# Entry for /dev/sda7
UUID=c63aeea9-ad3d-48c4-8b93-21e0b57779d3  none  swap sw  0  0
```
to this:
```
# Entry for /dev/sda7 :
/media/sda7   none  swap sw  0  0
```

See what goes, let me know.

---

### Post by eriffo on 2009-01-02
I think you meant
```

# Entry for /dev/sda7
/dev/sda7   none  swap sw  0  0

```
Which I think actually worked; ubuntu seems to be running faster, and it hibernates, well, kinda: It won't resume, it's as though I had shut down instead of hibernating. But that's seems to be a different issue ([http://ubuntuforums.org/showthread.php?t=781809](http://ubuntuforums.org/showthread.php?t=781809)). Also when i do swapon -a it shows nothing, which is good.
Anyway, thanks for your time!

---

### Post by TransitMan on 2009-01-02
Glad I was able to help.
Hope you get the "hibernate" issue fixed.

---

