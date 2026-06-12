---
title: "ubuntu doesnt detect new 1TB harddrive on existing system"
date: 2010-12-17
forum: Desktop Environments
---

### Post by Foeburner on 2010-12-17
I already have ubuntu running on a RAID 0 configuration. I installed an extra 1TB harddrive so that I can expand the file server but it's not detecting it at all. gparted doesnt see it, disk management either.

I ran this cmd:
```
sudo lshw -C disk
```

and this populates

```
*-cdrom                 
       description: SCSI CD-ROM
       product: CD-ROM LTN-4891S
       vendor: LITE-ON
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: NDS3
       capabilities: removable audio
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: ATA Disk
       product: WDC WD3200AAKS-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WMAV23811523
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0007604c
  *-disk:1
       description: ATA Disk
       product: WDC WD3200AAKS-0
       vendor: Western Digital
       physical id: 0.1.0
       bus info: scsi@2:0.1.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WMAV23752105
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0004ecda
  *-disk
       description: SCSI Disk
       vendor: FV-U35
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: 1.04
       serial: WD-WMAT10464853
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=c1b980b2

```

I connect the sata cable to a different slot on the motherboard and checked if the harddrive was getting any power. Everything seems to be fine. 

any help is greatly appreciated.

---

### Post by Migrus on 2010-12-17
I would reboot and check if the disk appears in the bios.

On an old motherboard I had, only some sata ports were enabled depending on sata settings. Can't recall what setting that was but probably something with mode (ide legacy or ahci). When changing that setting it also moved disks around so you may want to have a rescue CD ready if you try that, just in case it no longer finds the drive to boot from.

---

### Post by CharlesA on 2010-12-17
+1 to make sure it's seen in the BIOS.

Also check for loose cables and whatnot.

---

### Post by 741Baus on 2010-12-17
Hi Foeburner, +2 on the bios,is it picking up the detection of your new drive ?.
 I had this problem when I installed a new sata hard drive and the bios wasn't detecting the drive ,I scratched my head for ages trying to get it detected ,then my brother in law suggested that I unplug all the drives except the drive I was trying to detect restarted and checked the bios again to see if it was detected it was,replugged the other drives back in and up and running , you may want to try this even though it was a dirty solution it worked for me. 
                             cheers 741Baus

---

### Post by Foeburner on 2010-12-17
i may have crapped it. Went to bios. You guys were right. Although it couldnt ID the harddrive, any other sata connection was disabled so I reenabled all of them (there were 1 more sata and 2 pata) and now the startup goes purple where the bios should be and fades to the corner and stays black. Wont load anything. I disconnected all hard drives to see if it detects no OS and still does the same thing.

---

### Post by Foeburner on 2010-12-17
I just unplugged the power and removed the cmos battery hoping it would reset the bios and still nothing. Anyone know how to reset the bios? I have a Dell PowerEdge SC430

---

### Post by CharlesA on 2010-12-17
Reset the BIOS to default - there is probably a jumper to do that, but if not, remove the battery and then put it back in after a few minutes.

---

### Post by Foeburner on 2010-12-17
I tried removing the battery for a longer time. That didnt work. I removed the battery completely and started the pc up and even without it, it just boots to a fading purple screen. i may have just bricked it...  =*(

---

### Post by CharlesA on 2010-12-17
What do you mean a fading purple screen? Try this:

Reseat ALL cables - power, video, mouse, keyboard, drive cables, etc.

Then boot it up.

---

### Post by Foeburner on 2010-12-17
i disconnected all cables except for the vga and power (of course) powered on and only get that purple screen. Let me describe it. It's light purple (not solid color, has a brighter area like light is hitting it) and has darker purple dots uniformly fixed on the image. looks like a nice background image. It then fades from light to dark towards the lower right corner of the screen while the upper left corner goes black, then everything goes black and stays that way.

---

### Post by Foeburner on 2010-12-17
ok i was able to fix my issue. Did a procedure with Dell that defaulted everything.

Then I went to the bios and enabled SATA1 where the 1TB hard drive is connected and rebooted. The system sees the drive and is now asking me to format it. Wat is the best format for it? Its asking for Master boot record, GUID partition Table, Dont partition or Apple partition. MBR reads as compatible with any system but has limitations in disk size. Will this affect my 1TB harddrive?

---

### Post by CharlesA on 2010-12-17
You can create it as a MBR partition because it's less then 2TB in size.

Glad you got it working.

---

### Post by 741Baus on 2010-12-18
Foeburner , glad to here you've solved your problem .

---

### Post by Foeburner on 2010-12-20
Awesome! Thank you everyone!! I really appreciated all the help!

---

