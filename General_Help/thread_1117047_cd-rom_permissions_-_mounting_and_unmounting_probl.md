---
title: "cd-rom permissions - mounting and unmounting problem"
date: 2009-04-05
forum: General Help
---

### Post by rocketship on 2009-04-05
This is driving me nuts.  With two users logged into my system, if one user inserts a DVD and then tries to eject it, the system says that its locked by the other person.  I have to log into the other account and eject it from there.  Are my permissions screwed up?

Here's /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> 				<mount point>   		<type>  <options>      			<dump>  <pass>
proc            				/proc           		proc    defaults       			0       0
#
# /dev/sdc7
UUID=98fc1423-3d68-4d0d-ae1b-dbf35b0dae73 	/               		xfs     relatime       			0       1
#
# /dev/sdc1
UUID=bad8c393-7ddb-4e2e-9831-b4577085d7f4 	/boot           		ext3    relatime       			0       2
#
#/dev/sdc5	
UUID=a30e2749-a685-4041-8546-d6c333ff61d3 	/home           		xfs	relatime  			0	1
#
# /dev/sdc6
UUID=6dbdbaa3-175a-4a42-8f66-36078b716191	/var/lib/mythtv/recordings	xfs	relatime			0	1
#
# /dev/sdd1
UUID=0A3CB37C3CB360FD				/media/Windows_Old		ntfs	ro,user,auto			0	1
#
# /dev/sdb2
UUID=60FC1D05FC1CD75E				/media/Windows_New		ntfs	ro,user,auto			0	1
#
# /dev/sdc2
UUID=f4fd1cc5-ddcc-4b0e-b0ef-1a9e8cbf718a 	none            		swap    sw              		0       0
#
/dev/scd0       				/media/cdrom0   		iso9660,udf user,noauto,exec,utf8 	0       0
```

and the permissions for /media:
```
drwxr-xr-x  9 root  root  4096 Apr  4 14:42 .
drwxrwxrwx 23 root  root  4096 Apr  1 08:39 ..
-rw-r--r--  1 root  root     0 Apr  4 14:42 .hal-mtab
-rw-------  1 root  root     0 Apr  2 22:37 .hal-mtab-lock
drwxr-xr-x  2 root  root     6 May 10  2008 Backup
drwxr-xr-x  2 root  root     6 Mar 22 17:45 CardReader
drwxrwxrwx  1 root  root  8192 Jul 27  2008 Windows_New
drwxrwxrwx  1 root  root  4096 Mar 18 11:37 Windows_Old
lrwxrwxrwx  1 root  root     6 May  4  2008 cdrom -> cdrom0
dr-xr-xr-x  1 root  root  2048 Dec 31  1969 cdrom0
drwxr-xr-x  2 root  root     6 Mar 18 14:42 iso
drwxr-xr-x  2 sclay sclay    6 Nov 25 23:33 jungledisk

```

Any ideas?

-RS

---

