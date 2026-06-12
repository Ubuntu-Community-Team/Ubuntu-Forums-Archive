---
title: "gdesklet configufrustration!!! lol"
date: 2005-11-23
forum: Desktop Environments
---

### Post by tomwell on 2005-11-23
Hi,
I am trying to configure a gdesklet, that monitors my hard drives, for my main Ubuntu hard drive name hdb  thats not a prob... I use the path / wich means root...

I have the option of monitoring a second drive, i would like it to montior hda3 wich is my fat32 partition... what is the path or mount point i need to type inside the gdesklet configure... I have tried multiple things and to no avail!!! 

Any help greatly appreciated 

Peace 

Tom

ps: attached is a copy of my sudo fdisk -l




Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         523     4200966   1b  Hidden W95 FAT32
/dev/hda2   *         524        7271    54203310    7  HPFS/NTFS
/dev/hda3            7272        9729    19743885    c  W95 FAT32 (LBA)

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14759   118551636   83  Linux
/dev/hdb2           14760       14946     1502077+   5  Extended
/dev/hdb5           14760       14946     1502046   82  Linux swap / Solaris

---

### Post by narcolept on 2005-11-23
what is it mounted as?  type 'mount', find /dev/hda3, and then whatever it is mounted as is what you would put in the gdesklet configuration.

---

### Post by tomwell on 2005-11-23
Hey,

Still not working, I have put in

/dev/hda3 on /media/fat32 type vfat (rw,iocharset=utf8,umask=000)

here is my result for mount
[COLOR="Red"]
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hda2 on /media/windows type ntfs (rw,nls=utf8,umask=0222)
/dev/hda3 on /media/fat32 type vfat (rw,iocharset=utf8,umask=000)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hdc on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=tom)[/COLOR]

what could it be??
ps this is the error message i get... in gdesklets...

float division                                                                       
/home/tom/.gdesklets/Displays/gauges-desklet/twodisk.display                         
   28                                                                                
   29                                                                                
   30 def do_gauge():                                                                
   31                                                                                
   32     fsa = (float(sysa.fsusage.total) - float(sysa.fsusage.avail)) /            
float(sysa.fsusage.total) * 100                                                      
>  33     fsb = (float(sysb.fsusage.total) - float(sysb.fsusage.avail)) /            
float(sysb.fsusage.total) * 100                                                      
   34     a_angle = 120 - (fsa * 0.6)                                                
   35     b_angle = 240 + (fsb * 0.6)                                                
   36     w = Dsp.gauge.width[PX]                                                    
   37     h = Dsp.gauge.height[PX]                                                   
   38     scalex = float(w) / 100                                                    
   39     scaley = float(h) / 100

---

### Post by tomwell on 2005-11-23
got it sorted...!!!

Instead of typing the whole line of where it is mounted i just put in /media/fat32 and that worked just fine...

Hope it helps someone else...!!

Peace 

Tom

---

### Post by LeeMcc on 2006-04-12
Helped me mate :D

Thanks alot!

---

