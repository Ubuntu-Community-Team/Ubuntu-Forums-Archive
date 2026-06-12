---
title: "Mounting Hell!!!"
date: 2005-12-27
forum: General Help
---

### Post by rampage on 2005-12-27
ok I have had the worst experience ever when mouting things with kubuntu

1) what is the program that kubuntu uses to mount things with because I have now taken my optical drive out of my fstab and still it mounts itseft under /media/hda and I don't have that entered anywhere in fstab

2) I was trying to change my /dev/hda media/hda (which is my cdrom) to /dev/cdrom media/cdrom but still somehow it is still mounting as media hda even after I removed the hda directory from media

3) I don't know what the hell I have done but now every cd I put in the device now has cdrom name displayed under it not the name of the cd

4) also if I mount more than one device and the icon pops up on my desktop the previous "mountee" looses its ability to launch with an action or its option to "unmount/saftly remove" I have to go into comman and umount it

if anyone can hep me out that would be great I would love to get this mounting stuff under control

thanx a bunch everyone

---

### Post by bin on 2005-12-27
[QUOTE=rampage]2) I was trying to change my /dev/hda media/hda (which is my cdrom) to /dev/cdrom media/cdrom but still somehow it is still mounting as media hda even after I removed the hda directory from media[/QUOTE]

To save time here, please post your FSTAB and some system specs relating to your drives - SATA, IDE, SCSI???? hda is always your hard drive in an IDE system

in light

bin

---

### Post by rampage on 2005-12-27
ok I have 2 SATA drives 120 & 160 with a few partitions this is the fstab with the cdrom line taken out and it still mounts the damn thing... I don't think I have ever had an issue like this before... thanx guys

# /etc/fstab: static file system information.
#
# <file system>  <mount point>   <type>  	<options>      						         <dump>  <pass>
proc		 /proc 		 proc 	 	defaults			     				      0  0

### < Linux File System >
/dev/sda8	 / 		 ext3	 	defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser         0  1
/dev/sda10	 /home 		 ext3	 	defaults,atime,auto,rw,dev,exec,suid,nouser                           0  2
/dev/sda9        none		 swap	 	sw								      0  0


### < Windows Partitions >
/dev/sda1       /media/sda1      ntfs    	defaults,uid=1000,gid=0,noauto,ro,users			     	      0  0
/dev/sda6       /media/sda6      ntfs    	defaults,uid=1000,gid=0,noauto,ro,users			              0  0
/dev/sdb1       /media/sdb1      ntfs    	defaults,uid=1000,gid=0,auto,ro,users			              0  0
/dev/sda7       /media/sda7      vfat    	defaults,uid=1000,gid=0,auto,rw,users			              0  0


### < Removable Media >
/dev/fd0        /media/floppy0			defaults,uid=1000,gid=0,noauto,users				      0  0
/dev/sdc	/media/sdc	 vfat		defaults,uid=1000,gid=0,auto,users				      0  0
/dev/sdd        /media/sdd       vfat           defaults,uid=1000,gid=0,auto,users                                    0  0

---

### Post by rampage on 2005-12-27
the line I have been trying to implement for my cdrom is

/dev/cdrom      /media/cdrom  	 udf,iso9660    defaults,uid=1000,gid=0,auto,users    			              0  0

---

