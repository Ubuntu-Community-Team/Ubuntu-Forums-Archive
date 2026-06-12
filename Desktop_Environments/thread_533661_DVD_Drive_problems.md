---
title: "DVD Drive problems"
date: 2007-08-24
forum: Desktop Environments
---

### Post by jmcgee on 2007-08-24
CDROM not readable
I'm using 6.06. this used to work on this hardware, I suspect it broke when I installed a new kernel, (but I have backed up to 2.6.15-27-386.)

I can't read data, CDROM or DVD discs.

var/log/syslog has this:
Aug 15 11:55:34 localhost kernel: [17349902.852000] cdrom: This disc doesn't have any tracks I recognize!
and this:
Aug 15 19:35:29 localhost kernel: [17179576.192000] Probing IDE interface ide1...
Aug 15 19:35:29 localhost kernel: [17179577.208000] hdd: BENQ DVD LS DW1655, ATAPI CD/DVD-ROM drive
Aug 15 19:35:29 localhost kernel: [17179577.264000] ide1 at 0x170-0x177,0x376 on irq 15
Aug 15 19:35:29 localhost kernel: [17179577.272000] hda: max request size: 128KiB
Aug 15 19:35:29 localhost kernel: [17179577.280000] hda: 25385472 sectors (12997 MB) w/463KiB Cache, CHS=25184/16/63, UDMA(33)
Aug 15 19:35:29 localhost kernel: [17179577.280000] hda: cache flushes not supported
Aug 15 19:35:29 localhost kernel: [17179577.280000] hda: hda1 hda2
Aug 15 19:35:29 localhost kernel: [17179577.308000] hdb: max request size: 1024KiB
Aug 15 19:35:29 localhost kernel: [17179577.312000] hdb: 586114704 sectors (300090 MB) w/16384KiB Cache, CHS=36483/255/63, UDMA(133)
Aug 15 19:35:29 localhost kernel: [17179577.312000] hdb: cache flushes supported
Aug 15 19:35:29 localhost kernel: [17179577.312000] hdb: hdb1
Aug 15 19:35:29 localhost kernel: [17179577.320000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Aug 15 19:35:29 localhost kernel: [17179577.320000] Uniform CD-ROM driver Revision: 3.20


# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb1 /myth xfs defaults 0 2
/dev/hda2 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
//192.168.0.2/mythtvbackup smbfs credentials=/root/.smbcredentials,dmask=777,fmask= 777 0 0


If I type mount in terminal I get this:

sh-3.1$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hdb1 on /myth type xfs (rw)


Any ideas?

---

