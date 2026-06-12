---
title: "soundcard driver problem"
date: 2004-12-04
forum: Desktop Environments
---

### Post by ganbaru on 2004-12-04
hi all
Just installed Ubuntu4.10 everything's fine except sound---CDPlayer plays but there's no audio output! (same case with xmms)

I've done some research and these are the outputs after issuing some commands:

$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo  PRO133x] (rev 44)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo M VP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile So uth] (rev 23)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686 /A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
0000:00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Managem ent (rev 30)
0000:00:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Hos t Controller (rev 46)
0000:00:0b.0 Ethernet controller: Linksys 21x4x DEC-Tulip compatible 10 /100 Ethernet (rev 11)
0000:01:00.0 VGA compatible controller: S3 Inc. 86c368 [Trio 3D/2X] (re v 02)



$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1  /mnt/windows  ntfs  nls=iso8859-1,ro,umask=0  0  0



$ modinfo soundcore
filename:       /lib/modules/2.6.8.1-3-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.8.1-3-386 preempt 386 gcc-3.3
depends:



$ dmesg
dd: command error: error=0x54
end_request: I/O error, dev hdd, sector 917224
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 917000
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 753936
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 752912
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 752688
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 753928
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 752904
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 752680
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 753336
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 752312
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 752088
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 753328
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 752304
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 752080
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 1248
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 1024
UDF-fs: No partition found (1)
hdd: command error: status=0x51 { DriveReady SeekComplete Error }
hdd: command error: error=0x54
end_request: I/O error, dev hdd, sector 64
isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
NTFS driver 2.1.15 [Flags: R/O MODULE].
NTFS volume version 3.1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains cha racters that cannot be converted to character set iso8859-1.
Creative EMU10K1 PCI Audio Driver, version 0.20a, 12:59:02 Oct 12 2004
cdrom: open failed.
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 0
Buffer I/O error on device hdb, logical block 0
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 4
Buffer I/O error on device hdb, logical block 1
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 8
Buffer I/O error on device hdb, logical block 2
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 12
Buffer I/O error on device hdb, logical block 3
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 16
Buffer I/O error on device hdb, logical block 4
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 20
Buffer I/O error on device hdb, logical block 5
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 24
Buffer I/O error on device hdb, logical block 6
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 28
Buffer I/O error on device hdb, logical block 7
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 32
Buffer I/O error on device hdb, logical block 8
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 36
Buffer I/O error on device hdb, logical block 9
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 40
Buffer I/O error on device hdb, logical block 10
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 44
Buffer I/O error on device hdb, logical block 11
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 48
Buffer I/O error on device hdb, logical block 12
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 52
Buffer I/O error on device hdb, logical block 13
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 56
Buffer I/O error on device hdb, logical block 14
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 60
Buffer I/O error on device hdb, logical block 15
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 64
Buffer I/O error on device hdb, logical block 16
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 68
Buffer I/O error on device hdb, logical block 17
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 72
Buffer I/O error on device hdb, logical block 18
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 76
Buffer I/O error on device hdb, logical block 19
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 80
Buffer I/O error on device hdb, logical block 20
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 84
Buffer I/O error on device hdb, logical block 21
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 88
Buffer I/O error on device hdb, logical block 22
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 92
Buffer I/O error on device hdb, logical block 23
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 96
Buffer I/O error on device hdb, logical block 24
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 100
Buffer I/O error on device hdb, logical block 25
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 104
Buffer I/O error on device hdb, logical block 26
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 108
Buffer I/O error on device hdb, logical block 27
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 112
Buffer I/O error on device hdb, logical block 28
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 116
Buffer I/O error on device hdb, logical block 29
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 120
Buffer I/O error on device hdb, logical block 30
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 124
Buffer I/O error on device hdb, logical block 31
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 0
Buffer I/O error on device hdb, logical block 0
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 4
Buffer I/O error on device hdb, logical block 1
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 64
Buffer I/O error on device hdb, logical block 16
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 68
Buffer I/O error on device hdb, logical block 17
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 64
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1034616
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1033592
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1033368
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1034608
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1033584
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1033360
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1034016
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1032992
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1032768
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1034008
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1032984
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1032760
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 848920
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 847896
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 847672
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 848912
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 847888
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 847664
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 848320
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 847296
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 847072
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 848312
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 847288
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 847064
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1248
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 1024
UDF-fs: No partition found (1)
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54
end_request: I/O error, dev hdb, sector 64
isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16



so here are my questions:
1) how do i know what soundcard i've gotten? Which command should i issue to find this out?

2) where can i grab the right driver for my soundcard?

3) and how to install the driver?

any help would be greatly appreciated.
ganbaru

---

### Post by Marauder1 on 2004-12-04
Do you have sound when Ubuntu boot up ?
When Ubuntu boots there is a music do you
hear it ?

---

### Post by ganbaru on 2004-12-04
no I never heard that music when it boots up...

thanks
ganbaru

---

### Post by bob k on 2004-12-04
[QUOTE=ganbaru]no I never heard that music when it boots up...

thanks
ganbaru[/QUOTE]
 Just looking at it on the surface it looks like you have more problems than sound. It looks like your ntfs mount failed. I usually use the command without the quotes " sudo mount /dev/hdxx /mnt/windows -t ntfs -o umask=0222" and cdrom0 and cdrom1 have failed. I would think about down loading warty  again, your ISO could have been damaged in the down load

---

### Post by ganbaru on 2004-12-04
Thanks for your help.

There's no problem with mounting my ntfs partition...i don't know what those error messages mean but at this stage it's fine. I can access it from my home directory...

I didn't do ISO. I got a CD from them so i don't think it was damaged.

any help with my soundcard?

Thanks
ganbaru

---

### Post by ganbaru on 2004-12-05
any help please? i want to listen to the music so badly...:(

thanks
ganbaru

---

### Post by Marauder1 on 2004-12-05
Im not that guru on corecting these prob but a good
way to start is to tell us which hardware you have in
your box. This way we can see if a wifi has been issued
for it or maybe somebody had the same prob.

From the look of your outputs it looks like you have
a sounds blaster live card but is it using the right driver ?

Send your hardware list this way more people can jump in .

Dont' give up !!!!

---

### Post by ganbaru on 2004-12-06
i'm not giving up and i won't! Thanks.

i'm not sure what sound card i've gotten. what linux command should i use in order to find out? (actually this was my question 1 in my very first post...)

thanks
ganbaru

---

### Post by Marauder1 on 2004-12-06
What kind of motherboard have you got ?
If you have a motherboard with onboard sound
it looks like you have a soundblaster live also !!!
Did you de-activated your onboard to use your SB live ?

---

### Post by ganbaru on 2004-12-07
no it's not an onboard sound... and i didn't do any de-activation...

looking forward to ur further help
thanks
Ganbaru

---

### Post by Marauder1 on 2004-12-07
If i look to your lspci output, no sound card were found !!!

Here is an exemple of mine :
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
0000:00:07.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
0000:00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
0000:00:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)

You can see clearly what it detected !!!
But in your case if it's not detected you gonna have to open the box to find out
which type it is.
And while the case is open, check if its well seated in the pci slot.

And also from your dmesg we can see that your hdb and hdd drive had a hard
time reading a cd. (hdd must be a cdrom drive). I hope you did not use that
drive to install Ubuntu. !!!

Here is a list of the sound card compatibility in Ubuntu :
[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsSoundCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsSoundCards)

---

### Post by ganbaru on 2004-12-10
ok i opened my box and found out:
Crystal 4235 ISA sound card

obviously ubuntu doesn't recognize it. what should i do now? where can i get the driver for ubuntu?

thanks again
Ganbaru

---

### Post by taygan on 2004-12-10
looks like the 4235 uses the snd-cs4236 module.

open a terminal and try:

sudo modprobe snd-cs4236

and let us know what happens.

---

### Post by ganbaru on 2004-12-10
That was a very prompt reply. Thanks!

well i got another prompt after issuing that command. nothing happened.

What's the next step?
Ganbaru

---

### Post by taygan on 2004-12-10
good! the prompt means your soundcard module (the driver) loaded!  Go to Applications>Multimedia>Volume Control and turn off all the mute buttons and slide the volume up to the middle and then try some sounds!

_If all that works_, you'll want to put the sound module into your boot routine.

there's many ways to do this.. It seems that one way is to add "snd-cs4236" (without the quotes) to your /etc/modules file:

from the terminal: sudo gedit /etc/modules

it'll look something like this:

# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line.  Comments begin with
# a "#", and everything on the line after them are ignored.

sd_mod
psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp
nvidia
snd-cs4236

---

### Post by ganbaru on 2004-12-11
unfortuntely it still doesn't work...

what can i do now :(

thanks
Ganbaru

---

### Post by taygan on 2004-12-11
after you tried the "modprobe snd-cs4236" try "lsmod" and confirm that the sound modules loaded.. There should be a bunch of them..

---

### Post by ganbaru on 2004-12-11
here's what i got:

$ lsmod
Module                  Size  Used by
ppp_deflate             6144  0
zlib_deflate           20760  1 ppp_deflate
bsd_comp                5888  0
ppp_async              10624  1
crc_ccitt               2432  1 ppp_async
snd_cs4236             18248  2
snd_opl3_lib            9728  1 snd_cs4236
snd_hwdep               9120  1 snd_opl3_lib
snd_cs4236_lib         16000  1 snd_cs4236
snd_mpu401_uart         7296  1 snd_cs4236
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  2 snd_opl3_lib,snd_rawmidi
snd_cs4231_lib         24960  2 snd_cs4236,snd_cs4236_lib
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  3 snd_cs4236_lib,snd_cs4231_lib,snd_pcm_oss
snd_timer              23172  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    50660  12 snd_cs4236,snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc         11144  2 snd_cs4231_lib,snd_pcm
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ipv6                  230020  10
ppp_generic            27668  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7040  1 ppp_generic
tulip                  42528  0
crc32                   4608  1 tulip
ohci1394               32004  0
uhci_hcd               29328  0
usbcore               104292  3 uhci_hcd
via_agp                 8832  1
agpgart                31784  1 via_agp
ns558                   5760  0
gameport                4736  1 ns558
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
nls_iso8859_1           4352  1
ntfs                   88660  1
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
apm                    19948  2
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
sbp2                   22408  0
ieee1394              100536  2 ohci1394,sbp2
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38276  0
mousedev               10124  1
psmouse                17800  0
sr_mod                 15780  0
scsi_mod              115148  2 sbp2,sr_mod
cdrom                  35872  2 ide_cd,sr_mod
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
via82cxxx              13084  1
ide_disk               16768  4
ide_core              125272  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   25904  740
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

---

### Post by ganbaru on 2004-12-11
any more help please?

thanks
Ganbaru

---

### Post by taygan on 2004-12-12
Well, you could try just adding the snd-cs4236 to /etc/modules anyway, and reboot as it seems to have loaded just fine. (Remember, linux needs a sound cable from the cd player to the sound card if you're going to play cds analog, mp3s,etc should play digitally just fine.)

Then try 'alsamixer' from the terminal (instead of the gnome volume control, just for fun)  If you've got MM at the top of the volume column it's muted: use 'm' to unmute, arrows to move around and increase the volume, make sure the PCM column is unmuted and turned up..

get a .wav file into your home directory and try to play it with 'aplay filename'  If there's no error message than linux thinks it's trying to play it.

double check that your cords are plugged into the right places too :)

good luck!

---

### Post by ganbaru on 2004-12-12
there's no error message after issuing "aplay file.wav" but i still couldn't hear anything...:(

i've got a Sony CD_burner as the master and Liteon DVD-rom as the slave. Currently the sound cable connects to the DVD-rom. Could this be a problem?

and if all these attempts fail, what can i do? gget a new sound card?

thanks
Ganbaru

---

### Post by ganbaru on 2004-12-13
any more help please?

Thanks

---

### Post by taygan on 2004-12-13
Here's what you have: the module seems to be loading fine, the aplayer seems to be playing a sound, you just can't hear it right?  This looks like Ubuntu is loading everything now.  Double check your alsamixer (did you press the right arrow a bunch to get to the other volume settings?  The MM is gone from the top of the volume controls?  The volume is turned up to 70 or so?)  Double check your cords..  I've mixed up the sound in and the sound out more than once..  Your audio cable is only for hearing cds or dvds, not for system sounds..  Do your speakers work?  I'd double check all the non-system stuff, 'cuz it seems like it's loading..

You could try borrowing another sound card, but it seems like your sound card IS loading.

That's all I know..  Good Luck.


+++++++++++++++++++

Hmmm.. check out this post:

[http://ubuntuforums.org/showthread.php?t=486](http://ubuntuforums.org/showthread.php?t=486)

try adding pci=noacpi to the end of the kernel line in /boot/grub/menu.lst

---

