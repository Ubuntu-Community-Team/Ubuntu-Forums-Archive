---
title: "Kingston DataTraveler 16GB IO Error"
date: 2009-01-14
forum: General Help
---

### Post by peppers on 2009-01-14
Hi,

I've just bought a Kingston 16GB DataTraveler 100 flash drive. Every time I try to copy files with more than 100mb I get an IO error and the drive is umounted. 

The flash drive is formated in FAT32, but I tried to format with gparted in FAT32, EXT3, RAISERFS, but I keep getting the same error.

The worst thing is that is working great on windows. 
I've tried in 5 diferents PCS, some Ubuntu and some Slackware, with no sucess.

I'm using Ubuntu 8.10 and uname -a gives me:
```
Linux dkt-dti-009 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
```

---

### Post by RichardLinx on 2009-01-14
Hmmm, that's pretty weird. Are you able to copy files larger then 100MB to normal USB flash devices? Was the device unsafely removed? I had a similar problem with a friends 1TB external harddrive once because It was unplugged without safely removing first. Judging by the fact It hasn't worked on 5 Linux computers though I'm going to guess that for whatever reason the drive just isn't compatible with Linux. What file system is your OS using?

EDIT: Just read a few reviews, It seems It is compatible with Linux.

---

### Post by peppers on 2009-01-14
Yes I can copy files larger than 100mb to another flash drive (also kingston, but 2gb), and every other flash drive that I use works, except this 16gb one. 

I also have a 40gb HD in a USB case that also works.

My filesystem is RaiserFS.

And always savely remove!

---

### Post by peppers on 2009-01-14
Now things just get a little bit more complicated....

I tried at my laptop (also ubuntu 8.10) and everything is working... 
I copied files of all sizes....
That just doesn't make any sense!!!

The only thing I think of is some of the hardware at my work's pcs is making coping large files doesn't work. Or maybe I have something instaled thats is making those erros happen... I don't know.

Can someone help me? I'm not an expert linux user, I've been using as my principal OS for a few months only.

---

### Post by peppers on 2009-01-14
Anyone??

---

### Post by JvSivers on 2009-01-30
Hate to bump this, so sorry in advance.

Same problem (mind you I'm having this problem with any file ~50MB). It's really, really stange. Prior to picking up this drive I'd been using an 8GB of the same series (and prior to that a 2GB), without any issues. I used them to move ISO's around all the time.

Also, it works great in Windows, I've tried FAT32 (formatted from Windows and GParted and NTFS). No difference. Both from the GUi and by running...

sudo cp <file> /media/<DRIVENAME>
cp: writing '/media/<DRIVENAME>/<FILE>: Input/Output Error

It hangs for a minute or two, reads, stops reading, then spits and error. One of the guys I work with told me to run dmesg, outputs:

```
[ 4059.490177]  sdc: sdc1
[ 4059.657371] sd 13:0:0:0: [sdc] Attached SCSI removable disk
[ 4059.658039] sd 13:0:0:0: Attached scsi generic sg3 type 0
[ 4159.863491] usb 6-2: USB disconnect, address 16
[ 4161.592053] usb 6-2: new high speed USB device using ehci_hcd and address 17
[ 4161.727187] usb 6-2: configuration #1 chosen from 1 choice
[ 4161.732408] scsi14 : SCSI emulation for USB Mass Storage devices
[ 4161.736780] usb-storage: device found at 17
[ 4161.736804] usb-storage: waiting for device to settle before scanning
[ 4166.736561] usb-storage: device scan complete
[ 4166.737932] scsi 14:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 4166.743618] sd 14:0:0:0: [sdc] 31506432 512-byte hardware sectors (16131 MB)
[ 4166.744990] sd 14:0:0:0: [sdc] Write Protect is off
[ 4166.745006] sd 14:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 4166.745013] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[ 4166.748116] sd 14:0:0:0: [sdc] 31506432 512-byte hardware sectors (16131 MB)
[ 4166.749361] sd 14:0:0:0: [sdc] Write Protect is off
[ 4166.749373] sd 14:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 4166.749380] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[ 4166.750408]  sdc: sdc1
[ 4166.919707] sd 14:0:0:0: [sdc] Attached SCSI removable disk
[ 4166.922138] sd 14:0:0:0: Attached scsi generic sg3 type 0
[ 4206.136066] usb 6-2: reset high speed USB device using ehci_hcd and address 17
[ 4221.248072] usb 6-2: device descriptor read/64, error -110
[ 4236.464554] usb 6-2: device descriptor read/64, error -110
[ 4236.680062] usb 6-2: reset high speed USB device using ehci_hcd and address 17
[ 4251.792557] usb 6-2: device descriptor read/64, error -110
[ 4267.008117] usb 6-2: device descriptor read/64, error -110
[ 4267.224557] usb 6-2: reset high speed USB device using ehci_hcd and address 17
[ 4277.632060] usb 6-2: device not accepting address 17, error -110
[ 4277.744064] usb 6-2: reset high speed USB device using ehci_hcd and address 17
[ 4288.152056] usb 6-2: device not accepting address 17, error -110
[ 4288.152153] usb 6-2: USB disconnect, address 17
[ 4288.153286] sd 14:0:0:0: Device offlined - not ready after error recovery
[ 4288.153367] sd 14:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 4288.153386] end_request: I/O error, dev sdc, sector 42735
[ 4288.159426] sd 14:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 4288.159466] end_request: I/O error, dev sdc, sector 42975
[ 4288.164137] __ratelimit: 14440 callbacks suppressed
[ 4288.164151] Buffer I/O error on device sdc1, logical block 32
[ 4288.164160] lost page write due to I/O error on sdc1
[ 4288.164171] Buffer I/O error on device sdc1, logical block 33
[ 4288.164177] lost page write due to I/O error on sdc1
[ 4288.164185] Buffer I/O error on device sdc1, logical block 34
[ 4288.164191] lost page write due to I/O error on sdc1
[ 4288.164198] Buffer I/O error on device sdc1, logical block 35
[ 4288.164205] lost page write due to I/O error on sdc1
[ 4288.164212] Buffer I/O error on device sdc1, logical block 36
[ 4288.164226] lost page write due to I/O error on sdc1
[ 4288.164234] Buffer I/O error on device sdc1, logical block 37
[ 4288.164240] lost page write due to I/O error on sdc1
[ 4288.164247] Buffer I/O error on device sdc1, logical block 38
[ 4288.164254] lost page write due to I/O error on sdc1
[ 4288.164262] Buffer I/O error on device sdc1, logical block 39
[ 4288.164268] lost page write due to I/O error on sdc1
[ 4288.164278] Buffer I/O error on device sdc1, logical block 40
[ 4288.164291] lost page write due to I/O error on sdc1
[ 4288.164299] Buffer I/O error on device sdc1, logical block 41
[ 4288.164305] lost page write due to I/O error on sdc1
[ 4288.164660] FAT: bread failed in fat_clusters_flush
[ 4288.168627] sd 14:0:0:0: [sdc] READ CAPACITY failed
[ 4288.168643] sd 14:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 4288.168661] sd 14:0:0:0: [sdc] Sense not available.
[ 4288.175084] sd 14:0:0:0: [sdc] Write Protect is off
[ 4288.175101] sd 14:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 4288.175108] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[ 4288.175460] sd 14:0:0:0: [sdc] READ CAPACITY failed
[ 4288.175467] sd 14:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 4288.175478] sd 14:0:0:0: [sdc] Sense not available.
[ 4288.175517] sd 14:0:0:0: [sdc] Write Protect is off
[ 4288.175523] sd 14:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 4288.175529] sd 14:0:0:0: [sdc] Assuming drive cache: write through
[ 4288.199638] FAT: FAT read failed (blocknr 85)
[ 4288.199716] FAT: FAT read failed (blocknr 32)
[ 4288.201051] FAT: unable to read inode block for updating (i_pos 492291)
[ 4288.235577] FAT: unable to read inode block for updating (i_pos 492291)
[ 4288.324703] usb 6-2: new high speed USB device using ehci_hcd and address 18
[ 4303.436066] usb 6-2: device descriptor read/64, error -110
[ 4318.652067] usb 6-2: device descriptor read/64, error -110
[ 4318.868055] usb 6-2: new high speed USB device using ehci_hcd and address 19
[ 4333.980557] usb 6-2: device descriptor read/64, error -110
[ 4349.196562] usb 6-2: device descriptor read/64, error -110
[ 4349.412555] usb 6-2: new high speed USB device using ehci_hcd and address 20

```

Hopefully that's not to much info there.

Input (or output, whichever) would be awesome. Thanks!

---

### Post by Russell Burrows on 2009-01-30
[ 4288.152056] usb 6-2: device not accepting address 17, error -110



I have the same problem.


Toshiba satellite laptop brand new with three gigs of ram and ubuntu 8.1 32bit.

A sandisk 4 gb memory stick works fine.

However.

Pop in a KINGSTON 8GB usb stick be it in fat32 and the same problem hits:

When trying to copy a file from the laptop to the memory stick it halts at 56.8 MB and says I/O error! and auto unmounts the usb stick.

Ahh but when sending a file from the 8gb Kinston to the laptop then everything works fine with full transfer or full copy with no problems.

So yeah its WTF time for me also.

Any ideas any one?

Hmmmmm?
Also, if this is one of the cheap taiwanise device then you might
have to tweak the modprobe params.

Where was your Kingston 16 GB usb memory stick made?

Thanks in advance for reading this.

---

### Post by JvSivers on 2009-01-30
Oh, yeah, should have mentioned it's a Sattelite with...3GB of RAM.

I'm starting to think this is a firmware issue with the stick itself...

---

### Post by Russell Burrows on 2009-02-01
Hmmmm..........



I forgot to ask if you tried usb sticks in 8 GB and 16 GB from Sandisk, Corsair, PNY, geek squad, Kodak, HP, ATP, and others to see if its just limited to Kingston memory sticks in 8 GB and 16 GB versions?

Tuesday when stores are open again I will try to see if I can find some 8 GB mem sticks from PNY or Sandisk to see if the problem is limited to Kingston?

---

### Post by Boomhauer on 2009-02-01
i use an 8gb kingston with no problems at all.

---

### Post by Russell Burrows on 2009-02-01
> **Boomhauer said:**
> i use an 8gb kingston with no problems at all.

Maybe a bit more info from you?

Like what Toshiba Satellite laptop are you using?

What model number?

Ram size?

What Linux distro?

32bit or 64bit?

Serial and where made on that 8GB Kingston stick?

Not to jump on you but when someone is asking for help a NONinformative response is very uncalled for.:(



Update:

[http://www.kingston.com/support/howtodt/default.asp](http://www.kingston.com/support/howtodt/default.asp)

Notice how xp, vista and mac os are supported.

And Linux shows nada, zip for support from Kingston usb sticks.

Me thinks its time for me to stop buying Kingston and say yes to Sandisk purchases.

---

### Post by trebort-sorf on 2009-02-26
.

---

### Post by vurte on 2009-03-02
I've the same error with my Kingstan DataTraveler DTI/16GB,
which I bought yesterday.

It works on windows but doesn't works on Linux.

It's the first usb drive, I know, which didn't work with Linux and I had to buy it .... :(

---

### Post by Eyeless Blond on 2009-04-20
Same problem here. Kingston Datatraveler DTI 16GB. Crashed on transfer of large files, but seems perfectly fine when transferring even large batches of small files whose size totals much greater than the larger file. 

Relevant part of syslog seems to be:

```
Apr 20 17:50:12 Eyes kernel: [66906.145059] sd 6:0:0:0: Attached scsi generic sg2 type 0
Apr 20 17:50:13 Eyes hald: mounted /dev/sdb1 on behalf of uid 1000
Apr 20 17:51:10 Eyes kernel: [66963.205268] usb 1-2.3: reset high speed USB device using ehci_hcd and address 6
Apr 20 17:51:22 Eyes kernel: [66975.732951] usb 1-2.3: device descriptor read/64, error -110
Apr 20 17:51:37 Eyes kernel: [66990.909046] usb 1-2.3: device descriptor read/64, error -110
Apr 20 17:51:37 Eyes kernel: [66991.084505] usb 1-2.3: reset high speed USB device using ehci_hcd and address 6
Apr 20 17:51:53 Eyes kernel: [67006.156238] usb 1-2.3: device descriptor read/64, error -110
Apr 20 17:52:08 Eyes kernel: [67021.333045] usb 1-2.3: device descriptor read/64, error -110
Apr 20 17:52:08 Eyes kernel: [67021.508546] usb 1-2.3: reset high speed USB device using ehci_hcd and address 6
Apr 20 17:52:18 Eyes kernel: [67031.916523] usb 1-2.3: device not accepting address 6, error -110
Apr 20 17:52:18 Eyes kernel: [67031.989814] usb 1-2.3: reset high speed USB device using ehci_hcd and address 6
Apr 20 17:52:29 Eyes kernel: [67042.396541] usb 1-2.3: device not accepting address 6, error -110
Apr 20 17:52:29 Eyes kernel: [67042.396912] sd 6:0:0:0: Device offlined - not ready after error recovery
Apr 20 17:52:29 Eyes kernel: [67042.396932] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Apr 20 17:52:29 Eyes kernel: [67042.396941] end_request: I/O error, dev sdb, sector 443600
Apr 20 17:52:29 Eyes kernel: [67042.396948] usb 1-2.3: USB disconnect, address 6
```


Interestingly enough, it seems that when I keep the drive plugged in awhile and transfer a bunch of small files to/from it, it handles the big files just fine. Isn't that weird?

---

### Post by suvasimon on 2009-07-07
FWIW I have one of these flash drives and I see similar problems with Ubuntu 9.04 on one clone PC but it works perfectly with another clone running xubuntu 9.04 and on a Dell PC running Hardy. It also works with a Macbook pro running OS X. The PC that has problems has a Gigabyte motherboard and AMD Athlon CPU, the other two PC's have different Intel CPU's (a legacy P4 and a recent Dual core 64 bit one). 

There's a lot of variables there, it would be good to try switching disks around to see if it's related to the software installed, but that isn't possible due to controller differences and/or ownership of the PCs.

My gut feeling is that there is an issue with the USB device driver, the USB chipset and these particular flash drives. 

It would be useful to borrow another flash drive and see if that works, and also to try booting the 'problem'  PC with a different OS and see if the problem persists - then again with the current price of flash drives it's probably less hassle to buy a different one...

---

### Post by AndiHoffi on 2010-01-22
Same problem here with a Kingston DataTraveller 400 with 2 GB: Copying files of about 100MB and above fails and unmounts the drive. Anyway, the oddity begins a bit earlier: When beginning to copy the file, the progress bar starts off at about 200 MB and progresses very slowly from there (about 3 MB every 5 seconds). After some time, the copy fails. With files below 200 MB, the progress bar starts at 100%.

System:
Brand new Asus-Mainboard, 2GB RAM, AMD 64-processor, three HDDs, one IDE, two SATA.
Brand new installation of Ubuntu 9.10.
The system was even able to install itself from the exact same stick.
Windows is able to write on the stick without any issues.

---

### Post by jaclfh on 2010-01-27
I don't know what chipsets others in this thread have, but I have an Asus motherboard with AMD SB700 southbridge. Kingston Datatraveler DT100 / 16 GB fails with input/output error when writing large amounts of data to it and the device disappears (including from /proc/partitions). It has to be replugged to get it back. As a bonus, the filesystem gets corrupted (not surprising since it just fails and disappears while writing to it.)

The memory stick works fine on machines with different hardware, but fails with another model Asus motherboard with the same southbridge.

Here are two threads about this:

[http://vip.asus.com/forum/view.aspx?SLanguage=en-us&id=20081003191859937&board_id=1&model=M3A&page=1&count=25](http://vip.asus.com/forum/view.aspx?SLanguage=en-us&id=20081003191859937&board_id=1&model=M3A&page=1&count=25)

[http://vip.asus.com/forum/view.aspx?id=20090609085403518&board_id=1&model=M4A78-EM&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20090609085403518&board_id=1&model=M4A78-EM&page=1&SLanguage=en-us)

The last post of the first thread says:

[QUOTE=qbusss]
That is hardware issue of AMD SB700 Family Southbridges (SB700, SB710, SB750) and they (AMD) know about it from a long time... :-( We can only blame AMD for their pooor support...

...from AMD SB700 Family Product Errata:

Transmission Errors on Packet Identifier May Cause USB® Host Controller To Reinitialize Device

Description:
When receiving a packet identifier (PID) from a USB device while performing asynchronous data transfers, the SouthBridge’s USB host controller may not compare the packet type field to its check bits if the incoming packet type decodes as a STALL handshake. If transmission errors on an incoming packet cause a different packet type field in a PID to match the encoding for a STALL handshake, the SouthBridge may relay the STALL handshake to the application layer instead of ignoring the packet.

Potential Effect on System:
USB host driver software may act on an erroneous STALL handshake and perform a device re-initialization. USB devices should respond to this re-initialization and resume normal operation after a brief delay. If a device is unable to respond correctly to the re-initialization it may disconnect from the host unexpectedly.

Suggested Workaround:
None.

Fix Planned:
Under consideration for a future release.
[/QUOTE]

So.. both AMD and Kingston suck and in this case they suck in an incompatible way.

---

### Post by GreyyAsh on 2010-03-25
> **peppers said:**
> Hi,

I've just bought a Kingston 16GB DataTraveler 100 flash drive. Every time I try to copy files with more than 100mb I get an IO error and the drive is umounted. 

The flash drive is formated in FAT32, but I tried to format with gparted in FAT32, EXT3, RAISERFS, but I keep getting the same error.

The worst thing is that is working great on windows. 
I've tried in 5 diferents PCS, some Ubuntu and some Slackware, with no sucess.

I'm using Ubuntu 8.10 and uname -a gives me:
```
Linux dkt-dti-009 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
```

 Think I might have this problem too with a dell laptop using   Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10) (ATI 200M) and a dt100/16gb. Time outs occur under windows xp x64 and windows 7 and under Linux (I have a dual boot) when transferring  files bigger than 150 mb. I wish I had a non amd/ati comp to test in. Cheers

---

### Post by Maheriano on 2010-03-25
I got a 8 gibibyte Kingston Data Traveler flash drive which has been plug and play since the day I got it on every computer I've tried it in, both Windows and my 2 Ubuntu machines. Seems like it's only the 16s that are affected.

---

### Post by Nonsense on 2010-09-11
I've had the same problem on some Ubuntu machines with my Datatraveler 8GB.

dmesg:

```
[    1.879007] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-5/input0
[    1.879031] usbcore: registered new interface driver usbhid
[    1.879034] usbhid: v2.6:USB HID core driver
[    1.901604] usb 2-3.1: new full speed USB device using ehci_hcd and address 4
[    2.008195] usb 2-3.1: configuration #1 chosen from 1 choice
[    2.080451] usb 2-3.2: new full speed USB device using ehci_hcd and address 5
[    2.097962] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.174935] usb 2-3.2: configuration #1 chosen from 1 choice
[    6.321917] usb-storage: device scan complete
[    6.326261] scsi 6:0:0:0: Direct-Access     Sony     USB   HS-CF Card 3.95 PQ: 0 ANSI: 0
[    6.330119] scsi 6:0:0:1: Direct-Access     Sony     USB   HS-SM Card 3.95 PQ: 0 ANSI: 0
[    6.334244] scsi 6:0:0:2: Direct-Access     Sony     USB   HS-MS Card 3.95 PQ: 0 ANSI: 0
[    6.337616] scsi 6:0:0:3: Direct-Access     Sony     USB   HS-SD Card 3.95 PQ: 0 ANSI: 0
[    6.338077] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.338185] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    6.338277] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    6.338368] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    6.351483] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    6.410111] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    6.414737] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    6.419366] sd 6:0:0:3: [sde] Attached SCSI removable disk
[   10.485800] udev: starting version 151
[   10.559932] i2c i2c-0: nForce2 SMBus adapter at 0x600
[   10.559949] i2c i2c-1: nForce2 SMBus adapter at 0x700
[   10.582637] Adding 8691704k swap on /dev/sda5.  Priority:-1 extents:1 across:8691704k 
[   10.588077] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   10.641725] vga16fb: initializing
[   10.641728] vga16fb: mapped to 0xc00a0000
[   10.641783] fb0: VGA16 VGA frame buffer device
[   10.650313] lp: driver loaded but no devices found
[   10.686792] Linux agpgart interface v0.103
[   10.759447] nvidia: module license 'NVIDIA' taints kernel.
[   10.759451] Disabling lock debugging due to kernel taint
[   10.798237] type=1505 audit(1284197528.695:2):  operation="profile_load" pid=677 name="/sbin/dhclient3"
[   10.798446] type=1505 audit(1284197528.695:3):  operation="profile_load" pid=677 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.798566] type=1505 audit(1284197528.695:4):  operation="profile_load" pid=677 name="/usr/lib/connman/scripts/dhclient-script"
[   11.593510] parport_pc 00:05: reported by Plug and Play ACPI
[   11.593554] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.730708] Linux video capture interface: v2.00
[   11.736357] gspca: main v2.7.0 registered
[   11.737857] gspca: probing 045e:00f7
[   11.738431] sonixj: Sonix chip id: 11
[   11.738849] gspca: probe ok
[   11.738860] gspca: probing 045e:00f7
[   11.738869] gspca: probing 045e:00f7
[   11.738906] usbcore: registered new interface driver sonixj
[   11.739432] sonixj: registered
[   11.753635] ppdev: user-space parallel port driver
[   11.780180] lp0: using parport0 (interrupt-driven).
[   11.832633] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   11.832638] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   11.832641] hda_intel: Disable MSI for Nvidia chipset
[   11.832668] HDA Intel 0000:00:07.0: setting latency timer to 64
[   11.851631] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0027
[   11.851650] usbcore: registered new interface driver usblp
[   11.854600] usbcore: registered new interface driver snd-usb-audio
[   11.893183] Console: switching to colour frame buffer device 80x30
[   12.632736] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
[   12.632742] nvidia 0000:00:12.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
[   12.632749] nvidia 0000:00:12.0: setting latency timer to 64
[   12.632753] vgaarb: device changed decodes: PCI:0000:00:12.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.632976] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   37.434606] type=1505 audit(1284197555.331:5):  operation="profile_load" pid=896 name="/usr/share/gdm/guest-session/Xsession"
[   37.436366] type=1505 audit(1284197555.335:6):  operation="profile_replace" pid=897 name="/sbin/dhclient3"
[   37.436586] type=1505 audit(1284197555.335:7):  operation="profile_replace" pid=897 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   37.436711] type=1505 audit(1284197555.335:8):  operation="profile_replace" pid=897 name="/usr/lib/connman/scripts/dhclient-script"
[   37.443810] type=1505 audit(1284197555.339:9):  operation="profile_load" pid=899 name="/usr/bin/evince"
[   37.446663] type=1505 audit(1284197555.343:10):  operation="profile_load" pid=899 name="/usr/bin/evince-previewer"
[   37.448623] type=1505 audit(1284197555.347:11):  operation="profile_load" pid=899 name="/usr/bin/evince-thumbnailer"
[   37.456113]   alloc irq_desc for 31 on node -1
[   37.456116]   alloc kstat_irqs on node -1
[   37.456125] forcedeth 0000:00:0a.0: irq 31 for MSI/MSI-X
[   37.465515] type=1505 audit(1284197555.363:12):  operation="profile_load" pid=964 name="/usr/lib/cups/backend/cups-pdf"
[   37.465786] type=1505 audit(1284197555.363:13):  operation="profile_load" pid=964 name="/usr/sbin/cupsd"
[   37.471709] type=1505 audit(1284197555.367:14):  operation="profile_load" pid=968 name="/usr/sbin/tcpdump"
[   37.627749] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   37.627754] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   37.627755] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   37.627756] vboxdrv: the usage of hardware performance counters by
[   37.627757] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   37.627760] vboxdrv: Found 2 processor cores.
[   37.628442] vboxdrv: fAsync=1 offMin=0x1d16c offMax=0x1d16c
[   37.628920] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   37.628922] vboxdrv: Successfully loaded version 3.2.8 (interface 0x00140001).
[   38.060346] CE: hpet increasing min_delta_ns to 15000 nsec
[   38.264495] CPU0 attaching NULL sched-domain.
[   38.264500] CPU1 attaching NULL sched-domain.
[   38.340246] CPU0 attaching sched-domain:
[   38.340250]  domain 0: span 0-1 level MC
[   38.340253]   groups: 0 1
[   38.340258] CPU1 attaching sched-domain:
[   38.340260]  domain 0: span 0-1 level MC
[   38.340262]   groups: 1 0
[   39.512053] usb 2-3.1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   39.815832] CPU0 attaching NULL sched-domain.
[   39.815839] CPU1 attaching NULL sched-domain.
[   39.836083] CPU0 attaching sched-domain:
[   39.836088]  domain 0: span 0-1 level MC
[   39.836090]   groups: 0 1
[   39.836096] CPU1 attaching sched-domain:
[   39.836097]  domain 0: span 0-1 level MC
[   39.836099]   groups: 1 0
[   47.912188] eth0: no IPv6 routers present
[  619.230421] operapluginwrap[1942]: segfault at 0 ip (null) sp bf957d0c error 14 in operapluginwrapper[8048000+2b000]
[  619.244573] operapluginwrap[1946]: segfault at 0 ip (null) sp bfeb00ec error 14 in operapluginwrapper[8048000+2b000]
[  619.251016] operapluginwrap[1947]: segfault at 0 ip (null) sp bfbc6f7c error 14 in operapluginwrapper[8048000+2b000]
[  619.257928] operapluginwrap[1948]: segfault at 0 ip (null) sp bf8c82fc error 14 in operapluginwrapper[8048000+2b000]
[  619.294303] operapluginwrap[1951]: segfault at 0 ip (null) sp bf9105fc error 14 in operapluginwrapper[8048000+2b000]
[  619.304406] operapluginwrap[1953]: segfault at 0 ip (null) sp bfe4548c error 14 in operapluginwrapper[8048000+2b000]
[  619.310838] operapluginwrap[1954]: segfault at 0 ip (null) sp bff2c36c error 14 in operapluginwrapper[8048000+2b000]
[  619.317322] operapluginwrap[1955]: segfault at 0 ip (null) sp bfdb379c error 14 in operapluginwrapper[8048000+2b000]
[  661.713963] operapluginwrap[2009]: segfault at 0 ip (null) sp bfff575c error 14 in operapluginwrapper[8048000+2b000]
[  661.729969] operapluginwrap[2012]: segfault at 0 ip (null) sp bfe3ee2c error 14 in operapluginwrapper[8048000+2b000]
[  661.737245] operapluginwrap[2013]: segfault at 0 ip (null) sp bf95eebc error 14 in operapluginwrapper[8048000+2b000]
[  661.744446] operapluginwrap[2014]: segfault at 0 ip (null) sp bff46f6c error 14 in operapluginwrapper[8048000+2b000]
[  661.768297] operapluginwrap[2017]: segfault at 0 ip (null) sp bf959c8c error 14 in operapluginwrapper[8048000+2b000]
[  661.779177] operapluginwrap[2019]: segfault at 0 ip (null) sp bf96139c error 14 in operapluginwrapper[8048000+2b000]
[  661.786260] operapluginwrap[2020]: segfault at 0 ip (null) sp bfcec30c error 14 in operapluginwrapper[8048000+2b000]
[  661.793015] operapluginwrap[2021]: segfault at 0 ip (null) sp bfc2538c error 14 in operapluginwrapper[8048000+2b000]
[  669.214437] operapluginwrap[2032]: segfault at 0 ip (null) sp bfac37dc error 14 in operapluginwrapper[8048000+2b000]
[  669.228861] operapluginwrap[2035]: segfault at 0 ip (null) sp bfc0b80c error 14 in operapluginwrapper[8048000+2b000]
[  669.235131] operapluginwrap[2036]: segfault at 0 ip (null) sp bf8e003c error 14 in operapluginwrapper[8048000+2b000]
[  669.241915] operapluginwrap[2037]: segfault at 0 ip (null) sp bfcf3c6c error 14 in operapluginwrapper[8048000+2b000]
[  669.263278] operapluginwrap[2040]: segfault at 0 ip (null) sp bfc6870c error 14 in operapluginwrapper[8048000+2b000]
[  669.273264] operapluginwrap[2042]: segfault at 0 ip (null) sp bfb713ac error 14 in operapluginwrapper[8048000+2b000]
[  669.279607] operapluginwrap[2043]: segfault at 0 ip (null) sp bfd2889c error 14 in operapluginwrapper[8048000+2b000]
[  669.286131] operapluginwrap[2044]: segfault at 0 ip (null) sp bf9bd19c error 14 in operapluginwrapper[8048000+2b000]
[ 1691.417352] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 2456.869638] usb 2-3.4: new high speed USB device using ehci_hcd and address 6
[ 2456.965120] usb 2-3.4: configuration #1 chosen from 1 choice
[ 2456.971815] scsi7 : SCSI emulation for USB Mass Storage devices
[ 2456.976114] usb-storage: device found at 6
[ 2456.976117] usb-storage: waiting for device to settle before scanning
[ 2461.976679] usb-storage: device scan complete
[ 2461.978795] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 2461.981443] sd 7:0:0:0: Attached scsi generic sg6 type 0
[ 2461.983338] sd 7:0:0:0: [sdf] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 2461.985124] sd 7:0:0:0: [sdf] Write Protect is off
[ 2461.985129] sd 7:0:0:0: [sdf] Mode Sense: 23 00 00 00
[ 2461.985131] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 2461.989506] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 2461.989511]  sdf: sdf1
[ 2462.162382] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 2462.162388] sd 7:0:0:0: [sdf] Attached SCSI removable disk
[ 2502.750880] usb 2-3.4: USB disconnect, address 6
[ 2504.741537] usb 2-3.4: new high speed USB device using ehci_hcd and address 7
[ 2504.836991] usb 2-3.4: configuration #1 chosen from 1 choice
[ 2504.845256] scsi8 : SCSI emulation for USB Mass Storage devices
[ 2504.847427] usb-storage: device found at 7
[ 2504.847430] usb-storage: waiting for device to settle before scanning
[ 2509.844584] usb-storage: device scan complete
[ 2509.846791] scsi 8:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 2509.847316] sd 8:0:0:0: Attached scsi generic sg6 type 0
[ 2509.850649] sd 8:0:0:0: [sdf] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 2509.851342] sd 8:0:0:0: [sdf] Write Protect is off
[ 2509.851345] sd 8:0:0:0: [sdf] Mode Sense: 23 00 00 00
[ 2509.851347] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[ 2509.856411] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[ 2509.856417]  sdf: sdf1
[ 2510.114344] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[ 2510.114350] sd 8:0:0:0: [sdf] Attached SCSI removable disk
[ 2730.421631] usb 2-3.4: reset high speed USB device using ehci_hcd and address 7
[ 2736.664633] usb 2-3.4: device descriptor read/64, error -32
[ 2736.841632] usb 2-3.4: device descriptor read/64, error -32
[ 2737.021476] usb 2-3.4: reset high speed USB device using ehci_hcd and address 7
[ 2737.097464] usb 2-3.4: device descriptor read/64, error -32
[ 2737.277630] usb 2-3.4: device descriptor read/64, error -32
[ 2737.452483] usb 2-3.4: reset high speed USB device using ehci_hcd and address 7
[ 2737.860212] usb 2-3.4: device not accepting address 7, error -32
[ 2737.932480] usb 2-3.4: reset high speed USB device using ehci_hcd and address 7
[ 2738.340238] usb 2-3.4: device not accepting address 7, error -32
[ 2738.340802] sd 8:0:0:0: [sdf] Unhandled error code
[ 2738.340805] sd 8:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2738.340808] sd 8:0:0:0: [sdf] CDB: Read(10): 28 00 00 16 9e 18 00 00 f0 00
[ 2738.340816] end_request: I/O error, dev sdf, sector 1482264
[ 2738.340899] sd 8:0:0:0: [sdf] Unhandled error code
[ 2738.340901] sd 8:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2738.340904] sd 8:0:0:0: [sdf] CDB: Read(10): 28 00 00 16 9f 08 00 00 10 00
[ 2738.340910] end_request: I/O error, dev sdf, sector 1482504
[ 2738.340961] sd 8:0:0:0: [sdf] Unhandled error code
[ 2738.340962] sd 8:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2738.340965] sd 8:0:0:0: [sdf] CDB: Read(10): 28 00 00 16 9f 18 00 00 f0 00
[ 2738.340971] end_request: I/O error, dev sdf, sector 1482520
[ 2738.342176] usb 2-3.4: USB disconnect, address 7
[ 2738.561467] usb 2-3.4: new high speed USB device using ehci_hcd and address 8
[ 2738.636464] usb 2-3.4: device descriptor read/64, error -32
[ 2738.814542] usb 2-3.4: device descriptor read/64, error -32
[ 2738.989635] usb 2-3.4: new high speed USB device using ehci_hcd and address 9
[ 2739.065466] usb 2-3.4: device descriptor read/64, error -32
[ 2739.241629] usb 2-3.4: device descriptor read/64, error -32
[ 2739.417636] usb 2-3.4: new high speed USB device using ehci_hcd and address 10
[ 2739.824204] usb 2-3.4: device not accepting address 10, error -32
[ 2739.897636] usb 2-3.4: new high speed USB device using ehci_hcd and address 11
[ 2740.308038] usb 2-3.4: device not accepting address 11, error -32
[ 2740.308365] hub 2-3:1.0: unable to enumerate USB device on port 4
[ 2747.429631] usb 2-3.4: new high speed USB device using ehci_hcd and address 12
[ 2747.525123] usb 2-3.4: configuration #1 chosen from 1 choice
[ 2747.534786] scsi9 : SCSI emulation for USB Mass Storage devices
[ 2747.539373] usb-storage: device found at 12
[ 2747.539376] usb-storage: waiting for device to settle before scanning
[ 2752.536376] usb-storage: device scan complete
[ 2752.538485] scsi 9:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 2752.539034] sd 9:0:0:0: Attached scsi generic sg6 type 0
[ 2752.539834] sd 9:0:0:0: [sdf] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 2752.541374] sd 9:0:0:0: [sdf] Write Protect is off
[ 2752.541379] sd 9:0:0:0: [sdf] Mode Sense: 23 00 00 00
[ 2752.541381] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[ 2752.547570] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[ 2752.547577]  sdf: sdf1
[ 2752.806351] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[ 2752.806356] sd 9:0:0:0: [sdf] Attached SCSI removable disk
[ 2866.340473] usb 2-3.4: reset high speed USB device using ehci_hcd and address 12
[ 2872.584473] usb 2-3.4: device descriptor read/64, error -32
[ 2872.761473] usb 2-3.4: device descriptor read/64, error -32
[ 2872.936500] usb 2-3.4: reset high speed USB device using ehci_hcd and address 12
[ 2873.008525] usb 2-3.4: device descriptor read/64, error -32
[ 2873.185631] usb 2-3.4: device descriptor read/64, error -32
[ 2873.361643] usb 2-3.4: reset high speed USB device using ehci_hcd and address 12
[ 2873.768040] usb 2-3.4: device not accepting address 12, error -32
[ 2873.841476] usb 2-3.4: reset high speed USB device using ehci_hcd and address 12
[ 2874.248201] usb 2-3.4: device not accepting address 12, error -32
[ 2874.249293] sd 9:0:0:0: [sdf] Unhandled error code
[ 2874.249296] sd 9:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2874.249299] sd 9:0:0:0: [sdf] CDB: Read(10): 28 00 00 e1 0a 58 00 00 f0 00
[ 2874.249307] end_request: I/O error, dev sdf, sector 14748248
[ 2874.249532] sd 9:0:0:0: [sdf] Unhandled error code
[ 2874.249533] sd 9:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2874.249536] sd 9:0:0:0: [sdf] CDB: Read(10): 28 00 00 e1 0b 48 00 00 10 00
[ 2874.249543] end_request: I/O error, dev sdf, sector 14748488
[ 2874.249976] usb 2-3.4: USB disconnect, address 12
[ 2874.251274] sd 9:0:0:0: [sdf] Unhandled error code
[ 2874.251279] sd 9:0:0:0: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 2874.251282] sd 9:0:0:0: [sdf] CDB: Read(10): 28 00 00 e1 0b 58 00 00 f0 00
[ 2874.251290] end_request: I/O error, dev sdf, sector 14748504
[ 2874.343668] FAT: Directory bread(block 14743872) failed
[ 2874.344026] FAT: Directory bread(block 14743873) failed
[ 2874.344036] FAT: Directory bread(block 14743874) failed
[ 2874.344248] FAT: Directory bread(block 14743875) failed
[ 2874.344660] FAT: Directory bread(block 14743876) failed
[ 2874.345283] FAT: Directory bread(block 14743877) failed
[ 2874.345308] FAT: Directory bread(block 14743878) failed
[ 2874.345315] FAT: Directory bread(block 14743879) failed
[ 2874.412464] usb 2-3.4: new high speed USB device using ehci_hcd and address 13
[ 2874.484470] usb 2-3.4: device descriptor read/64, error -32
[ 2874.660478] usb 2-3.4: device descriptor read/64, error -32
[ 2874.837639] usb 2-3.4: new high speed USB device using ehci_hcd and address 14
[ 2874.913640] usb 2-3.4: device descriptor read/64, error -32
[ 2875.090253] usb 2-3.4: device descriptor read/64, error -32
[ 2875.265640] usb 2-3.4: new high speed USB device using ehci_hcd and address 15
[ 2875.672035] usb 2-3.4: device not accepting address 15, error -32
[ 2875.745626] usb 2-3.4: new high speed USB device using ehci_hcd and address 16
[ 2876.152029] usb 2-3.4: device not accepting address 16, error -32
[ 2876.152466] hub 2-3:1.0: unable to enumerate USB device on port 4
[ 2881.573633] usb 2-3.4: new high speed USB device using ehci_hcd and address 17
[ 2881.673161] usb 2-3.4: configuration #1 chosen from 1 choice
[ 2881.673446] scsi10 : SCSI emulation for USB Mass Storage devices
[ 2881.673542] usb-storage: device found at 17
[ 2881.673544] usb-storage: waiting for device to settle before scanning
[ 2886.672936] usb-storage: device scan complete
[ 2886.674786] scsi 10:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 2886.675183] sd 10:0:0:0: Attached scsi generic sg6 type 0
[ 2886.678299] sd 10:0:0:0: [sdf] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 2886.680512] sd 10:0:0:0: [sdf] Write Protect is off
[ 2886.680517] sd 10:0:0:0: [sdf] Mode Sense: 23 00 00 00
[ 2886.680520] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[ 2886.685520] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[ 2886.685526]  sdf: sdf1
[ 2886.938350] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[ 2886.938355] sd 10:0:0:0: [sdf] Attached SCSI removable disk
[ 2957.085464] usb 2-3.4: reset high speed USB device using ehci_hcd and address 17
[ 2968.332476] usb 2-3.4: device descriptor read/64, error -110
[ 2983.508473] usb 2-3.4: device descriptor read/64, error -110
[ 2983.685626] usb 2-3.4: reset high speed USB device using ehci_hcd and address 17
[ 2991.600908] sd 10:0:0:0: Device offlined - not ready after error recovery
[ 2991.600921] sd 10:0:0:0: [sdf] Unhandled error code
[ 2991.600923] sd 10:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2991.600927] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 ee 5f b0 00 00 f0 00
[ 2991.600935] end_request: I/O error, dev sdf, sector 15622064
[ 2991.600952] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.600973] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.600980] sd 10:0:0:0: [sdf] Unhandled error code
[ 2991.600982] sd 10:0:0:0: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 2991.600985] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 ee 60 a0 00 00 10 00
[ 2991.600991] end_request: I/O error, dev sdf, sector 15622304
[ 2991.601001] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601009] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601014] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601018] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601023] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601028] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601032] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601036] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601041] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601045] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601049] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601054] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601058] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601063] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601067] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601072] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601076] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601080] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601085] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601090] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601097] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601103] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601110] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601114] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601121] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601125] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601130] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601134] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601138] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601142] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601148] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601153] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601157] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601161] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601165] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601169] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601174] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601182] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601192] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601352] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.604718] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.604841] usb 2-3.4: USB disconnect, address 17
[ 2994.980460] usb 2-3.4: new high speed USB device using ehci_hcd and address 18
[ 2995.077239] usb 2-3.4: configuration #1 chosen from 1 choice
[ 2995.086724] scsi11 : SCSI emulation for USB Mass Storage devices
[ 2995.089625] usb-storage: device found at 18
[ 2995.089628] usb-storage: waiting for device to settle before scanning
[ 3000.088392] usb-storage: device scan complete
[ 3000.090799] scsi 11:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 3000.091274] sd 11:0:0:0: Attached scsi generic sg6 type 0
[ 3000.092850] sd 11:0:0:0: [sdf] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 3000.094665] sd 11:0:0:0: [sdf] Write Protect is off
[ 3000.094669] sd 11:0:0:0: [sdf] Mode Sense: 23 00 00 00
[ 3000.094672] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[ 3000.098572] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[ 3000.098578]  sdf: sdf1
[ 3000.350405] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[ 3000.350410] sd 11:0:0:0: [sdf] Attached SCSI removable disk
[ 3362.992845] usb 2-3.4: reset high speed USB device using ehci_hcd and address 18
[ 3369.233634] usb 2-3.4: device descriptor read/64, error -32
[ 3369.409634] usb 2-3.4: device descriptor read/64, error -32
[ 3369.585636] usb 2-3.4: reset high speed USB device using ehci_hcd and address 18
[ 3369.661636] usb 2-3.4: device descriptor read/64, error -32
[ 3369.836470] usb 2-3.4: device descriptor read/64, error -32
[ 3370.012483] usb 2-3.4: reset high speed USB device using ehci_hcd and address 18
[ 3370.420035] usb 2-3.4: device not accepting address 18, error -32
[ 3370.493633] usb 2-3.4: reset high speed USB device using ehci_hcd and address 18
[ 3370.900140] usb 2-3.4: device not accepting address 18, error -32
[ 3370.900755] sd 11:0:0:0: [sdf] Unhandled error code
[ 3370.900758] sd 11:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3370.900761] sd 11:0:0:0: [sdf] CDB: Read(10): 28 00 00 d5 34 a8 00 00 f0 00
[ 3370.900769] end_request: I/O error, dev sdf, sector 13972648
[ 3370.901829] sd 11:0:0:0: [sdf] Unhandled error code
[ 3370.901833] sd 11:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3370.901837] sd 11:0:0:0: [sdf] CDB: Read(10): 28 00 00 d5 35 98 00 00 0c 00
[ 3370.901844] end_request: I/O error, dev sdf, sector 13972888
[ 3370.902052] sd 11:0:0:0: [sdf] Unhandled error code
[ 3370.902053] sd 11:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3370.902056] sd 11:0:0:0: [sdf] CDB: Read(10): 28 00 00 d5 34 a8 00 00 80 00
[ 3370.902062] end_request: I/O error, dev sdf, sector 13972648
[ 3370.902090] usb 2-3.4: USB disconnect, address 18
[ 3371.117628] usb 2-3.4: new high speed USB device using ehci_hcd and address 19
[ 3371.192465] usb 2-3.4: device descriptor read/64, error -32
[ 3371.369631] usb 2-3.4: device descriptor read/64, error -32
[ 3371.545638] usb 2-3.4: new high speed USB device using ehci_hcd and address 20
[ 3371.620680] usb 2-3.4: device descriptor read/64, error -32
[ 3371.797634] usb 2-3.4: device descriptor read/64, error -32
[ 3371.973636] usb 2-3.4: new high speed USB device using ehci_hcd and address 21
[ 3372.380202] usb 2-3.4: device not accepting address 21, error -32
[ 3372.453650] usb 2-3.4: new high speed USB device using ehci_hcd and address 22
[ 3372.860198] usb 2-3.4: device not accepting address 22, error -32
[ 3372.860643] hub 2-3:1.0: unable to enumerate USB device on port 4
[ 3374.140124] FAT: Directory bread(block 13988360) failed
[ 3374.140133] FAT: Directory bread(block 13988361) failed
[ 3374.140139] FAT: Directory bread(block 13988362) failed
[ 3374.140145] FAT: Directory bread(block 13988363) failed
[ 3374.140151] FAT: Directory bread(block 13988364) failed
[ 3374.140156] FAT: Directory bread(block 13988365) failed
[ 3374.140162] FAT: Directory bread(block 13988366) failed
[ 3374.140168] FAT: Directory bread(block 13988367) failed
[ 3374.140178] FAT: FAT read failed (blocknr 13668)
[ 3374.141431] FAT: FAT read failed (blocknr 13668)
[ 3379.240635] usb 2-3.4: new high speed USB device using ehci_hcd and address 23
[ 3379.336992] usb 2-3.4: configuration #1 chosen from 1 choice
[ 3379.337326] scsi12 : SCSI emulation for USB Mass Storage devices
[ 3379.337422] usb-storage: device found at 23
[ 3379.337424] usb-storage: waiting for device to settle before scanning
[ 3384.336749] usb-storage: device scan complete
[ 3384.338525] scsi 12:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 3384.340012] sd 12:0:0:0: Attached scsi generic sg6 type 0
[ 3384.342147] sd 12:0:0:0: [sdf] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 3384.343503] sd 12:0:0:0: [sdf] Write Protect is off
[ 3384.343506] sd 12:0:0:0: [sdf] Mode Sense: 23 00 00 00
[ 3384.343508] sd 12:0:0:0: [sdf] Assuming drive cache: write through
[ 3384.349507] sd 12:0:0:0: [sdf] Assuming drive cache: write through
[ 3384.349510]  sdf: sdf1
[ 3384.601361] sd 12:0:0:0: [sdf] Assuming drive cache: write through
[ 3384.601367] sd 12:0:0:0: [sdf] Attached SCSI removable disk
[ 3411.104793] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3411.104798] ata4.00: irq_stat 0x40000000
[ 3411.104801] sr 3:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 3411.104811] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 3411.104812]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
[ 3411.104815] ata4.00: status: { DRDY }
```

---

### Post by jimmers on 2010-09-11
I run 10.4 on a Kingston Datatraveller G2 16 gb, with no problems, I  also run Maverick on a Kingston G2
 8 gb, again with no problems, my Laptop an Acer Aspire 5738Z, used to have lots of problems with Sandisk, that is the reason I changed to Kingston. The 8 gb drive I used to use for storing instructional videos before installing Maverick.

---

### Post by Ptero-4 on 2010-11-18
I got a [Datatraveler DTI 2GB]("http://www.kings-computers.com/tiendamx/images/dti_2gb.jpg") USB drive that Acts very oddly. If I plug it in a Toshiba laptop I got while it's running any version of Windows, OpenSUSE, SLED or SLES I can copy both large and small files to it without issue, I can even make LiveUSB's using unetbootin, USB-imagewriter, or USB-creator.
My dmesg on OpenSUSE while copying a group of folders full of small files (5MB or less) totaling 1.8GB (the folders are in a separate partition). 
```

wlan0: direct probe to AP 08:10:74:0f:c0:c0 (try 1)                              
wlan0: direct probe responded                                                    
wlan0: authenticate with AP 08:10:74:0f:c0:c0 (try 1)                            
wlan0: authenticated                                                             
wlan0: associate with AP 08:10:74:0f:c0:c0 (try 1)                               
wlan0: RX AssocResp from 08:10:74:0f:c0:c0 (capab=0x411 status=0 aid=1)          
wlan0: associated                                                                
ip_tables: (C) 2000-2006 Netfilter Core Team                                     
nf_conntrack version 0.5.0 (16384 buckets, 65536 max)                            
CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use             
nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or       
sysctl net.netfilter.nf_conntrack_acct=1 to enable it.                           
CE: hpet increasing min_delta_ns to 15000 nsec                                   
usb 2-3.4: new high speed USB device using ehci_hcd and address 4                  
scsi6 : usb-storage 2-3.4:1.0                                                      
usb-storage: device found at 4                                                   
usb-storage: waiting for device to settle before scanning                        
scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2     
usb-storage: device scan complete                                                
sd 6:0:0:0: [sdb] 3973120 512-byte logical blocks: (2.03 GB/1.89 GiB)            
sd 6:0:0:0: [sdb] Write Protect is off                                           
sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00                                        
sd 6:0:0:0: [sdb] Assuming drive cache: write through                            
sd 6:0:0:0: [sdb] Assuming drive cache: write through                            
 sdb: sdb1                                                                       
sd 6:0:0:0: [sdb] Assuming drive cache: write through                            
sd 6:0:0:0: [sdb] Attached SCSI removable disk                                  

```
If OTOH I plug the usb drive in the same laptop while it's running OSX, OpenIndiana, BSD or any non-Novell Linux distro and try to copy the same group of folders totalling 1.8GB the drive unmounts before it can finish the operation. I noticed (at least in this drive) that copying a single large file right after pluging it in works regardless of OS.
My dmesg under Ubuntu 10.10 copying the same group of small files.
```

wlan0: direct probe to AP 08:10:74:0f:c0:c0 (try 1)                              
wlan0: direct probe responded                                                    
wlan0: authenticate with AP 08:10:74:0f:c0:c0 (try 1)                            
wlan0: authenticated                                                             
wlan0: associate with AP 08:10:74:0f:c0:c0 (try 1)                               
wlan0: RX AssocResp from 08:10:74:0f:c0:c0 (capab=0x411 status=0 aid=1)          
wlan0: associated                                                                
ip_tables: (C) 2000-2006 Netfilter Core Team                                     
nf_conntrack version 0.5.0 (16384 buckets, 65536 max)                            
CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use             
nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or       
sysctl net.netfilter.nf_conntrack_acct=1 to enable it.                           
CE: hpet increasing min_delta_ns to 15000 nsec                                   
usb 2-3.4: new high speed USB device using ehci_hcd and address 4                  
scsi6 : usb-storage 2-3.4:1.0                                                      
usb-storage: device found at 4                                                   
usb-storage: waiting for device to settle before scanning                        
scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2     
usb-storage: device scan complete                                                
sd 6:0:0:0: [sdb] 3973120 512-byte logical blocks: (2.03 GB/1.89 GiB)            
sd 6:0:0:0: [sdb] Write Protect is off                                           
sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00                                        
sd 6:0:0:0: [sdb] Assuming drive cache: write through                            
sd 6:0:0:0: [sdb] Assuming drive cache: write through                            
 sdb: sdb1                                                                       
sd 6:0:0:0: [sdb] Assuming drive cache: write through                            
sd 6:0:0:0: [sdb] Attached SCSI removable disk
usb 2-3.4: reset high speed USB device using ehci_hcd and address 4
usb 2-3.4: device descriptor read/64, error -110
usb 2-3.4: device descriptor read/64, error -110
usb 2-3.4: reset high speed USB device using ehci_hcd and address 4
sd 10:0:0:0: Device offlined - not ready after error recovery
sd 10:0:0:0: [sdb] Unhandled error code
sd 10:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
sd 10:0:0:0: [sdb] CDB: Read(10): 28 00 00 ee 5f b0 00 00 f0 00
end_request: I/O error, dev sdb, sector 15622064
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: [sdb] Unhandled error code
sd 10:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
sd 10:0:0:0: [sdb] CDB: Read(10): 28 00 00 ee 60 a0 00 00 10 00
end_request: I/O error, dev sdb, sector 15622304
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
sd 10:0:0:0: rejecting I/O to offline device
usb 2-3.4: USB disconnect, address 4
usb 2-3.4: new high speed USB device using ehci_hcd and address 8
usb 2-3.4: configuration #1 chosen from 1 choice
scsi11 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 8
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
sd 6:0:0:0: [sdb] 3973120 512-byte logical blocks: (2.03 GB/1.89 GiB)            
sd 6:0:0:0: [sdb] Write Protect is off                                           
sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00                                        
sd 6:0:0:0: [sdb] Assuming drive cache: write through                            
sd 6:0:0:0: [sdb] Assuming drive cache: write through                            
 sdb: sdb1                                                                       
sd 6:0:0:0: [sdb] Assuming drive cache: write through                            
sd 6:0:0:0: [sdb] Attached SCSI removable disk
usb 2-3.4: reset high speed USB device using ehci_hcd and address 8
usb 2-3.4: device descriptor read/64, error -32
usb 2-3.4: device descriptor read/64, error -32
usb 2-3.4: reset high speed USB device using ehci_hcd and address 8
usb 2-3.4: device descriptor read/64, error -32
usb 2-3.4: device descriptor read/64, error -32
usb 2-3.4: reset high speed USB device using ehci_hcd and address 8
usb 2-3.4: device not accepting address 8, error -32
usb 2-3.4: reset high speed USB device using ehci_hcd and address 8
usb 2-3.4: device not accepting address 8, error -32
sd 11:0:0:0: [sdb] Unhandled error code
sd 11:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
sd 11:0:0:0: [sdb] CDB: Read(10): 28 00 00 d5 34 a8 00 00 f0 00
end_request: I/O error, dev sdb, sector 13972648
sd 11:0:0:0: [sdb] Unhandled error code
sd 11:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
sd 11:0:0:0: [sdb] CDB: Read(10): 28 00 00 d5 35 98 00 00 0c 00
end_request: I/O error, dev sdb, sector 13972888
sd 11:0:0:0: [sdb] Unhandled error code
sd 11:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
sd 11:0:0:0: [sdb] CDB: Read(10): 28 00 00 d5 34 a8 00 00 80 00
end_request: I/O error, dev sdb, sector 13972648
usb 2-3.4: USB disconnect, address 8
usb 2-3.4: new high speed USB device using ehci_hcd and address 9
usb 2-3.4: device descriptor read/64, error -32
usb 2-3.4: device descriptor read/64, error -32
usb 2-3.4: new high speed USB device using ehci_hcd and address 10
usb 2-3.4: device descriptor read/64, error -32
usb 2-3.4: device descriptor read/64, error -32
usb 2-3.4: new high speed USB device using ehci_hcd and address 11
usb 2-3.4: device not accepting address 21, error -32
usb 2-3.4: new high speed USB device using ehci_hcd and address 12
usb 2-3.4: device not accepting address 22, error -32
hub 2-3:1.0: unable to enumerate USB device on port 4
FAT: Directory bread(block 13988360) failed
FAT: Directory bread(block 13988361) failed
FAT: Directory bread(block 13988362) failed
FAT: Directory bread(block 13988363) failed
FAT: Directory bread(block 13988364) failed
FAT: Directory bread(block 13988365) failed
FAT: Directory bread(block 13988366) failed
FAT: Directory bread(block 13988367) failed
FAT: FAT read failed (blocknr 13668)
FAT: FAT read failed (blocknr 13668)
usb 2-3.4: new high speed USB device using ehci_hcd and address 13
usb 2-3.4: configuration #1 chosen from 1 choice
scsi11 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 13
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
sd 6:0:0:0: [sdb] 3973120 512-byte logical blocks: (2.03 GB/1.89 GiB)            
sd 6:0:0:0: [sdb] Write Protect is off                                           
sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00                                        
sd 6:0:0:0: [sdb] Assuming drive cache: write through                            
sd 6:0:0:0: [sdb] Assuming drive cache: write through                            
 sdb: sdb1                                                                       
sd 6:0:0:0: [sdb] Assuming drive cache: write through                            
sd 6:0:0:0: [sdb] Attached SCSI removable disk
ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata4.00: irq_stat 0x40000000
sr 3:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
ata4.00: status: { DRDY }

```

---

