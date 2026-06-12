---
title: "CD ROM not mountable? (reinstall?)"
date: 2009-11-22
forum: Desktop Environments
---

### Post by thoth3g on 2009-11-22
If there is anyone inclined to give me some ideas it would be greatly appreciated. If I've left something out please let me know.  I've managed to get theme managers, screenlets, splash screen managers etc........Overall I'm very impressed with Ubuntu! (Ubuntu 9.10 (karmic))
 

 I've been scouring the forums and have managed to find most solutions. Some of these listed seem to have posts that are similar but the problems expressed are not the same. (as far as I could tell after reading them repeatedly)
 

 Problems:
 Well, since I have an ATI card I'll probably just be screwed on the **direct rendering.** I've managed to get everything else looking pretty good display wise (just not going to work for any gaming for wow etc) That will be corrected if and when I upgrade my card to anything BUT ATI.
 

 I've been having some c***ompatibility issues with gmail. Firefox ***absolutely does not cooperate. Most of the time it doesn't load. With Thunderbird I think it's routing issues or something else. It does fine except it will not send attachments no matter how small. It will send text messages great. I've installed the recommended Java and flash for Ubuntu successfully (amd 64) but no change.
 

 _**The biggest problem is**_:
 CD/DVD ROM is not installed. I have searched all of the directories to find something to be mounted and come up blank. I can switch back to Vista and place a disk in the drive. When I switch back to Ubuntu it will read the media for the most part (although no twell for music etc). I can get it to eject but if I take the disk out and close the drive it will no longer be visible.   
 I've tried to mount this many times over:
 [SIZE=2]thoth3g@Algol:~$ sudo mount /dev/scd0 [/SIZE]
 [SIZE=2]mount: no medium found on /dev/sr0.etc etc.....[/SIZE]
 

 I will copy and paste mtab and fstab. Fstab seems to state that there was some confusion regarding this drive. (as well as the hardware profile)
 There is something listed as a cdrom drive that is actually my usb pen drive:
 [SIZE=2]id: cdrom[/SIZE]
 [SIZE=2]description: SCSI CD-ROM [/SIZE] 
 [SIZE=2]product: SanDisk Cruzer vendor: SanDisk[/SIZE]
 

 Below is what appears to be a cd rom but the list seems to indicate it's a mounted iso file system. There only thing that I can think of is that perhaps the installer became confused as I am now remembering that I had the usb pen plugged in during installation. Wow, well, not being the guru here I will still leave it to speculation:
 id: medium
 physical id: 0
 logical name: /dev/cdrom
 logical name: /media/cdrom1
 configuration:
                                           mount.fstype
                               =
                               iso9660
                                         mount.options
                               =
                               ro,nosuid,nodev,relatime,utf8
                                         state
                               =
                               mounted
               The hardware profile is attached. Thanks in advance for any insight or help.

FSTAB:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=183f8dd5-31f7-4486-a8ca-b62d3336c895 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c265dca5-1a13-4753-a293-fa44e7e5e85e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0













MTAB:
/dev/sda5 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/home/thoth3g/.Private /home/thoth3g ecryptfs ecryptfs_sig=728a1445122f1a73,ecryptfs_fnek_sig=c8c3f7a6586683b0,ecryptfs_cipher=aes,ecryptfs_key_bytes=16 0 0
gvfs-fuse-daemon /home/thoth3g/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=thoth3g 0 0
/dev/sdg1 /media/Cruzer vfat rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0
/dev/sr1 /media/cdrom1 iso9660 ro,nosuid,nodev,utf8,user=thoth3g 0 0
/dev/sr0 /media/cdrom0 iso9660 ro,nosuid,nodev,utf8,user=thoth3g 0 0

---

### Post by lidex on 2009-11-22
So what happens when you put in a disk in ubuntu? When you go to "Computer" in Nautilus, does it look like this screenshot? My disk drive does not mount until there is a disk in it - in essence mounting the disk not the drive.


*edit: you'll note that the cdrom does not show up in places menu*

---

### Post by jynyl on 2009-11-23
I'm getting similar symptoms here (Kubuntu Karmic 64bit), cd in drive does not automount.  Kubuntu Jaunty on this hardware did automount cd disks.
Manual mount does work, as a user.
```
mount /media/cdrom0
```

Swapping udf and iso9660 in fstab (as recommended in this thread) didn't help.
[http://ubuntuforums.org/showthread.php?t=1235151]("http://ubuntuforums.org/showthread.php?t=1235151")

Any suggestions appreciated.
TIA

Peter

---

### Post by thoth3g on 2009-11-23
Well, first off, to even put a disk into the drive or change disks I have to switch to Vista. When I log over it shows as a mounted file system and has an icon that looks like a disk. With a disk in the drive there is an icon of a disk on the desktop as well as the file browser. It will eject the disk but will not close the tray. As long as I leave a disk in the drive I can swap out disks but if I close the cd/dvd  without a disk, the icon is completely removed from the desktop.
In Nautilus:
Attachment one
The properties:
Attachment two

It almost looks to me that perhaps I confused the installer. There's a cd/dvd rom listed with the name of Cruzer. Cruser is my usb pen.
I'm thinking that I may install it again to see if it fixes it. It should go a bit faster than it did the last time.

> **lidex said:**
> So what happens when you put in a disk in ubuntu? When you go to "Computer" in Nautilus, does it look like this screenshot? My disk drive does not mount until there is a disk in it - in essence mounting the disk not the drive.


*edit: you'll note that the cdrom does not show up in places menu*

---

### Post by thoth3g on 2009-11-23
So far I'm inclined to blame the hardware. It's not just a matter of the cd dvd mounting correctly. The drive door does not operate when you push the button. By looking at the connector I can tell it's not the usual ribbon style connection to the mother board.

I'll keep looking around for solutions and let you know if I find one. I'll likely try other distros or versions if I'm not successful.

---

### Post by sand7000 on 2009-11-23
are you sure your user has access to the drive? If you run
```

sudo users-admin

```
you can make sure you have cdrom privileges. I had to enable fuse before I could mount my usb drives.

---

### Post by thoth3g on 2009-11-23
Yeah, I have the admin rights. 

Even if it doesn't auto mount, it should still open the CD tray when I push the button I presume.

---

### Post by lidex on 2009-11-23
Is that a sata cable you refer to?
Is this a desktop or notebook? You could try pulling out the drive and cleaning it. Make sure the cables are securely connected. May be power supply issue - switch to another lead if available. If you can access another drive, hook it up and try. If that one works, you'll know yours is faulty.

---

### Post by thoth3g on 2009-11-23
_I have no doubt that the cd dvd rom is good_. For one, this is a new computer and also because it works just fine under windows on the other partition. I had hoped to trigger a plug and play feature and have already unplugged and put it in a different port. Pretty much the same deal. My power supply is sufficient.
Maybe it's because it's a gateway....lol


> **lidex said:**
> Is that a sata cable you refer to?
Is this a desktop or notebook? You could try pulling out the drive and cleaning it. Make sure the cables are securely connected. May be power supply issue - switch to another lead if available. If you can access another drive, hook it up and try. If that one works, you'll know yours is faulty.

---

### Post by lidex on 2009-11-23
The bottom line in my fstab:
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Looking at /dev/scd0 shows it's a link to /dev/sr0.
Have you looked at dmesg?

---

### Post by thoth3g on 2009-11-23
Yup, mine is the same:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

also:
[SIZE=1]thoth3g@ALGOL:~$ sudo mount /dev/scd0
[sudo] password for thoth3g: 
mount: no medium found on /dev/sr0
thoth3g@ALGOL:~$ sudo mount /media/cdrom0
mount: no medium found on /dev/sr0[/SIZE]



> **lidex said:**
> The bottom line in my fstab:
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Looking at /dev/scd0 shows it's a link to /dev/sr0.
Have you looked at dmesg?

---

### Post by thoth3g on 2009-11-24
Oh, and the connection that I spoke of is Sata (sata 2 specifically). It's much smaller than the larger flat type. It has a total of 6 identical sata plug female ports.

---

### Post by lidex on 2009-11-24
can you post the output of this command?
```
dmesg | grep ata
```

---

### Post by thoth3g on 2009-11-24
[    0.000000]  BIOS-e820: 00000000cff90000 - 00000000cff9e000 (ACPI data)
[    0.000000]  modified: 00000000cff90000 - 00000000cff9e000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] PERCPU: Embedded 30 pages at ffff880028034000, static data 90720 bytes
[    0.000000] Memory: 5859964k/6815744k available (5315k kernel code, 787332k absent, 168448k reserved, 3018k data, 660k init)
[    0.323939] libata version 3.00 loaded.
[    0.767546] ata1: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff900 irq 27
[    0.767550] ata2: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ff980 irq 27
[    0.767552] ata3: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa00 irq 27
[    0.767555] ata4: SATA max UDMA/133 abar m1024@0xfe7ff800 port 0xfe7ffa80 irq 27
[    0.767779] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.767802] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    0.767867] scsi4 : pata_atiixp
[    0.767911] scsi5 : pata_atiixp
[    0.768923] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    0.768925] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.111310] ata4: SATA link down (SStatus 0 SControl 300)
[    1.111338] ata3: SATA link down (SStatus 0 SControl 300)
[    1.291264] ata1: softreset failed (device not ready)
[    1.291267] ata1: applying SB600 PMP SRST workaround and retrying
[    1.291281] ata2: softreset failed (device not ready)
[    1.291284] ata2: applying SB600 PMP SRST workaround and retrying
[    1.471268] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.471291] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.472186] ata1.00: ATA-8: Hitachi HDT721064SLA360, STDOA31B, max UDMA/133
[    1.472188] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.473290] ata1.00: configured for UDMA/133
[    1.474123] ata2.00: ATAPI: HL-DT-ST DVDRAM GH40F, MG01, max UDMA/100
[    1.477967] ata2.00: configured for UDMA/100
[    1.661966] Write protecting the kernel read-only data: 7584k
[    2.875778] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    7.146580] EXT4-fs (sda7): mounted filesystem with ordered data mode


> **lidex said:**
> can you post the output of this command?
```
dmesg | grep ata
```

---

### Post by thoth3g on 2009-11-26
Just as an update....
It appears that the front cover on this gateway has a plastic shield with the buttons to open the drives etc. After removing the front plastic panel you gain access to the actual buttons for the hardware (instead of the extra layer of buttons) and obviously the player itself opens. 
As I went about looking the situation over I also tried a few other things out. Currently I have Slackware 13 installed and it's pretty nice. After manually installing the drivers for ATI it's looking pretty good. (lots to learn on this one, lol)

---

### Post by hazelnut on 2010-03-14
I had this same problem after upgrading from 32 bit karmic to 64 bit.  For hours, I could not mount a dvd or cd.  

sudo lshw -C disk would always show "status=nodisc" for my drive no matter what kind of disk I had in it.  I noticed others on the forums having trouble with it reporting "status=open".

Like I said, for HOURS I fought with this, trying to find a solution.  I rebooted/reset multiple times to no avail.

I finally, just on a whim, cut the power and turned the machine off.  I almost never do that.  When I restarted from power-up, go figure, my disk mounted.  

That was yesterday.  It still works today.

Cheers:popcorn:

---

### Post by thoth3g on 2010-03-15
> **hazelnut said:**
> I had this same problem after upgrading from 32 bit karmic to 64 bit.  For hours, I could not mount a dvd or cd.  

sudo lshw -C disk would always show "status=nodisc" for my drive no matter what kind of disk I had in it.  I noticed others on the forums having trouble with it reporting "status=open".

Like I said, for HOURS I fought with this, trying to find a solution.  I rebooted/reset multiple times to no avail.

I finally, just on a whim, cut the power and turned the machine off.  I almost never do that.  When I restarted from power-up, go figure, my disk mounted.  

That was yesterday.  It still works today.

Cheers:popcorn:


Actually I found on further investigation that there is a plastic panel that can be removed from the front side of the box on my computer. It had an extra set of buttons wired from the box. After removing this panel (which doesn't look too pretty) I exposed the actual buttons from the CD ROM drive itself. The hardware buttons from the drive will open and close but that extra layer of buttons are pretty useless in linux.
I still have ubuntu installed but until a distro can get the frame rates and such for gaming it will never replace windows.

---

### Post by brent_weaver on 2010-03-27
Guys I am having the same issue. I am unable to mount but I can write a cd/dvd. Here is some info:

```

*-cdrom                                             
       description: DVD-RAM writer                    
       product: DVDRAM GH40F                          
       vendor: HL-DT-ST                               
       physical id: 1                                 
       bus info: scsi@1:0.0.0                         
       logical name: /dev/cdrom                       
       logical name: /dev/cdrw                        
       logical name: /dev/dvd                         
       logical name: /dev/dvdrw                       
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: MG01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

root@kebin:/dev# lsmod                                           
Module                  Size  Used by                            
isofs                  36424  0                                  
udf                    88136  0                                  
crc_itu_t               2336  1 udf                              
usblp                  15136  0                                  
vmnet                  46684  7                                  
parport_pc             37352  0                                  
vmci                   56392  0                                  
vmmon                  76752  0                                  
binfmt_misc            10220  1                                  
ppdev                   8232  0                                  
snd_hda_codec_realtek   277860  1                                
snd_hda_intel          31880  6                                  
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec                      
snd_pcm_oss            44704  0                                    
snd_mixer_oss          18976  1 snd_pcm_oss                        
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0                                        
snd_seq_oss            33440  0                                        
snd_seq_midi            8192  0                                        
snd_rawmidi            27360  1 snd_seq_midi                           
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi               
snd_seq                60608  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq                                          
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  24 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3872  0
soundcore               9088  1 snd
lp                     11908  0
i2c_nforce2             8168  0
psmouse                57124  0
ip_tables              21200  1 iptable_filter
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
nvidia              10316904  36
serio_raw               6596  0
parport                40528  3 parport_pc,ppdev,lp
led_class               5256  0
joydev                 13088  0
x_tables               25832  1 ip_tables
usbhid                 43968  0
reiserfs              247720  4
fbcon                  41344  72
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
vesafb                  7176  1
usb_storage            66016  1
ohci1394               33780  0
ieee1394              100896  1 ohci1394
forcedeth              61292  0

root@kebin:/dev# dmesg
[168544.604517] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[168544.604526] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]          
[168544.604534] Info fld=0x0, ILI                                                
[168544.604537] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track        
[168544.604546] end_request: I/O error, dev sr0, sector 0                        
[168544.604553] __ratelimit: 8 callbacks suppressed                              
[168544.604558] Buffer I/O error on device sr0, logical block 0                  
[168544.604567] Buffer I/O error on device sr0, logical block 1                  
[168544.604572] Buffer I/O error on device sr0, logical block 2                  
[168544.604577] Buffer I/O error on device sr0, logical block 3                  
[168544.604582] Buffer I/O error on device sr0, logical block 4                  
[168544.604586] Buffer I/O error on device sr0, logical block 5
[168544.604591] Buffer I/O error on device sr0, logical block 6
[168544.604595] Buffer I/O error on device sr0, logical block 7
[168544.604600] Buffer I/O error on device sr0, logical block 8
[168544.604604] Buffer I/O error on device sr0, logical block 9
[168546.780821] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[168546.780831] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[168546.780839] Info fld=0x0, ILI
[168546.780840] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[168546.780860] end_request: I/O error, dev sr0, sector 0
[168546.852600] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[168546.852618] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[168546.852625] Info fld=0x0, ILI
[168546.852627] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[168546.852645] end_request: I/O error, dev sr0, sector 0
[168546.983896] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[168546.983901] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[168546.983905] Info fld=0x0, ILI
[168546.983907] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[168546.983915] end_request: I/O error, dev sr0, sector 0
[168563.753976] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[168563.753983] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current]
[168563.753988] Info fld=0x10, ILI
[168563.753989] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[168563.753998] end_request: I/O error, dev sr0, sector 64
[168563.754024] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

```

I am quite desperate to get this working as I have to boot into Vista to use my cdrom. This is the LAST thing i thought would be broken on an Ubuntu box. Help :D

---

