---
title: "Failed to mount local filesystems"
date: 2005-11-03
forum: Desktop Environments
---

### Post by Micro Rotors on 2005-11-03
Ok as the saga goes on, I re-installed Ubuntu but this time I did it without the 64 version, The install went smooth exept for now on boot up I get mount local filesystem ..... FAILED

Ok , What happened and what can I do to get it to mount? :confused: 

Thanks Again
Bill

---

### Post by Rogmo on 2005-11-03
Can you get to the command line?


If so, this could be helpful:

[www.linuxquestions.org/questions/showthread.php?s=&threadid=4580](www.linuxquestions.org/questions/showthread.php?s=&threadid=4580)


Good luck :)

---

### Post by Micro Rotors on 2005-11-03
Yes Im on it now, I am new so I dont know what I am missing, Im on the internet and it all seems ok, Just that [COLOR="Red"]**Failed**[/COLOR] on the bootup screen worries me.

Thanks

---

### Post by Rogmo on 2005-11-03
Interesting problem :)


Try this:

At command line:

> vi /etc/fstab


And copy/paste here the results

---

### Post by Micro Rotors on 2005-11-03
[QUOTE=Rogmo]Interesting problem :)


Try this:

At command line:




And copy/paste here the results[/QUOTE]

Here yeah go;


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/sda2       /media/sda2     ntfs    defaults        0       0
/dev/sda6       /media/sda6     ntfs    defaults        0       0
/dev/sdb1       /media/sdb1     vfat    defaults        0       0
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdc        /media/usb0     auto    rw,user,noauto  0       0
~
~
~
~
~
~
~
~
~
~
"/etc/fstab" [readonly] 13L, 794C                             1,1           All

---

### Post by vegetto on 2005-11-04
I am having the same problem myself and the only effect is that my windows partitions are not listed in "Computer" eventhough they are mounted. the problem started after i did an upgrade from hoary to breezy.

---

### Post by sup on 2005-12-11
well, I went to syslog (got the smae problem here) and this is what it
says ```
localhost kernel [4294697.495000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
```
however when I tried to run ```
sudo e2fsck/dev/hda
5
``` it says it is dangerous to do that on an mounted partition. but since it is the root partition, it is almost impossible to umount it (sudo umount -l /dev/hda5 works somehow, but it is no help, e2fsck does not run either) so a possible solution should be to get oneself a live linux cd, boot from it and then run  e2fsck from it. Too bad I do not have one with me right now.

---

### Post by sup on 2005-12-11
I think I found the problem - at least for me. here goes my /etc/fstab:```
# /etc/fstab: static file system information.
#
#<file system> 	<mount point>   	            <type>  		        <options>      				<dump>  <pass>
proc                        /proc                   	proc    		         defaults        			0       0
/dev/hda6              /               	            ext3    		           defaults,errors=remount-ro 		0       1
/dev/hda5	   /media/data    ext3			            defaults				0	0
/dev/hda1                /media/system		ntfs   	 		umask=0722      			0       0
/dev/hda7                 none            	             swap    		      sw              			0       0
/dev/hdc                  /media/cdrom0   	             udf,iso9660 		      users,ro				0       0
/dev/sda2	/media/usbdisk/asus	ext3			defaults				0	0
/dev/sda6	/media/usbdisk/uploads	ext3			defaults				0	0
//asus/USBDisk	/media/usbdisk/share	smbfs			username=tom,password=,umask=722,uid=1000,gid=1000,rw,user	0	0
/dev/sda1	/media/usbdisk/share	vfat			uid=1000,gid=1000,rw,user			0	0
```
the entries for sda devices stand for my external harddrive which I conncet just from time to time and which usually is not connected during the boot up. When I commented them out, mounting local systems gave ok instead of fail. However, i do not think that "fail" here is anything harmful - everything else mounts the wy it is supposed to.

---

### Post by Ocxic on 2005-12-11
add the option "noauto" (without quotes) to the SDA devices that way they won't be automatically mounted at system startup.

---

### Post by sup on 2005-12-12
yeah, I know about it, but then they would not mount where I want them to mount when they are connected during the start up (and sometimes they are). Or would they? I played with noauto option (and whole fstab, actually) around for a while and that is what I figured out. So it is easier for me to just live on with the the fail message.

---

### Post by Ocxic on 2005-12-12
you should be fine then, it saying fail is abviosly because the external drive is not connected, leving it should be fine, it should still mount when you have the drive connected.

---

