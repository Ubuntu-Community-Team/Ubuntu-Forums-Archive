---
title: "iso burning problem - hard to solve"
date: 2005-08-04
forum: Desktop Environments
---

### Post by Boffa on 2005-08-04
Hi

This is a delicate problem to solve for you.

I have serious problems with DVD-burning. I have no problems in Windows to burn .iso so I don't expect Linux have that either, but I couldn't be more wrong. I think I have tried the most.

My dvd.iso file is 3.0 GB and I am using DVD-R discs.
This is what I have tested so far.

1) Rightclick on iso-file and "Write to disc...." in Nautilus. It looks like it starts a burning session and after 5 minutes ejects the DVD and say it is ready. The DVD is way off ready. If I closely look at the disc, it looks like  it has burned about 15% and the DVD is inaccessible in both PC and my external DVD-player.

2) With Gnomebaker it complains it cannot use the device.

3) Installing K3B with no problem. K3B recognize it as recordable device. See below.  It starts up and looks fine with burning process but ends up exactly as with the "Write to disc..." but here I get the error after about 5 seconds that say.. "write failed: Invalid argument". The result below is the debugging information from K3B. But!!! K3B continues to think it is burning and gives oddly a "burning successful" in the end.

4) Last I have tried in shell perform the growisofs command but even here it ends up with the same result as K3B (and probably "Write to disc..")


I think I have run out of options now. I hope I have all information you need to help me out here. Because if CD/DVD burning does not work in Linux I have no options to return to WIndows XP. Everything else I can live with/without. I still have my Linuxserver up and running since 1999 as mailserver etc.

If you take a look at the result from "hdparm -i" command it gives strange result about the device, but that maybe not is interesting. 

thanks
Michael

------------------------------------------------------------------

Devices
-----------------------
HL-DT-ST DVDRAM GSA-4040B A109 (/dev/scd1, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD+R; DVD+RW] [DVD-ROM; DVD-R Sequential; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]


System
-----------------------
K3b Version: 0.11.23
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-686
growisofs: 5.21
mkisofs: 2.01a34-unofficial-iconv


growisofs comand:
-----------------------
/usr/bin/growisofs -Z /dev/scd1=/home/mhellden/dvd.iso -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -speed=2 


growisofs output:
-----------------------
Executing 'builtin_dd if=/home/mhellden/dvd.iso of=/dev/scd1 obs=32k seek=0'
/dev/scd1: "Current Write Speed" is 2.0x1385KBps.
:-[ WRITE@LBA=10h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
:-( write failed: Invalid argument
/dev/scd1: flushing cache
/dev/scd1: updating RMA
/dev/scd1: closing disc


hdparm -i /dev/scd1 command:
----------------------------------------
/dev/scd1:

 Model=DVDRAM GSA-4040BA109, FwRev=A109, SerialNo=
 Config={ }
 RawCHS=0/255/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/255/63, CurSects=0, LBA=no
 IORDY=no
 PIO modes:  pio0
 AdvancedPM=no

---

### Post by heimo on 2005-08-04
No idea... But one question: is DMA enabled on DVD and hard disks?

---

### Post by Boffa on 2005-08-04
System regonize SATA cotroller as SCSI emulation.

Harddisk - /dev/sda
DVD reader - /dev/scd0
DVD writer - /dev/scd1


root@pheonix:~ # hdparm -d 1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

root@pheonix:~ # hdparm -d 1 /dev/sda1

/dev/sda1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
root@pheonix:~ # hdparm -d 1 /dev/sda5

/dev/sda5:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
root@pheonix:~ # hdparm -d 1 /dev/scd1

/dev/scd1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
root@pheonix:~ # hdparm -d 1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

---

### Post by Boffa on 2005-08-05
New tries...

1) I tested to format a DVD-RW disc, and that worked. But I can not write anything to it.

2) Installed demo of NeroLinux 2.0.0
Even this application fails to burn with my recorder.

It reports: "Unspecified target error"

I starting to wonder if my DVD-burner is Linux incompatible.

// michael

---

### Post by heimo on 2005-08-05
Long shot (change to different controller):
[http://www.webservertalk.com/message1053872.html](http://www.webservertalk.com/message1053872.html)

---

### Post by heimo on 2005-08-05
[QUOTE=Boffa]System regonize SATA cotroller as SCSI emulation.
Harddisk - /dev/sda
DVD reader - /dev/scd0
DVD writer - /dev/scd1
[/QUOTE]

Are you saying that these are all SATA devices? My SATA disks are of the form /dev/sd? (a,b), and my DVD/RW + CD/RW devices are IDE and of the form /dev/hd? (c,d) Or are your DVD drives real scsi devices? If not... go check how those are detected in dmesg (run on terminal, these are boot time messages)

---

### Post by Boffa on 2005-08-05
First: Both devices work perfectly if you just use them to read DVD movies or DVD data disks. They mount perfect on /dev/scd0 and /dev/scd1.

/dev/dvd -> /dev/scd0
/dev/dvd2 -> /dev/scd1


That&#347; a strange thing I do not really fully understand.

There is one harddisk and it is on the SATA controller. It is called /dev/sda

But the two DVD recorder and DVD reader are connected to standard IDE / ATA bus.
This computer is recognizing these as SCSI disks but in reality they are ATA-devices.

In device manager :

82810EB (ICH5) Serial ATA 150 Storage Controller
- SCSI Host Interface
- - SCSI Device
- - - Maxtor 6Y160M0
- - - - Volume
- - - - Volume
- - - - Volume
- - - - Volume
- SCSI Host Interface
- - SCSI Device
- - - DVDRAM GSA-4040B
- SCSI Host Interface
- - SCSI Device
- - - HITACHI DVD

---

### Post by nocturn on 2005-08-05
Hmmm

The DVD is on an IDE connector, but the device name looks like SCSI, do you have SCSI emulation on for that device?  (check in /boot/grub/menu.lst, what options are passed to the kernel).

---

### Post by heimo on 2005-08-05
There's SCSI emulation for IDE devices (at least for ATAPI) in kernel, but I think it's "old" now and real ide implementation should be used. There's probably kernel parameter to force detection of these devices as a IDE device rather than SCSI-emulated... (*goes googling*)

Hmm... no... Can you check your grub configuration file (somewhere under /etc/grub/) - it should not contain anything like *ide-scsi  *I can't find "anti-parameter" for this, to force detection to IDE - I think it's just the default behaviour.

EDIT: Hi nocturn, I think you have a good point! ;)

Boffa: nocturn probably knows the location of that configuration file better - so it's not under /etc/ as I thought. (My excuse for lack of knowledge here is lilo.)

---

### Post by Boffa on 2005-08-05
[QUOTE=heimo]There's SCSI emulation for IDE devices (at least for ATAPI) in kernel, but I think it's "old" now and real ide implementation should be used. There's probably kernel parameter to force detection of these devices as a IDE device rather than SCSI-emulated... (*goes googling*)

Hmm... no... Can you check your grub configuration file (somewhere under /etc/grub/) - it should not contain anything like *ide-scsi  *I can't find "anti-parameter" for this, to force detection to IDE - I think it's just the default behaviour.

EDIT: Hi nocturn, I think you have a good point! ;)

Boffa: nocturn probably knows the location of that configuration file better - so it's not under /etc/ as I thought. (My excuse for lack of knowledge here is lilo.)[/QUOTE]
 My grub configuration file is at : /boot/grub/menu.lst and looks like this:

mhellden@pheonix:~$ cat /boot/grub/menu.lst
default         0
timeout         10
splashimage=(hd0,0)/boot/grub/images/ubuntu.xpm.gz
title           Ubuntu, kernel 2.6.10-5-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-686 root=/dev/sda1 ro vga=792
initrd          /boot/initrd.img-2.6.10-5-686
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-686 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-686 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.10-5-686
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
savedefault
boot





As you can see this is a standard grub configuration with no parameter for the kernel (except vga mode).

Can you find a parameter that force to IDE ?

---

### Post by Boffa on 2005-08-06
update:

Why is the kernel see the units as "SCSI devices" ?
I no such card in the machine. 
It is a IBM ThinkCentre , about 1,5 year old.


extract from DMESG....
--------------------------------------
SCSI subsystem initialized
libata version 1.10 loaded.
ata_piix version 1.03
ata_piix: combined mode detected
ACPI: PCI interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1f.2 to 64
ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x1880 irq 14
ata1: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4003 85:7c69 86:3e01 87:4003 88:207f
ata1: dev 0 ATA, max UDMA/133, 307757197 sectors: lba48
ata1: dev 0 configured for UDMA/133
scsi0 : ata_piix
elevator: using anticipatory as default io scheduler
  Vendor: ATA       Model: Maxtor 6Y160M0    Rev: YAR5
  Type:   Direct-Access                      ANSI SCSI revision: 05
ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
ata2: dev 1 cfg 49:0f00 82:421c 83:0000 84:0000 85:0000 86:0000 87:0000 88:001f
ata2: dev 1 ATAPI, max UDMA/66
ata2: dev 1 configured for UDMA/33
scsi1 : ata_piix
  Vendor: HL-DT-ST  Model: DVDRAM GSA-4040B  Rev: A109
  Type:   CD-ROM                             ANSI SCSI revision: 05
Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
Attached scsi generic sg1 at scsi1, channel 0, id 1, lun 0,  type 5
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
usbcore: registered new driver usbfs
usbcore: registered new driver hub
Initializing USB Mass Storage driver...
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
SCSI device sda: 307757197 512-byte hdwr sectors (157572 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 307757197 512-byte hdwr sectors (157572 MB)
SCSI device sda: drive cache: write back
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
sr0: scsi3-mmc drive: 32x/32x writer dvd-ram cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
Attached scsi CD-ROM sr0 at scsi1, channel 0, id 1, lun 0

---

### Post by nocturn on 2005-08-08
[QUOTE=Boffa]update:

Why is the kernel see the units as "SCSI devices" ?
I no such card in the machine. 
It is a IBM ThinkCentre , about 1,5 year old.

...
[/QUOTE]

That is very strange, it is loading them as SCSI, but you didn't tell it to do that...
Can you check if hdparm -d1 /dev/hdc does anything?

---

### Post by nocturn on 2005-08-08
I'm not sure if this still works, but try the parameter hdc=cdrom to see if it will drop to IDE.

---

### Post by Boffa on 2005-08-08
None of /dev/hdx are available at all.

And kernel paramater hdc=cdrom didn't do different to the system

I am getting annoyed because of this.

I wonder. Is this a bug due to

a) kernel incompatiblities?
b) hardware limitations? (I would rule this out since DVD-burner works in WinXP)

I alse checked th BIOS. 
As most people know, brands like IBM does not have good BIOS options.
The only thing is about SATA is:

Automatic - regonize SATA controller and IDE controller
Serial ATA - regonize ONLY the SATA device and not IDE devices at all.
None - Only IDE devices.

If I would put in any harddisk on any controller the SATA device would be dead.
thank you IBM sucker.

So that is how it is now.

---

### Post by Boffa on 2005-08-08
Update.

I have to say that I now really believe that it is kernel limitation.
I moved the DVD-burner to another old box and installed the same version of Ubuntu.

And with this computer it is a joy to burn iso.

So where do I sign up this as a B U G ????

---

### Post by Boffa on 2005-08-08
Searching and googling ... 

Probably the problem lies in ICH5 controller and BIOS as mentioned some times before.
Among text to read: 
[http://linux.yyz.us/sata/sata-status.html#ich5](http://linux.yyz.us/sata/sata-status.html#ich5)

But my BIOS doesn't help me to set "Enhanced mode".

If I set SATA only mode I cannot use my CD/DVD players at all.

But in the end the question still is: Could really this cause that DVD-burning fails since reading works.

---

### Post by Boffa on 2005-08-09
I am getting crazy.

If I set BIOS to "SATA only" and run the Ubuntu DVD in "live" mode, the computer boots nicely and I can mount both CDROM and DVD and SATA harddisk.

This shows that probably a re-installation would get it work, but I would preferably not do that.

During normal bootup, DMESG does not show any IDE-devices. I tried to create the dev nodes but didn't work well.

Do I need to recreate a initrd.img is some way ? 
Can I load a module ?

---

### Post by Boffa on 2005-08-09
I think this concludes this BIG HELL of problem.

After reinstallation with BIOS in SATA only mode only I can without problem burn DVD.

Still it is a mystery why Ubuntu would not see the difference in change of BIOS setting before a reinstallation.

---

### Post by heimo on 2005-08-10
I'm very glad you got around the problem. Sad it was so rough. Can you tell us, is your DVD drive used as IDE device now? No longer scd?

---

