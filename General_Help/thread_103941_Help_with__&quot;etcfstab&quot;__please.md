---
title: "Help with  &quot;/etc/fstab&quot;  please?"
date: 2005-12-15
forum: General Help
---

### Post by handy on 2005-12-15
Hi,
I have just made a fat32 partition on my windoze drive. There are 2 ntfs partitions on the same drive functioning with no prob's.  I can't write to ntfs partitions from Linux, I am under the impression that I can write to fat32, so that's the reason for this little adventure.  
I require a partition where I can share files from linux to winxp.

Could someone please correct the last line in the copy of my fstab file bellow.

I've had a few shots in the dark & get the following error after trying "mount -a"  :-

"mount: mount point /media/winlin does not exist"

----------------------------------------------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc          /proc            proc          defaults        0        0
/dev/hda1           /                   ext3        defaults,errors=remount-ro     0       1
/dev/hda5           none                swap        sw                  0           0
/dev/hdd            /media/cdrom0       iso9660     ro,user,noauto      0           0
/dev/fd0            /media/floppy0      vfat        rw,user,noauto      0           0
/dev/hdc1    	/media/winxp    	ntfs    	umask=0222	    0    	0
/dev/hdc5    	/media/winwork    	ntfs	    umask=0222	    0    	0
/dev/sda1    	/media/winbfast     ntfs    	umask=0222	    0	    0
/dev/hdc?    	/media/winlin	    ????	    umask=????	    0	    0

---------------------------------------------------------------------------------------------------------------------
Also, if you could tell me what the command is that lists the details of the drives, that would be wonderfull.  I have used it once nearly 3 weeks ago, & I can't remember it, or find any reference to it... 

Thankyou for your time.  :-)

handy

---

### Post by alamba on 2005-12-15
/dev/hdc? /media/winlin vfat umask=???? 0 0

You can check what partition is the fat32 one (will answer /dev/hdc?) from an app called parted. I believe this can also be done from the about my computer link on system (not sure about this).

Akshay

---

### Post by jegerjensen on 2005-12-15
Hi, I think I can give you some hints at least.

"mount: mount point /media/winlin does not exist"

Have you created the folder '/media/winlin'  ?
If not,
$sudo mkdir /media/winlin

/dev/hdc?    	/media/winlin	    ????	    umask=????	    0	    0

you need to find out which partition you want to mount:
$sudo fdisk -l /dev/hdc

filesystem type should be vfat

the umask=???  settings I'm not sure about.

cheers

---

### Post by handy on 2005-12-15
Thanks for your help.

It works! 

I had totally forgotten about making "/media/new-directory".  & this time I'll write down that  "$sudo fdisk -l /dev/hdc"  command so as not to waste peoples time.

Cheers,  :KS 

handy

---

### Post by Domie on 2005-12-15
[QUOTE=handy]
/dev/hdc?    	/media/winlin	    ????	    umask=????	    0	    0
[/QUOTE]

I'd try:

/dev/hdc /media/winlin vfat defaults,umask=0111 0 0

This allows you to read and write to the partition. I assume you want to store pictures and other media to it, things that are not executable, since Windows cannot handle Linux progs...

If you want to execute some files too, try

/dev/hdc /media/winlin vfat defaults,umask=0000 0 0

Now you can read, write and execute files. I'd only do this if you really uses executables.

If you want to use a custom setting, just remember that umask=0XXX where XXX is the opposite of chmod. So 777 in chmod (owner=rwx, group=rwx, others=rwx) is umask=0000. 644 in chmod (owner=rw-, group=r--, others=r--) is umask=0133,... You get the point.

I'm only a newbie, but this is a major point of disencourage to many other newbies. I had a hard time with this.

---

### Post by handy on 2005-12-15
Hey thanks Domie,   :-)

I hadn't got around to learning the WHY of the 0222 etc.  (I'm obviously a newB too, there is sooo much new stuff to learn.)
Now it makes sense, I can see how this is VERY important & fundamental knowledge for anyone who has multiple partitions.  Just one wrong character can bring a whole system to a standstill.  Arn't computers fun  :-)

Where did you source this info'?  Sometimes I find it hard to find the info' that I need, I guess that's why this forum is so popular, apart from the great community thing.

Thanks again,

handy

---

### Post by Domie on 2005-12-15
[QUOTE=handy]
Where did you source this info'?  Sometimes I find it hard to find the info' that I need, I guess that's why this forum is so popular, apart from the great community thing.[/QUOTE]

I don't know anymore. I found it on the internet, but can't find it back.

---

### Post by handy on 2005-12-15
No worries Domie,

Thanks anyway,

handy

---

