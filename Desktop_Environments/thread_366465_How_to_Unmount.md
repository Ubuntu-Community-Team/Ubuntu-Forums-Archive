---
title: "How to Unmount"
date: 2007-02-20
forum: Desktop Environments
---

### Post by cornellpd on 2007-02-20
I have this posted as a reply in someone else's resoved issue, but it isn't being seen-
I have icons of three hard drive partitions on my desktop.  I guess I am somehow mounted on these, but I am able to get rid of them by 
sudo umount /media/sda1/  
etc for each one.  The problem is, each time I reboot-they come back.  The must be mounting in some setup config, maybe?

I do not know how to permanantly get rid of them, nor do I know the language well enough to attempt.  I am using Ubuntu, with gnome 2.14.  Any help?  Thanks.

---

### Post by kerry_s on 2007-02-20
There auto mounted, just change your /etc/fstab and add>  ,noauto,user

sudo gedit /etc/fstab

/dev/hdb1 /media/hdb1     jfs     defaults,user,noauto        0       0

You also want to change the end of the line where it has a number change it to 0 so it doesn't bother checking it. On each start.

---

### Post by cornellpd on 2007-02-20
First-thanks
I understand what you mean by going to gedit, and I know that sudo is root (right?)
I was able to change the ones to zeros at the end of the "offending windows" partitions.
What do you mean by change my /etc/fstab and add >,noauto.user    ?
This is what it looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/sda4       /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

I have dual booted winxp and ubuntu 6.06
Winxp is for my wife-and I'm trying not to distort or damage it on account of her.
Thanks again.

OK I changed the purple line:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
[COLOR="Red"]/dev/sda4       /media/sda4     vfat    defaults,user,noauto 0 0 [/COLOR]      
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Is this ok-it worked to get rid of the icon and winxp still boots.  If it's something I shouldn't do-I'll be asking for the fix!!
Thanks again.

---

### Post by cornellpd on 2007-02-21
OK-issue is resolved...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,user,noauto 0       0
/dev/sda2       /media/sda2     ntfs    defaults,user,noauto 0       0
/dev/sda4       /media/sda4     vfat    defaults,user,noauto 0 0       
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Everything seems to be working fine.  Now where do I learn all the commands for the terminal?

i.e.:gedit, sudo, bin, bash -all of that good stuff.

Thanks one more time!!

---

### Post by kerry_s on 2007-02-21
Sorry, i didn't mean change the line exactly like mine, i should have asked you to post yours first. You need to just add the words to what was there.->

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda7 / ext3 defaults,errors=remount-ro 0 1
/dev/sda1 /media/sda1 vfat defaults,user,noauto,utf8,umask=007,gid=46 0 0
/dev/sda2 /media/sda2 ntfs defaults,user,noauto,nls=utf8,umask=007,gid=46 0 0
/dev/sda4 /media/sda4 vfat defaults,user,noauto,utf8,umask=007,gid=46 0 0
/dev/sda8 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0


That tells the system not to automount the drive. "user" will let you mount the drive with out being root, for if you want to access them.

linux-commands-> [http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

