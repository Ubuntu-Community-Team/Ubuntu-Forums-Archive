---
title: "/dev/sdb, sdb1, sdb2, etc...  I'm stupid!"
date: 2009-06-17
forum: General Help
---

### Post by Philsco on 2009-06-17
This may be a simple fix *fingers crossed*, but it was a complicated mess up X_x
      
      It all started about half a year ago when I bought a 1 TB External USB SATA HDD.  I bought an IDE to SATA conversion power cable (to hook it into this ancient beast of a machine, Dell Dimension 8250), plugged in the USB cable, and partitioned it into 4 sections: 124 GB main file partition, two three-hundred something GB storage partitions, and a 214 (244?) GB back-up partition.  It worked great, but Ubuntu supplied them all with random target locations upon each reboot/remount.  /media/disk, /media/disk-2, /media/disk-3, /media/disk-4, each were granted to the partitions randomly.  Well, whatever, it was just an annoyance, but I had a nice shiny new Terabyte of data storage!  Great!  For four long glorious months, that sufficed.
      
      However, a couple months ago, I got a little annoyed at having to redirect my programs depending on directory locations (music player, Flash projects, BG Images,etc).  So, I go in, and name their mount points.  Of course, I made the newbie error of using "/media/disk," instead of just "disk."  That caused my drives to be inaccessible for the next two months, as I had no internet access to trouble-shoot with.
     
    Now, earlier today, my wife and I reconnected our internet, so the first thing I did was jump on to try and fix this little issue.  Well, happening across the information in all the wrong orders, I first get my hands on a tutorial telling me to use "sudo pysdm" to correctly label partitions and such.  I didn't realize this didn't quite pertain to my situation, so I go ahead and sudo apt-get install it, and run it.  It shows my sdb drives (the Terabyte partitions), and I go and click on them in order, each auto-configuring as I do so.  I then rename them to what I want them to mount as, save, mount, and I think I'm done!
    
    Well, a restart later shows me how horribly wrong I was...  Now, there are four new mounted drives that I can't access (the four I just named) in my /media/ folder, the four original drives (124 GB, etc, etc, etc,) which are shown as "Cannot contain ...etc...," and four NEW drives that the USB SATA drive is trying to load as...  F*ck me...
    
This time, I come across the information telling me to use "gconf -editor," go to System --> Media, and kill the Key values for the drives that I had written in.  Okay!  Done.  Now, however, I have 12 other annoying drives in my /media/ folder, and my SATA drive is randomly unmounting and remounting itself.  This is really annoying, as it makes movies hard to watch, music hard to listen to, and causes corrupted saves for projects I'm working on.  I (for some unknown reason, mainly due to ignorance) assume that this is because of the sdb files.  From what the "dmesg" stated, I gathered that the sdb file had become corrupted or cluttered or something (not realizing what it was, at the time).  So, I went to my terminal, typed in "sudo nautilus," went to /dev/, and deleted sdb, sdb-2, sdb-3, sdb-4 (5?), and restarted my computer...  Damn.

No good, obviously, came of this.  Now, my drive won't mount at all.

Well, with all my steps explained, let me give you some readouts.

```
~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14406   115716163+  83  Linux
/dev/sda2           14407       14593     1502077+   5  Extended
/dev/sda5           14407       14593     1502046   82  Linux swap / Solaris
``````
[ 3136.444494] scsi96 : SCSI emulation for USB Mass Storage devices
[ 3136.446178] usb-storage: device found at 100
[ 3136.446182] usb-storage: waiting for device to settle before scanning
[ 3138.301648] usb 2-4: USB disconnect, address 100
[ 3138.572019] usb 2-4: new high speed USB device using ehci_hcd and address 101
[ 3138.628319] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3138.868018] usb 2-4: new high speed USB device using ehci_hcd and address 102
[ 3139.004096] usb 2-4: configuration #1 chosen from 1 choice
[ 3139.058961] scsi97 : SCSI emulation for USB Mass Storage devices
[ 3139.060710] usb-storage: device found at 102
[ 3139.060714] usb-storage: waiting for device to settle before scanning
[ 3144.060173] usb-storage: device scan complete
[ 3144.063660] scsi 97:0:0:0: Direct-Access     WDC WD10 EACS-00D6B1           PQ: 0 ANSI: 2
[ 3144.101935] sd 97:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[ 3144.121669] sd 97:0:0:0: [sdb] Write Protect is off
[ 3144.121674] sd 97:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 3144.121677] sd 97:0:0:0: [sdb] Assuming drive cache: write through
[ 3144.122667] sd 97:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[ 3144.125322] sd 97:0:0:0: [sdb] Write Protect is off
[ 3144.125327] sd 97:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 3144.125330] sd 97:0:0:0: [sdb] Assuming drive cache: write through
[ 3144.125337]  sdb:<6>usb 2-4: USB disconnect, address 102
[ 3144.219704] sd 97:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.219711] end_request: I/O error, dev sdb, sector 0
[ 3144.219715] __ratelimit: 5 callbacks suppressed
[ 3144.219719] Buffer I/O error on device sdb, logical block 0
[ 3144.219783] sd 97:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.219788] end_request: I/O error, dev sdb, sector 0
[ 3144.219790] Buffer I/O error on device sdb, logical block 0
[ 3144.219840] sd 97:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.219844] end_request: I/O error, dev sdb, sector 0
[ 3144.219846] Buffer I/O error on device sdb, logical block 0
[ 3144.219889] sd 97:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.219893] end_request: I/O error, dev sdb, sector 0
[ 3144.219896] Buffer I/O error on device sdb, logical block 0
[ 3144.223276] sd 97:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.223283] end_request: I/O error, dev sdb, sector 0
[ 3144.223288] Buffer I/O error on device sdb, logical block 0
[ 3144.223303] ldm_validate_partition_table(): Disk read failed.
[ 3144.223316] sd 97:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.223320] end_request: I/O error, dev sdb, sector 0
[ 3144.223323] Buffer I/O error on device sdb, logical block 0
[ 3144.223340] sd 97:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.223344] end_request: I/O error, dev sdb, sector 0
[ 3144.223346] Buffer I/O error on device sdb, logical block 0
[ 3144.223364] sd 97:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.223368] end_request: I/O error, dev sdb, sector 0
[ 3144.223370] Buffer I/O error on device sdb, logical block 0
[ 3144.223387] sd 97:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.223391] end_request: I/O error, dev sdb, sector 0
[ 3144.223394] Buffer I/O error on device sdb, logical block 0
[ 3144.223402] Dev sdb: unable to read RDB block 0
[ 3144.223413] sd 97:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.223418] end_request: I/O error, dev sdb, sector 0
[ 3144.223420] Buffer I/O error on device sdb, logical block 0
[ 3144.223437] sd 97:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.223441] end_request: I/O error, dev sdb, sector 0
[ 3144.223469] sd 97:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.223473] end_request: I/O error, dev sdb, sector 24
[ 3144.223489] sd 97:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.223493] end_request: I/O error, dev sdb, sector 24
[ 3144.223511] sd 97:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.223515] end_request: I/O error, dev sdb, sector 0
[ 3144.223532] sd 97:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3144.223536] end_request: I/O error, dev sdb, sector 0
[ 3144.223543]  unable to read partition table
[ 3144.223651] sd 97:0:0:0: [sdb] Attached SCSI disk
[ 3144.223724] sd 97:0:0:0: Attached scsi generic sg2 type 0
[ 3144.472026] usb 2-4: new high speed USB device using ehci_hcd and address 103
[ 3144.528346] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3144.768025] usb 2-4: new high speed USB device using ehci_hcd and address 104
[ 3144.824393] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3145.064027] usb 2-4: new high speed USB device using ehci_hcd and address 105
[ 3145.748268] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3145.988018] usb 2-4: new high speed USB device using ehci_hcd and address 106
[ 3146.044327] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3146.228356] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3146.412250] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3146.596280] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3146.836032] usb 2-4: new high speed USB device using ehci_hcd and address 110
[ 3146.892325] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3147.135055] usb 2-4: new high speed USB device using ehci_hcd and address 111
[ 3147.188252] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3147.428018] usb 2-4: new high speed USB device using ehci_hcd and address 112
[ 3147.484297] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3147.724017] usb 2-4: new high speed USB device using ehci_hcd and address 113
[ 3147.780342] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3148.020017] usb 2-4: new high speed USB device using ehci_hcd and address 114
[ 3148.076261] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3148.316017] usb 2-4: new high speed USB device using ehci_hcd and address 115
[ 3148.372308] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3148.612018] usb 2-4: new high speed USB device using ehci_hcd and address 116
[ 3148.668352] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3148.852379] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3149.092025] usb 2-4: new high speed USB device using ehci_hcd and address 118
[ 3149.148299] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3149.388026] usb 2-4: new high speed USB device using ehci_hcd and address 119
[ 3149.444347] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3149.684027] usb 2-4: new high speed USB device using ehci_hcd and address 120
[ 3149.740263] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3149.980027] usb 2-4: new high speed USB device using ehci_hcd and address 121
[ 3150.064301] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3150.304018] usb 2-4: new high speed USB device using ehci_hcd and address 122
[ 3150.460362] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3150.700036] usb 2-4: new high speed USB device using ehci_hcd and address 123
[ 3154.516355] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3154.756017] usb 2-4: new high speed USB device using ehci_hcd and address 124
[ 3155.364361] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3155.604032] usb 2-4: new high speed USB device using ehci_hcd and address 125
[ 3155.767267] usb 2-4: configuration #1 chosen from 1 choice
[ 3155.797378] scsi98 : SCSI emulation for USB Mass Storage devices
[ 3155.799150] usb-storage: device found at 125
[ 3155.799155] usb-storage: waiting for device to settle before scanning
[ 3160.796233] usb-storage: device scan complete
[ 3160.799842] scsi 98:0:0:0: Direct-Access     WDC WD10 EACS-00D6B1           PQ: 0 ANSI: 2
[ 3160.844232] sd 98:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[ 3160.846592] sd 98:0:0:0: [sdb] Write Protect is off
[ 3160.846597] sd 98:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 3160.846600] sd 98:0:0:0: [sdb] Assuming drive cache: write through
[ 3160.847589] sd 98:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[ 3160.849977] sd 98:0:0:0: [sdb] Write Protect is off
[ 3160.849982] sd 98:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 3160.849985] sd 98:0:0:0: [sdb] Assuming drive cache: write through
[ 3160.849993]  sdb: sdb1 sdb2 sdb3 sdb4
[ 3160.858854] sd 98:0:0:0: [sdb] Attached SCSI disk
[ 3160.858941] sd 98:0:0:0: Attached scsi generic sg2 type 0
[ 3160.862294] usb 2-4: USB disconnect, address 125
[ 3161.104033] usb 2-4: new high speed USB device using ehci_hcd and address 126
[ 3161.164367] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 3161.404031] usb 2-4: new high speed USB device using ehci_hcd and address 127
[ 3166.536196] usb 2-4: unable to read config index 0 descriptor/start: -110
[ 3166.536201] usb 2-4: chopping to 0 config(s)
[ 3166.566336] usb 2-4: no configuration chosen from 0 choices

```That includes a few times of disconnecting and reconnecting the USB SATA drive.

```
~$ sudo mount /dev/sdb
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab

``````
~$ lsusb
Bus 002 Device 127: ID 04fc:0c15 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``````
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                   proc         defaults                    0  0  
# /dev/sda1
UUID=5a607001-a9ea-4384-b49f-12b04181535b  /                       ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=f4d3427f-4daa-4f81-a5fe-5463d2638b3e  none                    swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0           udf,iso9660  user,noauto,exec,utf8       0  0  
```And that's my fstab

Anything else I can post that would help, I'd be glad to!  Sorry if I gave too much info to sift through, though.  This's my first post I've done on these forums.

I'm not a complete newbie, but I am fairly new to Linux functionality.  I've been using it since November 2008, but when you're making an almost 7 year-old frankensteined machine compatible with things like WoW, Flash, an inserted SATA drive, a G-Pen tablet (not installed at the moment), and other things, you pick up how to run around an operating system pretty quickly.

---

### Post by x22 on 2009-06-17
> sudo mount /dev/sdb

2 problems with this. One: you need to specify on what
directory you wish to mount a partition; and Two
/dev/sdb is the whole drive, but what you want to mount
are the partitions: according to your posting, you have
four partitions sdb1 sdb2 sdb3 sdb4 on that drive: so
if you have directories /1 /2 /3 /4 say, you could do
this

sudo mount /dev/sdb1 /1
sudo mount /dev/sdb2 /2
sudo mount /dev/sdb3 /3
sudo mount /dev/sdb4 /4

to automate, expand yr fstab thus

/dev/sdb1 /1 ext3   defaults 0 0
/dev/sdb2 /2 ext3   defaults 0 0
/dev/sdb3 /3 ext3   defaults 0 0
/dev/sdb4 /4 ext3   defaults 0 0

---

### Post by Philsco on 2009-06-17
Thanks for the response.

Okay, so fstab now reads:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                   proc         defaults                    0  0  
# /dev/sda1
UUID=5a607001-a9ea-4384-b49f-12b04181535b  /                       ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=f4d3427f-4daa-4f81-a5fe-5463d2638b3e  none                    swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0           udf,iso9660  user,noauto,exec,utf8       0  0  
# Following I added in (Phil)
/dev/sdb1                                  /media/1                      ext3         defaults                    0  0
/dev/sdb2                                  /media/2                      ext3         defaults                    0  0
/dev/sdb3                                  /media/3                      ext3         defaults                    0  0
/dev/sdb4                                  /media/4                      ext3         defaults                    0  0
```

I used sudo mkdir /media/1...2...3...4 to make the directories.  So, in /media, the directories noted in fstab do exist.  However, now...

```
~$ sudo mount /dev/sdb1 /media/1
mount: special device /dev/sdb1 does not exist

```

That's the newest issue!  Thanks for the help.

---

### Post by redmk2 on 2009-06-17
Philsco,

To insure the partitions mount correctly use the UUID of eash partition instead of the /dev/sdb*x*.  Look at the entries for sda1 and sda5 in your fstab.

To find the UUID for all your partitions try this:```
sudo blkid
```  For a complete explanation see [[COLOR="DimGray"]_**https://help.ubuntu.com/community/UsingUUID**_[/COLOR]]("https://help.ubuntu.com/community/UsingUUID")

---

### Post by Philsco on 2009-06-18
Hey redmk2 and x22, thank you both so much for your time.  This got solved.

Here's what happened:

Thanks to x22, I quit screwing around with /dev/sdb and realized that, yes, I was working with individual partitions seen as drives.  So, I did as he said, and got that new error.  Then, going through my "dmesg" output, I realized that at some point I had plugged into a USB 1.0 hub.  X_x  Okay, I don't think that should have had the backlash that it did, but, well...  it did.  That's when I responded here.

 So, plugging it into the adjacent USB 2.0 port, I ran dmesg again, saw it was a MUCH nicer looking output with far less "this computer is confused" looking messages, and hit up

sudo mount /dev/sdb1 /media/1
This time, the outcome was much nicer.  After mounting all of the partitions (1-4), I came back here.  Redmk2, thanks for that article.  I reassigned them to UUIDs in my fstab, and I'll see how those run.

Now, would you recommend using
```
$ sudo chown phil:phil /media/1
$ sudo chown phil:phil /media/2
$ sudo chown phil:phil /media/3
$ sudo chown phil:phil /media/4
```
or
```
$ sudo pysdm
```
to make the directories writable?

---

### Post by redmk2 on 2009-06-18
> Now, would you recommend using...

I'm old school (because I'm old).  I don't even think about using others GUI interfaces.  I use chown and chmod.  I check the ownership and permissions on the spot.  If it is not right,  (nobody's perfect) I just use the up arrow key and modifiy the command.

---

### Post by merlinus on 2009-06-18
You may wish to add -R to the chown command so it is recursive.

And iirc you can do them all with one command.

---

### Post by Philsco on 2009-06-18
Okay, I'll take that route!  And, I agree.  See, I prefer to see what's happening and "going through the computer's mind," so to speak.

The one command thing would be nifty to know, if you can happen to remember it.  I don't mind repetition (I do a LOT of Flash "programming," and in that environment, there's a LOT of repetition), but it'd be nice to have it in my arsenal, jic

---

### Post by merlinus on 2009-06-18
Simply combine them:

```

sudo chown -R phil:phil /media/1 /media/2

```

etc.

---

### Post by Philsco on 2009-06-18
Ah, thanks man.

Again, you guys rock.  I have been using this forum as my primary source of trouble-shooting for a long time before I registered today, and the speed and ability with which my help request was met is astounding.  :D

---

### Post by merlinus on 2009-06-18
Welcome aboard, and happy ubuntuing!

---

