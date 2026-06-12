---
title: "Boot issues with RAID1 , fstab &amp; binds - The disk drive for /media is not present ..e"
date: 2010-12-30
forum: Desktop Environments
---

### Post by Whyzer on 2010-12-30
Unlike the other posts for the boot error "The device for /media/(name) is not present, my issue seems to be a bit different.

Before I forget I am using Ubuntu 10.04 LTS Desktop

my boot drive is a regular ATA drive, no RAID. I have (2) 400Gb drives that I've created RAIDed using the /System/Administration/Drive Utility (raid1 for data security).
In my fstab (which i'll paste below) I mount the RAID partition as /media/RAID. I created this RAID AFTER I had installed Ubuntu (if that matters). I also have a bunch of bind commands in my fstab to link to other directories I use for a home FTP (so my kids can back up data from college). 

My issue is I get the famous "The disk drive for /media/RAID is not present or ready yet" upon boot. If I do the SKIP it boots to Ubuntu. If I do an immediate mount -a from a terminal it gives me drive errors because the RAID hasn't been started yet. 
I have to go to System/Administration/Drive Utility and manually start the RAID from there. THEN mount -a will work.

My two 400Gb drives are hooked to a SATA PCI controller card inside  the box, but I DIDN'T created the RAID there. 

I've torn down the RAID several times and re-created it with the same results. I've also reinstalled Ubuntu several times, but if I recall (and I am NOT positive on this) but it seemed like the very 1st time I did this I created the RAID1 in the RAID BIOS
and then installed Ubuntu. It showed up correctly (and mounted in Computer, and both drives showed up in fstab with the same UUID (as SDB & SDC) but there wasn't an MD0 for me to mount into my /media as RAID. Hence I tore it down and did it via software like a few posts suggested. 

I am pulling my hair out on this one and could really use some advice on how to get my RAID to start prior to the fstab mount command takes place. 
Thanks!
Jamie
Here's my fstab file
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f3cf58c7-a04f-4044-b5e0-1535a107e85a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0242251e-49cb-48e9-b325-1a03990dc160 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

##Raid
UUID=52974a6d-7374-4262-aadc-a15f81fb8f16   /media/RAID  ext4  auto 0 0

##CDROMS
###32x Burner
/dev/scd0   /media/cdburner    udf,iso9660  user,noauto,exec,utf8 0 0 
#### 50x CDROM
/dev/scd1   /media/cd50x    udf,iso9660  user,noauto,exec,utf8 0 0 


##FTP Binds
## Legal
#/media/RAID/Data/Legal   #/media/RAID/ftp/benny/Legal  none bind 0 0 
#/media/RAID/Data/Legal   #/media/RAID/ftp/lynn/Legal  none bind 0 0 

###Pictures
#/media/RAID/Data/Pictures  #/media/RAID/ftp/benny/Pictures  none bind 0 0 
#/media/RAID/Data/Pictures  #/media/RAID/ftp/lynn/Pictures  none bind 0 0 
#/media/RAID/Data/Pictures  #/media/RAID/ftp/ally/Pictures  none bind 0 0 
#/media/RAID/Data/Pictures  #/media/RAID/ftp/justin/Pictures  none bind 0 0 
#/media/RAID/Data/Pictures  #/media/RAID/ftp/jamie/Pictures  none bind 0 0 
#/media/RAID/Data/Pictures  #/media/RAID/ftp/guest/Pictures  none bind 0 0 

### Music
#/media/RAID/Data/Music  #/media/RAID/ftp/benny/Music  none bind 0 0 
#/media/RAID/Data/Music  #/media/RAID/ftp/lynn/Music  none bind 0 0 
#/media/RAID/Data/Music  #/media/RAID/ftp/ally/Music  none bind 0 0 
#/media/RAID/Data/Music  #/media/RAID/ftp/justin/Music  none bind 0 0 
#/media/RAID/Data/Music  #/media/RAID/ftp/jamie/Music  none bind 0 0 

###Stuff
#/media/RAID/Data/Stuff  #/media/RAID/ftp/benny/Stuff  none bind 0 0 
#/media/RAID/Data/Stuff  #/media/RAID/ftp/lynn/Stuff  none bind 0 0 
#/media/RAID/Data/Stuff  #/media/RAID/ftp/ally/Stuff  none bind 0 0 
#/media/RAID/Data/Stuff  #/media/RAID/ftp/justin/Stuff  none bind 0 0 
#/media/RAID/Data/Stuff  #/media/RAID/ftp/jamie/Stuff  none bind 0 0 

###Upload
#/media/RAID/Data/Upload  #/media/RAID/ftp/benny/Upload  none bind 0 0 
#/media/RAID/Data/Upload  #/media/RAID/ftp/lynn/Upload  none bind 0 0 
#/media/RAID/Data/Upload  #/media/RAID/ftp/ally/Upload  none bind 0 0 
#/media/RAID/Data/Upload  #/media/RAID/ftp/justin/Upload  none bind 0 0 
#/media/RAID/Data/Upload  #/media/RAID/ftp/jamie/Upload  none bind 0 0 
#/media/RAID/Data/Upload  #/media/RAID/ftp/guest/Upload  none bind 0 0 

### Share
#/media/RAID/Data/Share  #/media/RAID/ftp/benny/Share  none bind 0 0 
#/media/RAID/Data/Share  #/media/RAID/ftp/lynn/Share  none bind 0 0 
#/media/RAID/Data/Share  #/media/RAID/ftp/ally/Share  none bind 0 0 
#/media/RAID/Data/Share  #/media/RAID/ftp/justin/Share  none bind 0 0 
#/media/RAID/Data/Share  #/media/RAID/ftp/jamie/Share  none bind 0 0 
#/media/RAID/Data/Share  #/media/RAID/ftp/guest/Share  none bind 0 0

###Yourstuffs
#/media/RAID/Data/Yourstuffs/benny  #/media/RAID/ftp/benny/Yourstuff none bind 0 0
#/media/RAID/Data/Yourstuffs/lynn  #/media/RAID/ftp/lynn/Yourstuff none bind 0 0
#/media/RAID/Data/Yourstuffs/ally  #/media/RAID/ftp/ally/Yourstuff none bind 0 0
#/media/RAID/Data/Yourstuffs/justin  #/media/RAID/ftp/justin/Yourstuff none bind 0 0

---

### Post by Whyzer on 2010-12-30
Oh I forgot to mention. I commented out the BINDS in my fstab to make sure they weren't the boot issue. 
If I do a mount -a without the binds (if they are commented out) no errors, but if I uncomment the bind commands it errors on the binds until I go to computer and double click it (in which I have to put my password in) and do another mount -a

This is just SO WRONG!
Help!
Thanks
Jamie

---

### Post by Whyzer on 2011-01-01
I was able to solve the issue (at least one way). I reinstalled Ubuntu 10.04 using the Alternate Install CD and created the RAID in there, I forgot to format the drive there, but when I got into Ubuntu I used the mkfs command to format it (I forgot to label it, but just used Disk Manager to do that and it all works fine now).
Somehow I still think is can be done within Ubuntu but for the life of me neither Disk Manager or mdadm seemed to work for me despite numerous tries. 
If anyone knows, please update the thread.

---

