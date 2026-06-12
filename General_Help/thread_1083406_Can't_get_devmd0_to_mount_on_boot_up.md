---
title: "Can't get /dev/md0 to mount on boot up"
date: 2009-02-28
forum: General Help
---

### Post by toorudez on 2009-02-28
I created a RAID 5 software array, with an ntfs filesystem on it.  I cannot get it to mount on boot up though.  I have this line in the /etc/fstab:

/dev/md0	/var/media	ntfs-3g	defaults,locale=en_US.utf8	0 0

And when I run "sudo mount -a", I get this error:

NTFS signature is missing.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

"fdisk -l" lists the following:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00064690

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e23e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d5c41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18701   150215751   83  Linux
/dev/sdc2           18702       19457     6072570    5  Extended
/dev/sdc5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3409

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

The RAID array consists of sda1, sdb1, and sdd1.  If I just run "mount /dev/md0 /var/media", the drive mounts fine, and I can access it from my windows box.  But it will not mount at boot.  Can anyone help me?

Thanks in advance.

---

### Post by thtrgremlin on 2009-02-28
You mention it is a soft raid? Did you use, or have you installed 'dmraid'?
```
sudo apt-get install dmraid
```

What software did you use to make the soft raid? One of those onboard tools you can access at startup?

anyway, /dev/md0 is the physical disk, not the raid. It is like you are trying to mount the part rather than the whole definition, hence that 'NTFS signature is missing.' thing.

dmraid will add a new directory in /dev/ for raids, and in there will be a strange name made up of some of the stats about the first disk. If you arn having trouble locating it, post:
```
ls /dev/
```and I will be able to recognize it.

After you install dmraid, I still don't think that it will show up in the fdisk -l output, just because fdisk only handler real physical connections.

Best luck. I am heading out for about an hour, but I will check in when I get back.

---

### Post by thtrgremlin on 2009-02-28
Oh, and just in case, you may want to check out this thread.

[http://www.linuxquestions.org/questions/linux-software-2/raid5-using-mdadm-how-to-mount-devmd0-387769/]("http://www.linuxquestions.org/questions/linux-software-2/raid5-using-mdadm-how-to-mount-devmd0-387769/")

---

### Post by toorudez on 2009-03-01
I used mdadm.  From this link: [http://bfish.xaedalus.net/?p=188]("http://bfish.xaedalus.net/?p=188")

Here's the output of sudo dmraid -r

/dev/sdd: sil, "sil_ajabaccaaidg", unknown, ok, 1953523630 sectors, data@ 0
/dev/sdc: sil, "sil_ajabacbjcjch", linear, ok, 312580270 sectors, data@ 0
/dev/sdb: sil, "sil_ajabaccaaidg", unknown, ok, 1953523630 sectors, data@ 0
/dev/sda: sil, "sil_ajabaccaaidg", unknown, ok, 1953523630 sectors, data@ 0

sudo dmraid -s
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sdd to RAID set "sil_ajabaccaaidg"
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sdb to RAID set "sil_ajabaccaaidg"
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sda to RAID set "sil_ajabaccaaidg"
*** Set
name   : sil_ajabacbjcjch
size   : 312580270
stride : 0
type   : linear
status : ok
subsets: 0
devs   : 1
spares : 0

ls /dev
adsp                ptyd4  ptyt8  ptyzc       tty54  ttyp6  ttyv6
audio               ptyd5  ptyt9  ptyzd       tty55  ttyp7  ttyv7
block               ptyd6  ptyta  ptyze       tty56  ttyp8  ttyv8
bus                 ptyd7  ptytb  ptyzf       tty57  ttyp9  ttyv9
cdrom               ptyd8  ptytc  ram0        tty58  ttypa  ttyva
char                ptyd9  ptytd  ram1        tty59  ttypb  ttyvb
console             ptyda  ptyte  ram10       tty6   ttypc  ttyvc
core                ptydb  ptytf  ram11       tty60  ttypd  ttyvd
cpu_dma_latency     ptydc  ptyu0  ram12       tty61  ttype  ttyve
disk                ptydd  ptyu1  ram13       tty62  ttypf  ttyvf
dsp                 ptyde  ptyu2  ram14       tty63  ttyq0  ttyw0
dvd                 ptydf  ptyu3  ram15       tty7   ttyq1  ttyw1
fd                  ptye0  ptyu4  ram2        tty8   ttyq2  ttyw2
full                ptye1  ptyu5  ram3        tty9   ttyq3  ttyw3
fuse                ptye2  ptyu6  ram4        ttya0  ttyq4  ttyw4
hpet                ptye3  ptyu7  ram5        ttya1  ttyq5  ttyw5
initctl             ptye4  ptyu8  ram6        ttya2  ttyq6  ttyw6
input               ptye5  ptyu9  ram7        ttya3  ttyq7  ttyw7
kmem                ptye6  ptyua  ram8        ttya4  ttyq8  ttyw8
kmsg                ptye7  ptyub  ram9        ttya5  ttyq9  ttyw9
log                 ptye8  ptyuc  random      ttya6  ttyqa  ttywa
loop0               ptye9  ptyud  rtc         ttya7  ttyqb  ttywb
loop1               ptyea  ptyue  rtc0        ttya8  ttyqc  ttywc
loop2               ptyeb  ptyuf  scd0        ttya9  ttyqd  ttywd
loop3               ptyec  ptyv0  sda         ttyaa  ttyqe  ttywe
loop4               ptyed  ptyv1  sda1        ttyab  ttyqf  ttywf
loop5               ptyee  ptyv2  sdb         ttyac  ttyr0  ttyx0
loop6               ptyef  ptyv3  sdb1        ttyad  ttyr1  ttyx1
loop7               ptyp0  ptyv4  sdc         ttyae  ttyr2  ttyx2
lp0                 ptyp1  ptyv5  sdc1        ttyaf  ttyr3  ttyx3
MAKEDEV             ptyp2  ptyv6  sdc2        ttyb0  ttyr4  ttyx4
mapper              ptyp3  ptyv7  sdc5        ttyb1  ttyr5  ttyx5
md0                 ptyp4  ptyv8  sdd         ttyb2  ttyr6  ttyx6
mem                 ptyp5  ptyv9  sdd1        ttyb3  ttyr7  ttyx7
mixer               ptyp6  ptyva  sequencer   ttyb4  ttyr8  ttyx8
net                 ptyp7  ptyvb  sequencer2  ttyb5  ttyr9  ttyx9
network_latency     ptyp8  ptyvc  sg0         ttyb6  ttyra  ttyxa
network_throughput  ptyp9  ptyvd  sg1         ttyb7  ttyrb  ttyxb
null                ptypa  ptyve  sg2         ttyb8  ttyrc  ttyxc
nvidia0             ptypb  ptyvf  sg3         ttyb9  ttyrd  ttyxd
nvidiactl           ptypc  ptyw0  sg4         ttyba  ttyre  ttyxe
oldmem              ptypd  ptyw1  shm         ttybb  ttyrf  ttyxf
parport0            ptype  ptyw2  snapshot    ttybc  ttyS0  ttyy0
port                ptypf  ptyw3  snd         ttybd  ttys0  ttyy1
ppp                 ptyq0  ptyw4  sndstat     ttybe  ttyS1  ttyy2
psaux               ptyq1  ptyw5  sr0         ttybf  ttys1  ttyy3
ptmx                ptyq2  ptyw6  stderr      ttyc0  ttyS2  ttyy4
pts                 ptyq3  ptyw7  stdin       ttyc1  ttys2  ttyy5
ptya0               ptyq4  ptyw8  stdout      ttyc2  ttyS3  ttyy6
ptya1               ptyq5  ptyw9  tty         ttyc3  ttys3  ttyy7
ptya2               ptyq6  ptywa  tty0        ttyc4  ttys4  ttyy8
ptya3               ptyq7  ptywb  tty1        ttyc5  ttys5  ttyy9
ptya4               ptyq8  ptywc  tty10       ttyc6  ttys6  ttyya
ptya5               ptyq9  ptywd  tty11       ttyc7  ttys7  ttyyb
ptya6               ptyqa  ptywe  tty12       ttyc8  ttys8  ttyyc
ptya7               ptyqb  ptywf  tty13       ttyc9  ttys9  ttyyd
ptya8               ptyqc  ptyx0  tty14       ttyca  ttysa  ttyye
ptya9               ptyqd  ptyx1  tty15       ttycb  ttysb  ttyyf
ptyaa               ptyqe  ptyx2  tty16       ttycc  ttysc  ttyz0
ptyab               ptyqf  ptyx3  tty17       ttycd  ttysd  ttyz1
ptyac               ptyr0  ptyx4  tty18       ttyce  ttyse  ttyz2
ptyad               ptyr1  ptyx5  tty19       ttycf  ttysf  ttyz3
ptyae               ptyr2  ptyx6  tty2        ttyd0  ttyt0  ttyz4
ptyaf               ptyr3  ptyx7  tty20       ttyd1  ttyt1  ttyz5
ptyb0               ptyr4  ptyx8  tty21       ttyd2  ttyt2  ttyz6
ptyb1               ptyr5  ptyx9  tty22       ttyd3  ttyt3  ttyz7
ptyb2               ptyr6  ptyxa  tty23       ttyd4  ttyt4  ttyz8
ptyb3               ptyr7  ptyxb  tty24       ttyd5  ttyt5  ttyz9
ptyb4               ptyr8  ptyxc  tty25       ttyd6  ttyt6  ttyza
ptyb5               ptyr9  ptyxd  tty26       ttyd7  ttyt7  ttyzb
ptyb6               ptyra  ptyxe  tty27       ttyd8  ttyt8  ttyzc
ptyb7               ptyrb  ptyxf  tty28       ttyd9  ttyt9  ttyzd
ptyb8               ptyrc  ptyy0  tty29       ttyda  ttyta  ttyze
ptyb9               ptyrd  ptyy1  tty3        ttydb  ttytb  ttyzf
ptyba               ptyre  ptyy2  tty30       ttydc  ttytc  urandom
ptybb               ptyrf  ptyy3  tty31       ttydd  ttytd  usbdev1.1_ep00
ptybc               ptys0  ptyy4  tty32       ttyde  ttyte  usbdev1.1_ep81
ptybd               ptys1  ptyy5  tty33       ttydf  ttytf  usbdev2.1_ep00
ptybe               ptys2  ptyy6  tty34       ttye0  ttyu0  usbdev2.1_ep81
ptybf               ptys3  ptyy7  tty35       ttye1  ttyu1  vcs
ptyc0               ptys4  ptyy8  tty36       ttye2  ttyu2  vcs1
ptyc1               ptys5  ptyy9  tty37       ttye3  ttyu3  vcs2
ptyc2               ptys6  ptyya  tty38       ttye4  ttyu4  vcs3
ptyc3               ptys7  ptyyb  tty39       ttye5  ttyu5  vcs4
ptyc4               ptys8  ptyyc  tty4        ttye6  ttyu6  vcs5
ptyc5               ptys9  ptyyd  tty40       ttye7  ttyu7  vcs6
ptyc6               ptysa  ptyye  tty41       ttye8  ttyu8  vcs7
ptyc7               ptysb  ptyyf  tty42       ttye9  ttyu9  vcs8
ptyc8               ptysc  ptyz0  tty43       ttyea  ttyua  vcsa
ptyc9               ptysd  ptyz1  tty44       ttyeb  ttyub  vcsa1
ptyca               ptyse  ptyz2  tty45       ttyec  ttyuc  vcsa2
ptycb               ptysf  ptyz3  tty46       ttyed  ttyud  vcsa3
ptycc               ptyt0  ptyz4  tty47       ttyee  ttyue  vcsa4
ptycd               ptyt1  ptyz5  tty48       ttyef  ttyuf  vcsa5
ptyce               ptyt2  ptyz6  tty49       ttyp0  ttyv0  vcsa6
ptycf               ptyt3  ptyz7  tty5        ttyp1  ttyv1  vcsa7
ptyd0               ptyt4  ptyz8  tty50       ttyp2  ttyv2  vcsa8
ptyd1               ptyt5  ptyz9  tty51       ttyp3  ttyv3  xconsole
ptyd2               ptyt6  ptyza  tty52       ttyp4  ttyv4  zero
ptyd3               ptyt7  ptyzb  tty53       ttyp5  ttyv5

---

### Post by thtrgremlin on 2009-03-01
looking at this:> /dev/sdd: sil, "sil_ajabaccaaidg", unknown, ok, 1953523630 sectors, data@ 0
/dev/sdc: sil, "[COLOR="DarkRed"]sil_ajabacbjcjch[/COLOR]", linear, ok, 312580270 sectors, data@ 0
/dev/sdb: sil, "sil_ajabaccaaidg", unknown, ok, 1953523630 sectors, data@ 0
/dev/sda: sil, "sil_ajabaccaaidg", unknown, ok, 1953523630 sectors, data@ 0
I see that it doesn't match these> 
sudo dmraid -s
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sdd to RAID set "[COLOR="DarkRed"]sil_ajabaccaaidg[/COLOR]"
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sdb to RAID set "[COLOR="DarkRed"]sil_ajabaccaaidg[/COLOR]"
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sda to RAID set "[COLOR="DarkRed"]sil_ajabaccaaidg[/COLOR]"
not to mention > *** Set
name : [COLOR="DarkRed"]sil_ajabacbjcjch[/COLOR]
size : 312580270
stride : 0
type : linear
status : ok
subsets: 0
devs : 1
spares : 0

This makes me believe that the raid is /dev/mapper/[COLOR="DarkRed"]*[/COLOR]/sil_ajabacbjcjch

so try changing your fstab to
> 
/dev/mapper/[COLOR="DarkRed"]*[/COLOR]/sil_ajabacbjcjch /var/media ntfs-3g defaults,locale=en_US.utf8 0 0

If I remember correctly, there should be a directory between mapper and sil_

Also, in poking around a bit, I found this:[http://ubuntuforums.org/showthread.php?t=490332]("http://ubuntuforums.org/showthread.php?t=490332") since it APPEARS mdadm should have done everything you needed. Just thought it was worth sharing.

Hope that solves the problem. Going to bed. if that doesn't fix everything, i'll be back on tomorrow morning. Best luck!

---

### Post by toorudez on 2009-03-01
The only directory in /dev/mapper is control.  Tried 
> /dev/mapper/control/sil_ajabaccaaidg /var/media ntfs-3g defaults,locale=en_US.utf8 0 0
and came up with
> ntfs-3g: Failed to access volume '/dev/mapper/control/sil_ajabaccaaidg': Not a directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

So I tried 
> sudo ntfs-3g /dev/md0 /var/media -o force
and got
> Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

And yet when I try
> sudo mount /dev/md0 /var/media
it works fine.  But mounting it that way in either /etc/fstab or /etc/rc.local dosen't work.


As a side note, the device 
> /dev/sdc: sil, "sil_ajabacbjcjch", linear, ok, 312580270 sectors, data@ 0
is my 150GB drive with linux on it.

---

