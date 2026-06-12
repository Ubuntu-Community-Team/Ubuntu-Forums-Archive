---
title: "Ext Hard drive permissions"
date: 2006-09-10
forum: Desktop Environments
---

### Post by freddy metz on 2006-09-10
Im trying to give the other users on the pc permission to read and write to an external hard drive.
Im having trouble with the chown and chmod commands. My external hard drive is called trekstor 2 and terminal keeps giving me the error 
```
chown: cannot access `2': No such file or directory
```
I cant rename the drive, is the space causing the trouble?

---

### Post by jimmymac on 2006-09-10
I _think_ that you need to type it such that:

trekstor\ 2/

The alternative is just type the first few letters and press tab, it should autocomplete.  What a brilliant feature!

HTH

Jimmy

---

### Post by lukew on 2006-09-10
It dont like the space. I would rename it if you could. You could try putting it like 

"trekstor 2" or 'trekstor 2'

However you should be doing this on a directory of some sort and not on the actual HD.

sudo chmod 777 "/media/trekstor 2"

I hope this helps.

Luke

---

### Post by freddy metz on 2006-09-10
the autocomplete feature works when i try ```
ls -ld /media/TREKSTOR\ 2/

```

but when i try ```
sudo chown -R freddy:freddy /media/TREKSTOR\ 
```

it only completes as far as "TREKSTOR\"(and i have to enter the 2 myself) and nothing happens when i press enter.

Also when i try ```
sudo chmod 777 "/media/TREKSTOR 2"/

``` it autocompletes but nothing happens.

---

### Post by freddy metz on 2006-09-12
anyone? :(

---

### Post by rogier.de.groot on 2006-09-12
In my experience, problems with drive access are more likely caused by the way your drive gets mounted than the directory permissions. Could you post the output of running the "sudo mount" command? And the group membership info ("groups") of the user you're using?
BTW, which kind of filesystem is on the external harddisk??

---

### Post by freddy metz on 2006-09-12
```

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/TREKSTOR 2 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/sdb1 on /media/TREKSTOR 1 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
freddy@freddy-desktop:~$

```

and the groups output (if thats what you mean)
```
freddy adm dialout cdrom floppy tape audio dip video plugdev lpadmin scanner admin

```

Its formatted as fat32 and im using ext3 on linux.

---

### Post by Alex1770 on 2006-09-12
Using file completion (tab) to find a file with a space in is not that reliable because it needs the shell to understand what is going on. In the case of your command, sudo chown -R freddy:freddy /media/TREKSTOR\ [tab], it doesn't look like the shell understands it (it doesn't complete correctly). Is it possible to rename the disk to be without a space?

Or you could try
```

sudo chmod -R a+rwX '/media/TREKSTOR 2'

```
(There were stray backslashes and forward slashes in the version of this you quoted above.)
But maybe a different solution (that works automatically when you plug in the disk) is better in the long run.

When you say nothing happens, what exactly is the output?

---

### Post by rogier.de.groot on 2006-09-12
Are the other users member of the plugdev group? That's what made them able to read/write to a USB flash disk for me. Making them members of the audio group so they have sound is also usefull.

---

### Post by xyz on 2006-09-12
My external HD's named "usbdisk" and when I type "mount" in a console, this is how it reads to have read/write permissions:
> /dev/sda5 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=007,iocharset=utf8)


which is the same as yours except it works for me! Strange!

It's been a while so I don't remember for sure but I seem to recall right clicking on my external HD's icon, went Properties, then Permissions and checked boxes to allow for Permissions!!

---

### Post by yota on 2006-09-12
Hi,

I think that the problem is in the umask parm that is set in fstab:
> 
/dev/sda1 on /media/TREKSTOR 2 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

umask 077 means that only the owner can access the mounted drive, so if you want everyone to access it change to 'umask=000'
> 
from man mount
...
umask=value
              Set the umask (the bitmask  of  the  permissions  that  are  not
              present).  The default is the umask of the current process.  The
              value is given in octal.
...


Hope this helps

---

### Post by freddy metz on 2006-09-12
all the users are in the plugdev group.

"sudo chmod -R a+rwX '/media/TREKSTOR 2'" Do i have to replace rwX with the numeric values (777)?

Either way i just get 
```
freddy@freddy-desktop:~$ sudo chmod -R a+rwX '/media/TREKSTOR 2
>

```
 What is supposed to happen after i enter that command?

---

### Post by Jussi Kukkonen on 2006-09-12
> **freddy metz said:**
> all the users are in the plugdev group.

"sudo chmod -R a+rwX '/media/TREKSTOR 2'" Do i have to replace rwX with the numeric values (777)?

Either way i just get 
```
freddy@freddy-desktop:~$ sudo chmod -R a+rwX '/media/TREKSTOR 2
>

```
 What is supposed to happen after i enter that command?

You are missing a ' in the end. I really suggest you rename the mount points to something with no whitespace. You are going to have troubles like this till the end of time if you don't.

Ask if you need help.

---

### Post by freddy metz on 2006-09-12
the trouble is that i cant rename it..


and thanks yota, im going to try that now!

---

### Post by Jussi Kukkonen on 2006-09-12
> **freddy metz said:**
> the trouble is that i cant rename it..

Not true. read/write permissions of the mounted partition are not related to the normal file permissions of the mount point. You can always move a mount point.

Something like this should work:
```
sudo umount /dev/sda1
sudo umount /dev/sdb1
sudo mv /media/TREKSTOR\ 1 /media/trekstor1
sudo mv /media/TREKSTOR\ 2 /media/trekstor2
sudo nano /etc/fstab
### edit fstab so that the mount points are /media/trekstor1 and /media/trekstor2
sudo mount /media/trekstor1
sudo mount /media/trekstor1

```

---

### Post by freddy metz on 2006-09-12
Okay i edited it like this
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/trekstor1 vfat
/dev/sdb1       /media/trekstor2 vfat

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0


```
Now im not the owner anymore (drwxr-xr-x) its group and owner is ROOT so everyone can read and execute but only root can write.  How do i change this now? Yotas version might work but i dont know what exactly to type into the terminal...

---

### Post by Jussi Kukkonen on 2006-09-12
It's been a while since I played with Windows filesystems, but try this in fstab...
```
/dev/sda1  /media/trekstor1    vfat    user,fmask=0111,dmask=0000   0   0
```

the options mean that all users can mount /media/trekstor1, and that the file permissions should allow anyone to do pretty much anything. That's not too safe, so if it works you might want to mount the disk so that only your user has write access (if that's what you want) -- wiki.ubuntu.com has instructions, search for "mount windows"...

---

### Post by freddy metz on 2006-09-12
okay i have it like this now
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/trekstor1 vfat user,fmask=0111,dmask=0000   0   0
/dev/sdb1       /media/trekstor2 vfat user,fmask=0111,dmask=0000   0   0

```
and i umounted and remounted them but theyre still as ROOT.

---

### Post by Jussi Kukkonen on 2006-09-12
Yes, they're owned by root, but the files inside the partitions should have very liberal permissions (if I remembered the options right)... what kind of permissions do files in */media/trekstor1* have?

If you want to own the files, take a look at the howtos in the wiki, I don't remember the options.

---

### Post by freddy metz on 2006-09-12
wow thanks! i guess problem fixed :)

The only minor thing is that although the trekstor drives are renamed without spaces theyre still shown with spaces (e.g trekstor 1) in the places bar in file browser. 

thanks to everyone who contributed in this thread!

---

