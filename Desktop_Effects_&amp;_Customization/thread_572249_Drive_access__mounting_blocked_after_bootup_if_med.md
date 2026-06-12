---
title: "Drive access / mounting blocked after bootup if media is present"
date: 2007-10-10
forum: Desktop Effects &amp; Customization
---

### Post by perixx on 2007-10-10
Hello ! Nasty problem - help appreciated!!!


When I boot the computer with USB stick inserted or Audio CD in the drive, the stick won't be auto-mounted and is inaccessible e.g. for saving sites under FF, unless I replug it - also Audio CD's aren't being auto-played and are only 'auto-mounted' - desktop icon 'Audio-CD' included (which is ok), but cannot be accessed nonewhatsoever, unless they're re-inserted. 

I get 2 error windows in either case: 'Cannot mount volume. Invalid mount option when attempting to mount the volume.' and sth. like 'mounting failed. Couldn't mount 'Audio-CD'. Unknown error.'

I should be able to access those drives, even if they're already present at bootup...?!

What can be done?


perixx

---

### Post by Rupertronco on 2007-10-10
Post your mtab and fstab. We'll go from there.

---

### Post by perixx on 2007-10-10
Hi Rupertronco!

I suppose you're referring to the 


/media/.hal-mtab  - file

/dev/sda1	1000	0	vfat0 noexec,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,exec	/media/disk



/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=120247a9-3e01-440c-b2cf-cb70e9321988 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=e37de1b8-9e7f-4e53-b8d7-40cd5bbe8da7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



/etc/mtab

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0



here you go!

---

### Post by perixx on 2007-10-11
Well Rupertronco, 

here are the file contents.... what do you make of it?

perixx

---

### Post by Rupertronco on 2007-10-12
run fdisk -l in a terminal and post the output of that i'm guessing the parameters of mtab aren't correctly configured. make sure all of your usb devices are plugged in when you do that. (i'm assuming they were with your mtab post as well, if they weren't plug them in and repost mtab)

the entry for sda1, which i'm assuming is your usb hd looks fine mine is identical with a different mount point. are you sure the file system is vfat? have you ever formatted that drive?

---

### Post by Rupertronco on 2007-10-12
change your bottom line in your mtab to this, also make sure to save a backup of the current configuration. 

/dev/sda1 /media/disk vfat rw,nosuid,nodev,fmask=0111,dmask=0000 0 0

---

### Post by perixx on 2007-10-13
Hello again, Rupertronco!


Thanks for your help on this!

First, I noticed a few more things so far: 


-The USB-stick is not auto-mounted when it's already plugged and the PC is booted; it's got a link on the desktop, but can only be accessed in Thunar, after I rightclick/mount onto that link.... I've just applied your suggested alternate code-line and will try to restart, to see if anything changes. Btw., 'sda1' is the 64MB stick, not an USB-drive!

Apart froim that, the stick is always just recognized as 'disk' under /media and in most applications, unlike in Thunar's main tree and on the desktop - which is both confusing and annoying. Can I simply change that by editing the according line in the 'mtab' file?



-When I boot with an Audio-CD inside the DVD-drive; it won't autostart Gxine, but I cannot access it via the link on my desktop then, nor via Thunar. If I do that, I get the error messages, suggesting an invalid mount option and that the drive cannot be mounted ('unknown error'). I have to re-insert the CD, which triggers the next problem.

The Audio-CD starts autoplay of Gxine, which only produces second-wise interrupted playback. 
It then is also impossible to view the directory of an Audio-CD. This problem even remains after I quit Gxine (unlike when inserting DVD's, which trigger autostart of Gxine, but cannot be played back yet, due to missing codecs). So maybe there's a problem with Gxine permanently grabbing the drive after playback..?  


Anyway, here's the new mtab for you:

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/disk vfat rw,nosuid,nodev,fmask=0111,dmask=0000 0 0



And the results of 'fdsik -l':

Disk /dev/sda: 64 MB, 64204800 bytes
18 heads, 32 sectors/track, 217 cylinders
Units = cylinders of 576 * 512 = 294912 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         218       62640    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(933, 17, 32) logical=(217, 9, 32)


greetz,

perixx

---

### Post by perixx on 2007-10-16
Well, Rupertronco...

Your turn!
:]

perixx

---

### Post by Rupertronco on 2007-10-16
I'll be able to read your post when I'm done with this lab. I haven't forgotten about you!

---

### Post by perixx on 2007-10-16
Thanks, good to hear that ^^

---

### Post by Rupertronco on 2007-10-16
You can always change the mount point by editing the second parameter of the mtab file. I dont use /media/disk-x for any of my mount points. Just change that parameter to wherever you'd like the drive mounted. Example I use /external/music for my music external HD.

What was the result of you changing your mtab?

---

### Post by perixx on 2007-10-17
To be perfectly honest, I'm not sure if we're talking about the same thing..? I couldn't see any change, because:

I edited the mtab file as you told, but it was re-written in the old manner by the system again. Will this not also happen to an altered /media/disk mountpoint? When I start the system without the stick plugged, this line in mtab doesn't even exist, so I suppose, it's re-created at every boot-up - isn't it?

I changed it to /media/memorystick -

letssee, if that stays persistent at next boot...


perixx

---

### Post by perixx on 2007-12-08
If I'm not mistaken, editing the mtab file will have no effect, since it's updated by the system automatically. So editing the '/etc/fstab' file would be what I want to do, if I'd like to have my memory-stick auto-mounted...

> UUID=C680-0000	  /media/sda1	auto			vfat	defaults	

would adding this line to fstab auto-mount my stick when already plugged at boot time and still auto-mount when just being plugged into the running system?

perixx

---

### Post by perixx on 2007-12-12
*bumpagain*

---

### Post by perixx on 2008-01-04
*bumpagainagain*

how would a correct auto-mounting entry for my USB stick in /etc/fstab look like?

perixx

---

