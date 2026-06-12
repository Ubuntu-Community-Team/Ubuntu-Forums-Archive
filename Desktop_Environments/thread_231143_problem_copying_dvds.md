---
title: "problem copying dvds"
date: 2006-08-07
forum: Desktop Environments
---

### Post by katana2k on 2006-08-07
hey guys, I  have a DL DVDRW drive and a DVD-ROM/CDRW in my computer. When I put a dvd movie into either drive totem pops up and plays them without a problem. The problem is, under Places > Computer, only one of the drives shows up (often the DVD-RW) and the other drive (the DVD-ROM) doesnt appear unless I double click the first drive. I would like to copy a dvd from the DVD-ROM to a blank DVD in the DVD-RW but the icon doesnt show most of the time. 

I would also like to have a shortcut to whatever media i have in either drive on the desktop when there is a disk present.

here is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> 	<mount point>   	<type>  		<options>       						<dump>  <pass>

proc            		/proc           		proc    		defaults        							0       	0
/dev/hda1       		/               		ext3    		defaults,errors=remount-ro 				0       	1
/dev/hda5       		none            		swap    		sw              							0       	0

/dev/hdb1       		/media/windows  	ntfs    		defaults,users,nls=utf8,umask=007,gid=46  0       	0

/dev/hdc        		/media/cdrom0   	udf,iso9660 	user,noauto     						0       	0

#This was added to see if i could fix the other dvd drive mounting issue

/dev/hdd        		/media/cdrom1   	udf,iso9660 	user,noauto     						0       	0

#this was added to see if the floppiness would look right

dev/fd0			/media/floppy0	auto		defaults								0		0


```

if anybody has any suggestions, they would be greatly appreciated :D

---

