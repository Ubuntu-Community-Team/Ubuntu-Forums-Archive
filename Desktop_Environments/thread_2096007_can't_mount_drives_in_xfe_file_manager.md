---
title: "can't mount drives in xfe file manager"
date: 2012-12-18
forum: Desktop Environments
---

### Post by rolypolycat on 2012-12-18
Hello!

I tried this question in the Bodhilinux forums, but no luck, so I hope someone here can help me. I use Bodhilinux with the enlightenment window manager. I tried the enlightenment file manager, and it doesn't recognize my cdrom or dvd drives. Decided I didn't like it anyway, so I switched to an old favorite I used to use under openbox in ubuntu- xfe. It likewise won't find the cd or dvd drives. I remember I used to use something called ivman with openbox to get it to recognize the drives, but it's no longer in the repos; a new program is there instead. I wrote the developer of xfe--he sent me this email:

Hi,

let me explain, it's a mistake: I've written on the Xfe website that xfe can mount or unmount disks, but it's only *manually*, assuming you have all the stuff in your fstab file.

OK, I apologize, if I was not clear...

So for automount working with Xfe, you need an extra program that performs the automount. I don't know the distro you use, but on my Debian Squeeze (or in Ubuntu) this feature comes up with the Gnome desktop, and there's nothing to do. Then Xfe allows you to mount or unmount disk manually if you want...

Hope this is more clear now!
Have a nice day,
RB
___________________________
I have automount installed, and I installed pcmanfm to check. It can find the drives, although xfe can't. when I ran the mount command, this is what I got:

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda6 on /home type ext4 (rw)
/dev/sdb1 on /stuff type ext4 (rw)
gvfs-fuse-daemon on /home/michelle/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michelle)
/dev/sr1 on /media/Data disc (05 Jan 12) type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)

Judging from the last line, mount is finding the dvd rewriteable drive.( I had a data disk I burned in there to test in pcmanfm)

This is my fstab file:


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=2ba60b7e-2e75-4537-9da0-be8960b38900 / ext4 errors=remount-ro 0 1
# /home was on /dev/sda6 during installation
UUID=d3944afc-ae3c-406e-902d-17d6c61d29e6 /home ext4 defaults 0 2
# /stuff was on /dev/sdb1 during installation
UUID=b2494909-9882-47e4-8fe9-6329e920b413 /stuff ext4 defaults 0 2
# swap was on /dev/sda5 during installation
UUID=07b95289-d00b-48e6-95e7-1056dae77c29 none swap sw 0 0


I suspect maybe I need to add something to it? I thought I had to do that ages ago when I used openbox on ubuntu (it was a minimal install, build -it- yourself- deal), but I can't find my notes from that time.(that was a ways back-Hardy Heron, I believe)
I don't know if downloading the replacement program for ivman would do the trick;or if gnome volume manager would work; besides, pcmanfm can find the drives, so automount seems to work.
I'd really like to fix this, since xfe is a great file manager that suits my needs well in my work. (I have to compare numerous files, and it helps that I can open 2 folders in the same program, instead of flipping back and forth between tabs or having 2 instances of the same program opened.)

Any help is greatly appreciated! Thanks in advance!

---

### Post by cwsnyder on 2012-12-18
You need to add lines to your /etc/fstab file similar to: ```
/dev/sr0  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0
```Follow the documentation in [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) for more information.  The device '/dev/sr0' should match the device for your cd/dvd drive.  Don't try to use a UUID, because that will change every time you change the CD platter.

---

### Post by rolypolycat on 2012-12-19
I added the lines you told me:

# /etc/fstab: static system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2ba60b7e-2e75-4537-9da0-be8960b38900 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=d3944afc-ae3c-406e-902d-17d6c61d29e6 /home           ext4    defaults        0       2
# /stuff was on /dev/sdb1 during installation
UUID=b2494909-9882-47e4-8fe9-6329e920b413 /stuff          ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=07b95289-d00b-48e6-95e7-1056dae77c29 none            swap    sw              0       0
#line I added
/dev/sr1       /media/cdrom0   udf,iso9660   user,noauto,exec,utf8                 0      0

I still see no sign of the drive in my file manager, and when I ran the mount command, I got this response:
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda6 on /home type ext4 (rw)
/dev/sdb1 on /stuff type ext4 (rw)
gvfs-fuse-daemon on /home/michelle/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michelle)

If I run mount with the name of the device, I get this:
mount /dev/sr1
mount: mount point /media/cdrom0 does not exist

Is there something else I need to add? Or is this file manager or dvd just being obnoxious?:)

I found that when I edited the fstab file, my mouse seemed to act up-much slower to click on items- and  even pcmanfm couldn't read the dvd's it previously could. Once I removed the added line from fstab, pcmanfm could see the drives again, and an icon appears on the desktop. I can open the link in xfe-I get this message:

[Desktop Entry]
Encoding=UTF-8
Type=Link
X-Enlightenment-Type=Removable
X-Enlightenment-Removable-State=Full
Name=Data disc (05 Jan 12)
Icon=drive-optical
Comment=Removable Device
URL=file://org/freedesktop/UDisks/devices/sr1

The other file managers show the contents, this one just gives me a link. I really wish I knew what was going on; I don't recall having this much trouble before. Any ideas?

Thanks in advance!

---

### Post by rolypolycat on 2012-12-23
Well, I worked with this for a week, and finally came up with a workaround. Whether it works for all file managers and not just this one, I don't know.

At any rate, I loaded the places module, then placed it in a shelf. when I loaded a data dvd, it found it, but I had to click the places icon, or the one that strangely appears on my desktop(it didn't before) to get the disk to open in a file manager. It won't show up in an already open xfe.
So I have my favorite file manager working. The drives still don't show up in enlightenment's file manager-don't know why, but since I like xfe better, it doesn't really matter.

---

