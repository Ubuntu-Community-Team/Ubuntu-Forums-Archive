---
title: "burned video or data DVD fails to mount"
date: 2009-05-19
forum: General Help
---

### Post by asalford on 2009-05-19
[COLOR="Blue"]upon boot, it will mount previously burned video and data DVD's.  However, After burning a data DVD, I can't mount it.  Though in another ubuntu system, the disk is mountable.  This tells me that the burn process is ok and the drive is also ok.


System is ubuntu edgy running  2.6.24-24-386 i686 GNU/Linux
 upgraded moons ago from a lts version[/COLOR]


dpkg --list | grep libdvd

ii  libdvdcss2                             1.2.9-2medibuntu4                                          Library for accessing DVDs like block device usind deCSS

ii  libdvdnav4                             0.1.10-0.2                                                 The DVD navigation library

ii  libdvdread3                            0.9.7-8ubuntu1                                             library for reading DVDs

 



# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/hda3

UUID=1619ecfa-74a1-4774-9aa5-918eb6800700 / ext3 defaults,errors=remount-ro 0 1

# /dev/hda1 

UUID=40271064-a597-452d-a62f-9ee0c532aebf /boot ext3 defaults 0 2

# /dev/hda6 

UUID=54f7bda9-5774-4a58-ae12-5b8eb28f574f /home ext3 defaults 0 2

# /dev/hdc1 

UUID=d23ba3b2-0e00-47d1-b273-a3908b59b90c /media/video ext3 defaults 0 2

# /dev/hda5

UUID=2c17d9ca-f447-4409-8bed-710ba8b47478 /usr ext3 defaults 0 2

# /dev/hda7 

UUID=c29730db-94a9-444f-959c-4348e65857b7 /var ext3 defaults 0 2

# /dev/hda2

UUID=3dae0560-b09c-401f-92c7-5e6c63b56898 none swap sw 0 0

/dev/scd0        /media/cdrom0   auto user,noauto     0       0  [B][COLOR="Red"]<== I changed this based on various posts, but the problem remains
[/COLOR][/B]


[COLOR="Blue"]After rebooting, I can again mount the previously burned disk.  It will even automount.  trying then to mount a recently burned data dvd, I get the following after using the command "sudo mount -t iso9660 -o ro /dev/scd0 /media/cdrom0" which is the same command i used on the previously burned disk.  after that, nothing else, for example "eject" works with the drive until the system is rebooted.  I have no problem mounting cdroms recently burned.[/COLOR]



[  406.224615] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

[  406.224630] ata2.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0

[  406.224631]          cdb 1b 00 00 00 03 00 00 00  00 00 00 00 00 00 00 00

[  406.224633]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)

[  406.224636] ata2.01: status: { DRDY }

[  547.270480] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x4)

[  547.270484] ata2.01: revalidation failed (errno=-5)

[  547.270488] ata2.01: disabled

[  547.795387] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x40)

[  547.795394] ata2.00: revalidation failed (errno=-5)

[  547.795398] ata2: failed to recover some devices, retrying in 5 secs

[  552.791392] ata2: soft resetting link

[  557.980832] ata2: port is slow to respond, please be patient (Status 0x90)

[  562.790732] ata2: SRST failed (errno=-16)

[  562.790739] ata2: soft resetting link

[39300.490582] ata2: EH complete

[39300.491303] attempt to access beyond end of device

[39300.491307] sr0: rw=0, want=68, limit=4

[39300.491311] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

[40293.704331] attempt to access beyond end of device

[40293.704339] sr0: rw=0, want=68, limit=4

[40293.704342] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

[40376.651219] attempt to access beyond end of device

[40376.651226] sr0: rw=0, want=68, limit=4

[40376.651229] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[COLOR="Blue"]
Any Ideas or suggestions?[/COLOR]

---

