---
title: "external USB/cardreader drive no longer mounts (on desktop only)"
date: 2005-12-08
forum: Desktop Environments
---

### Post by 0okami on 2005-12-08
Ok, i have an XS drive (basicly a deice that is a multicard reader with a harddrive on the inside)

This device was working flawless up untill a few minutes ago. It would mount automaticly when pluged into the usb drive... 

Now it wont auto mount on my desktop machine anymore.  My notebook cant see it and r/w to it. but pluging it into my desktop does nothing. 

the only thing i did before this problem happened was boot into windowsxp to copy some files off to XP and boot back into linux. 

I tried unpluging the device, and booting back into linux without it pluged into the port... that didnt work...  I tried other ports, that didnt work. 

reading some posts, i hear mention about fstab and such... i dont know what any of that means yet... 

this is my fstab: 
 ```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0



```


this is when i do lsusb: 
```


ookami@Navi:~$ lsusb
Bus 003 Device 004: ID 0d7d:1270 Phison Electronics Corp.
Bus 003 Device 003: ID 07cc:0301 Carry Computer Eng., Co., Ltd 6-in-1 Card Reader
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 062a:0000 Creative Labs
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
ookami@Navi:~$


```

this is what comes back with the mount command: 

```


ookami@Navi:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
ookami@Navi:~$


```


... i dont know what to do next.

---

### Post by Sokraates on 2005-12-08
This sugestion may sound insulting for an experienced user but: have you done any changes to your system, that became effective after reboot?

---

### Post by 0okami on 2005-12-08
none as far as i recall. Nothing system like. 

*checks his log of changes* 
nope. nothing other than desktop theme installation.

(i keep a lof of everything i change for learning purposes)  :)

looking at the fstab on my notebook, and comparing it to my desktop, i see there is no /media/usb0  on my desktop as there is on my notebook.
 
the line on my botebook reads: 
/dev/sda   /media/usb0/  auto  rw,user,noauto   0    0

that line is missing on my desktop


Can i just add that line to the fstab?
do i have to reboot if i do?

---

### Post by Sokraates on 2005-12-08
Since on your desktop the reader works, but not on the desktop, I would suggest removing /media/usb0.

Of course: after backing up your fstab.

To remount /etc/fstab, simply type

```
sudo mount -a
```

---

### Post by 0okami on 2005-12-08
for what i understood that was an ok to add that line? 
did so, ran that command and i added -v (verbose) got: 

```

ookami@Navi:~$ sudo mount -a -v
mount: proc already mounted on /proc
nothing was mounted
ookami@Navi:~$

```

still no drive mounted.

---

### Post by Sokraates on 2005-12-08
Right, I read that the problem was on your notebook, not your desktop.

"nothing was mounted" only means, that no device was found on /dev/sda. 

As far as I understand, /dev/sda is the first SCSI-drive. Just like /dev/hda is the first IDE-drive. So it's usually a HD. USB-devs are usually /dev/ttyUSB0, /dev/ttyUSB1 etc. These devs are only created, when the USB-device is plugged in.

So it seems, that the HD inside your cardreader is a SCSi-drive and that this drive is addressed by /dev/sda /media/usb0/ auto rw,user,noauto 0 0.

You can try to remove "noauto". That way the device will be mounted automatically. With "noauto", you will have to mount the device manually.

Then again, it works on your notebook.

Hmm ... that's about it. I'm at my witt's end. :???: 

BTW: for a quick guide to fstab look here: 

[http://www.humbug.org.au/talks/fstab/fstab.html](http://www.humbug.org.au/talks/fstab/fstab.html)

---

### Post by 0okami on 2005-12-08
i got it solved for the moment... 

here's how i did it:
(doubt ill remember tomorow, so i figure id post the temp solution: 

```


ookami@Navi:~$ cd Desktop
ookami@Navi:~/Desktop$ mkdir xs-drive
ookami@Navi:~/Desktop$ dmesg | grep -i "SCSI device"
[4300686.425000] SCSI device sdd: 58605120 512-byte hdwr sectors (30006 MB)
[4300686.435000] SCSI device sdd: 58605120 512-byte hdwr sectors (30006 MB)
[4300686.807000] SCSI device sdg: 1993728 512-byte hdwr sectors (1021 MB)
[4300686.821000] SCSI device sdg: 1993728 512-byte hdwr sectors (1021 MB)
[4300926.638000] SCSI device sdh: 2001888 512-byte hdwr sectors (1025 MB)
[4300926.643000] SCSI device sdh: 2001888 512-byte hdwr sectors (1025 MB)
[4301028.433000] SCSI device sdd: 58605120 512-byte hdwr sectors (30006 MB)
[4301028.443000] SCSI device sdd: 58605120 512-byte hdwr sectors (30006 MB)
[4301028.721000] SCSI device sdg: 1993728 512-byte hdwr sectors (1021 MB)
[4301028.734000] SCSI device sdg: 1993728 512-byte hdwr sectors (1021 MB)
ookami@Navi:~/Desktop$sudo mount -t vfat -o uid=ookami,gid=users /dev/sdd /home/ookami/Desktop/xs-drive
Password:*************************
ookami@Navi:~/Desktop$ cd xs-drive
ookami@Navi:~/Desktop/xs-drive$ ls
anime 
ookami@Navi:~/Desktop/xs-drive$

``` 


YAY! .........damn i have a headache now.

it seems i have to mount things manually now. Not a big deal. Im up for the learning experience.

---

### Post by Sokraates on 2005-12-08
[QUOTE=0okami]YAY! .........damn i have a headache now.[/QUOTE]

*passing the Aspirin*

Congrats!

---

### Post by 0okami on 2005-12-08
i noticed something... i just rememberd i deleted a few lings from the /media/ folder....  it was an icon for USB with an arrow on it... 

I remember i didnt add that to my log...  hmm i wonder if that had anything to do with it.

---

### Post by Sokraates on 2005-12-08
Hmmm ... "Arrow" usually means "Link".

It could well be, that you've deleted a link to /dev/sda, which is used by ubuntu.  Like /media/cdrom or /media/floppy.

---

### Post by firenurse4 on 2005-12-08
[QUOTE=0okami]i got it solved for the moment... 

YAY! .........damn i have a headache now.

it seems i have to mount things manually now. Not a big deal. Im up for the learning experience.[/QUOTE]

I know that feeling. I was having a an auto mount problem as well.  What I finally did to fix it was to remove a package named **gnome-volume-manager**, reboot and then reinstall it.  The gnome-volume-manager is the dameon that handles auto mounting drives in gnome.

You can read that saga here...

[My automount saga ;) ]("http://ubuntuforums.org/showthread.php?t=100129")

I hope this helps!

---

