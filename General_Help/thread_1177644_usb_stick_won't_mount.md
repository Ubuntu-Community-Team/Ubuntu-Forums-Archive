---
title: "usb stick won't mount"
date: 2009-06-03
forum: General Help
---

### Post by Th3Professor on 2009-06-03
I plug a USB stick into the computer and it doesn't mount.

I've tried checking /media, used various commands, lspci, dmesg, fdisk, etc., but not really sure how to get it to mount.

It's not sda1, that's a hard drive, and yet howto pages online say to mount that. Of course it'll be different on different computers, yet I'd think it'd be possible to at least find out which /dev I can use to mount it under.

Any ideas?

Thanks!

---

### Post by Yellow Pasque on 2009-06-03
Unplug your USB stick and use:
```
sudo fdisk -l
```
Now plug in the stick and use the command again. What changed in the output between the 2 commands?

---

### Post by Th3Professor on 2009-06-03
> **Temüjin said:**
> Unplug your USB stick and use:
```
sudo fdisk -l
```Now plug in the stick and use the command again. What changed in the output between the 2 commands?

I unplugged the USB stick and here's the list:
```

/dev/sda1               1         122      979933+  83  Linux
/dev/sda2   *         123       24437   195310237+   7  HPFS/NTFS
/dev/sda3           24438       26261    14651280   be  Solaris boot
/dev/sda4           26262       60801   277442550    5  Extended
/dev/sda5           26262       28693    19535008+  83  Linux
/dev/sda6           28694       57263   229488493+  83  Linux
/dev/sda7           57264       57506     1951866   82  Linux swap / Solaris
/dev/sda8           57507       57749     1951866   82  Linux swap / Solaris
/dev/sda9           57750       57992     1951866   bf  Solaris
/dev/sda10          57993       60801    22563261   83  Linux
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

```

I plugged the USB stick back in and here's the list:
```

/dev/sda1               1         122      979933+  83  Linux
/dev/sda2   *         123       24437   195310237+   7  HPFS/NTFS
/dev/sda3           24438       26261    14651280   be  Solaris boot
/dev/sda4           26262       60801   277442550    5  Extended
/dev/sda5           26262       28693    19535008+  83  Linux
/dev/sda6           28694       57263   229488493+  83  Linux
/dev/sda7           57264       57506     1951866   82  Linux swap / Solaris
/dev/sda8           57507       57749     1951866   82  Linux swap / Solaris
/dev/sda9           57750       57992     1951866   bf  Solaris
/dev/sda10          57993       60801    22563261   83  Linux
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

```

(No change.)

`mount' doesn't show anything.
`dmesg' (the last few lines) shows the following, I've removed lines that repeated:
```

[ 1069.864018] usb 3-5: new high speed USB device using ehci_hcd and address 23
[ 1072.199705] usb 3-5: configuration #1 chosen from 1 choice
[ 1072.200257] scsi30 : SCSI emulation for USB Mass Storage devices
[ 1072.200365] usb-storage: device found at 23
[ 1072.200369] usb-storage: waiting for device to settle before scanning
[ 1076.692013] usb 1-4: new full speed USB device using ohci_hcd and address 6
[ 1076.872012] usb 1-4: device descriptor read/64, error -62
[ 1077.200182] usb-storage: device scan complete
[ 1077.201775] scsi 30:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[ 1077.213199] sd 30:0:0:3: [sdh] Attached SCSI removable disk
[ 1077.213297] sd 30:0:0:3: Attached scsi generic sg8 type 0
[ 1077.437512] usb 1-4: new full speed USB device using ohci_hcd and address 7
[ 1077.845509] usb 1-4: device not accepting address 7, error -62
[ 1077.957514] usb 3-5: reset high speed USB device using ehci_hcd and address 23
[ 1078.672036] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 1088.616097] usb 3-5: reset high speed USB device using ehci_hcd and address 23
[ 1125.864023] usb 1-4: new full speed USB device using ohci_hcd and address 10
[ 1126.044021] usb 1-4: device descriptor read/64, error -62
[ 1126.613050] usb 1-4: new full speed USB device using ohci_hcd and address 11
[ 1127.020821] usb 1-4: device not accepting address 11, error -62
[ 1127.605544] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 1127.717523] usb 3-5: reset high speed USB device using ehci_hcd and address 23

```
...other addresses, sg#s, etc. were listed also... perhaps this will give an idea on what's going on.

---

### Post by Th3Professor on 2009-06-05
vump

---

### Post by Th3Professor on 2009-06-08
> **Th3Professor said:**
> vump
bump
...still cannot mount the usb flash stick device. any ideas?

---

### Post by Mark76 on 2009-06-08
I'm having the same problem. The usb stick I have mounts fine in Windows XP but not at all in Ubuntu.

---

### Post by nuclearj on 2009-06-08
ditto, my flash drive will not mount when plugged in either.  And this was after a Hardy system update.  So any clues?  This board used to be hopping with answers before...

---

### Post by izizzle on 2009-06-08
I think I may have the solution. If you have access to Windows, plug your device into the Windows computer and let it mount. Then, before unplugging it, "Safely Remove" the device by right clicking it and and hitting safely remove. Now, plug it back into Ubuntu and hopefully it will mount.

---

### Post by nuclearj on 2009-06-08
I'll try it, BRB


I got nothing, but thanks for the suggestion!

---

### Post by reeseslover531 on 2009-06-08
Have you tried a different USB port?

---

### Post by Mark76 on 2009-06-08
Yes.

All of them

---

### Post by nuclearj on 2009-06-08
yup!

---

### Post by Th3Professor on 2009-06-08
Yes, I have tried all of them also.
...I'm surprised there isn't a how-to on this, or if someone finds one (and it works) can they link it in this thread?

---

### Post by nuclearj on 2009-06-08
this is old but see if we can't glean something from it.

[HTML]http://ubuntuforums.org/showthread.php?t=582045[/HTML]

---

### Post by reeseslover531 on 2009-06-08
hmmmm not sure but try removing ehci_hcd module. I have heard of that module messing things up. To do this type 
```
sudo rmmod ehci_hcd
```
and then unplug and plug the usb stick back in. Are all you guys getting the exact same error?

---

### Post by Mark76 on 2009-06-08
I don't even have that module.

---

### Post by nuclearj on 2009-06-08
> **reeseslover531 said:**
> hmmmm not sure but try removing ehci_hcd module. I have heard of that module messing things up. To do this type 
```
sudo rmmod ehci_hcd
```
and then unplug and plug the usb stick back in. Are all you guys getting the exact same error?

I tried that but it did nothing, i guess the solution is to upgrade to the next distro?

---

### Post by reeseslover531 on 2009-06-09
i dunno, have you tried booting a liveCD of 9.04 and trying the usb stick to see if it works?

---

### Post by nuclearj on 2009-06-09
Okay so I upgraded to Intrepid.  Still nothing with my USB or even my DVD drive.  What to do now?

Well, I backed up all my files (luckily I have two HDs installed) and I am about ready to erase everything and go back to Gutsy.  I did the update thinking it would be cool to do.  Let this be a lesson, if it ain't broke don't fix it!

So any ideas in the next hour while I use my sister's computer to download Gutsy and burn the live cd?

---

### Post by AlanInVancouverBC on 2009-06-09
I can't save my son's homework on his flashdrive. Because 9.04 doesn't recognize any usb port I have. And I find so many others with similar, flashdrive problems. This appears to be a stunning, stunning issue. Certainly someone must have an answer. It's got to be something basic. Why would this be possible? It appears to be so simple an issue.

So I have to email my son's file to myself and open Windows XP to save it to the flash drive, because Windows recognizes my flashdrives!

---

### Post by Linksy on 2009-06-09
I have the same problem.

---

### Post by Yellow Pasque on 2009-06-10
You folks might want to compare notes on your hardware setups (especially what mobo chipset and/or southbridge you're using).

---

### Post by Linksy on 2009-06-10
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris


____________________________________________________________________________
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 1000 MB, 1000341504 bytes
16 heads, 32 sectors/track, 3816 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xf50af50a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3816      976880    e  W95 FAT16 (LBA)


I see there is a difference, and yes that difference is one of my drives, so what do I do from here?

---

### Post by Yellow Pasque on 2009-06-10
It really should automount, but if it doesn't
```
sudo mount /dev/sdb1 <place where you want to mount it>
```

---

### Post by Linksy on 2009-06-10
> **Temüjin said:**
> It really should automount, but if it doesn't
```
sudo mount /dev/sdb1 <place where you want to mount it>
```


And where would I want to mount it? New with ubuntu/linux.

---

### Post by Chronon on 2009-06-10
You could create a directory in /media/ or /mnt/:
```
mkdir /media/usbstick
```

Then do:
```
sudo mount /dev/sdb1 /media/usbstick
```

Then you will find the contents of your device at /media/usbstick.

---

### Post by Mark76 on 2009-06-10
Tried that and got an unknown device error

Someone at Ubuntu or Debian broked the usb stick detector thingy :(

---

### Post by ubfu on 2009-06-10
> **AlanInVancouverBC said:**
> I can't save my son's homework on his flashdrive. Because 9.04 doesn't recognize any usb port I have. And I find so many others with similar, flashdrive problems. This appears to be a stunning, stunning issue. Certainly someone must have an answer. It's got to be something basic. Why would this be possible? It appears to be so simple an issue.

So I have to email my son's file to myself and open Windows XP to save it to the flash drive, because Windows recognizes my flashdrives!

I am having the same issue as you guys 
[http://ubuntuforums.org/showthread.php?t=1181065](http://ubuntuforums.org/showthread.php?t=1181065)
It's an external hard disk.If you try to boot with 8.04 , it's totally fine while 9.04 gives a lot of problem

---

### Post by bronxbomberz41 on 2009-06-10
> **Chronon said:**
> You could create a directory in /media/ or /mnt/:
```
mkdir /media/usbstick
```

Then do:
```
sudo mount /dev/sdb1 /media/usbstick
```

Then you will find the contents of your device at /media/usbstick.



I'm having this issue too but with only one of my USB sticks.  I have a 4gb Cruzer and a 2gb Cruzer.  The 4g one works fine (i've  been using it to load videos to my xbox and watch them on my tv) but the 2g one isn't working.  I tried making a UNR bootable USB from it but it failed so I formatted it to blank it out and now it doesn't work.:(

I tried this but the mount command doesn't even recognize that the 2g one is even plugged in.

---

### Post by Yellow Pasque on 2009-06-10
> **Mark76 said:**
> Tried that and got an unknown device error

The commands were specific to Linksy's post. If your USB partition isn't  /dev/sdb1, then it's not going to work.

---

### Post by Mark76 on 2009-06-10
I tried to mount the drive (sdf) and got this

mount: can't find /dev/sdf in /etc/fstab or /etc/mtab

I've looked at fstab and can't quite work out what to add.

---

### Post by Yellow Pasque on 2009-06-10
Mount the partition, e.g. sdf1 , not sdf

---

### Post by Mark76 on 2009-06-10
That gives exactly the same outcome.

---

### Post by NiksaVel on 2009-06-19
I have the same problem with 3 of my usb sticks right now...  using jaunty.

All of them worked before on other computers, as well as this one, but now all I get is:

```
[67202.296255] hub 1-0:1.0: unable to enumerate USB device on port 3
[67202.580038] usb 1-3: new high speed USB device using ehci_hcd and address 2
[67202.636257] hub 1-0:1.0: unable to enumerate USB device on port 3
[67202.920031] usb 1-3: new high speed USB device using ehci_hcd and address 3
[67202.976256] hub 1-0:1.0: unable to enumerate USB device on port 3
[67203.260033] usb 1-3: new high speed USB device using ehci_hcd and address 4
[67203.316255] hub 1-0:1.0: unable to enumerate USB device on port 3
[67203.600035] usb 1-3: new high speed USB device using ehci_hcd and address 5
[67203.656258] hub 1-0:1.0: unable to enumerate USB device on port 3
[67203.940031] usb 1-3: new high speed USB device using ehci_hcd and address 6
[67203.996258] hub 1-0:1.0: unable to enumerate USB device on port 3
[67204.280036] usb 1-3: new high speed USB device using ehci_hcd and address 7
[67204.336256] hub 1-0:1.0: unable to enumerate USB device on port 3
[67204.620031] usb 1-3: new high speed USB device using ehci_hcd and address 8
[67204.676256] hub 1-0:1.0: unable to enumerate USB device on port 3
[67204.960029] usb 1-3: new high speed USB device using ehci_hcd and address 9
[67205.016256] hub 1-0:1.0: unable to enumerate USB device on port 3
[67205.300036] usb 1-3: new high speed USB device using ehci_hcd and address 10
[67205.356264] hub 1-0:1.0: unable to enumerate USB device on port 3
[67205.640035] usb 1-3: new high speed USB device using ehci_hcd and address 11
[67205.696357] hub 1-0:1.0: unable to enumerate USB device on port 3
[67205.980034] usb 1-3: new high speed USB device using ehci_hcd and address 12
[67206.036257] hub 1-0:1.0: unable to enumerate USB device on port 3
[67206.320038] usb 1-3: new high speed USB device using ehci_hcd and address 13
[67206.376259] hub 1-0:1.0: unable to enumerate USB device on port 3
[67206.660035] usb 1-3: new high speed USB device using ehci_hcd and address 14
[67206.716258] hub 1-0:1.0: unable to enumerate USB device on port 3
[67207.000039] usb 1-3: new high speed USB device using ehci_hcd and address 15
[67207.056257] hub 1-0:1.0: unable to enumerate USB device on port 3
[67207.340035] usb 1-3: new high speed USB device using ehci_hcd and address 16
[67207.396257] hub 1-0:1.0: unable to enumerate USB device on port 3
[67207.680036] usb 1-3: new high speed USB device using ehci_hcd and address 17
[67207.736260] hub 1-0:1.0: unable to enumerate USB device on port 3
[67208.020036] usb 1-3: new high speed USB device using ehci_hcd and address 18
[67208.076259] hub 1-0:1.0: unable to enumerate USB device on port 3
[67208.360039] usb 1-3: new high speed USB device using ehci_hcd and address 19
[67208.416258] hub 1-0:1.0: unable to enumerate USB device on port 3
[67208.700029] usb 1-3: new high speed USB device using ehci_hcd and address 20
[67208.756263] hub 1-0:1.0: unable to enumerate USB device on port 3
[67209.040034] usb 1-3: new high speed USB device using ehci_hcd and address 21
[67209.096309] hub 1-0:1.0: unable to enumerate USB device on port 3
[67209.380040] usb 1-3: new high speed USB device using ehci_hcd and address 22
[67209.436259] hub 1-0:1.0: unable to enumerate USB device on port 3
[67209.720034] usb 1-3: new high speed USB device using ehci_hcd and address 23
[67209.776259] hub 1-0:1.0: unable to enumerate USB device on port 3
[67210.060041] usb 1-3: new high speed USB device using ehci_hcd and address 24
[67210.116260] hub 1-0:1.0: unable to enumerate USB device on port 3
[67210.400038] usb 1-3: new high speed USB device using ehci_hcd and address 25
[67210.456310] hub 1-0:1.0: unable to enumerate USB device on port 3
[67210.740085] usb 1-3: new high speed USB device using ehci_hcd and address 26
[67210.800268] hub 1-0:1.0: unable to enumerate USB device on port 3
[67211.084028] usb 1-3: new high speed USB device using ehci_hcd and address 27
[67211.140260] hub 1-0:1.0: unable to enumerate USB device on port 3
[67211.424040] usb 1-3: new high speed USB device using ehci_hcd and address 28
[67211.480259] hub 1-0:1.0: unable to enumerate USB device on port 3
[67211.764035] usb 1-3: new high speed USB device using ehci_hcd and address 29
[67211.820259] hub 1-0:1.0: unable to enumerate USB device on port 3
[67212.104033] usb 1-3: new high speed USB device using ehci_hcd and address 30
[67212.160259] hub 1-0:1.0: unable to enumerate USB device on port 3
[67212.444035] usb 1-3: new high speed USB device using ehci_hcd and address 31
[67212.500259] hub 1-0:1.0: unable to enumerate USB device on port 3
[67212.784035] usb 1-3: new high speed USB device using ehci_hcd and address 32
[67212.840260] hub 1-0:1.0: unable to enumerate USB device on port 3
[67213.124036] usb 1-3: new high speed USB device using ehci_hcd and address 33
[67213.180260] hub 1-0:1.0: unable to enumerate USB device on port 3
[67213.464032] usb 1-3: new high speed USB device using ehci_hcd and address 34
[67213.520259] hub 1-0:1.0: unable to enumerate USB device on port 3
[67213.804037] usb 1-3: new high speed USB device using ehci_hcd and address 35
[67213.860261] hub 1-0:1.0: unable to enumerate USB device on port 3
[67214.144038] usb 1-3: new high speed USB device using ehci_hcd and address 36
[67214.200263] hub 1-0:1.0: unable to enumerate USB device on port 3
[67214.484033] usb 1-3: new high speed USB device using ehci_hcd and address 37
[67214.540261] hub 1-0:1.0: unable to enumerate USB device on port 3
[67214.824029] usb 1-3: new high speed USB device using ehci_hcd and address 38
[67214.880261] hub 1-0:1.0: unable to enumerate USB device on port 3
[67215.164045] usb 1-3: new high speed USB device using ehci_hcd and address 39
[67215.220272] hub 1-0:1.0: unable to enumerate USB device on port 3
[67215.504033] usb 1-3: new high speed USB device using ehci_hcd and address 40
[67215.560261] hub 1-0:1.0: unable to enumerate USB device on port 3
[67215.844039] usb 1-3: new high speed USB device using ehci_hcd and address 41
[67215.900265] hub 1-0:1.0: unable to enumerate USB device on port 3
[67216.184027] usb 1-3: new high speed USB device using ehci_hcd and address 42
[67216.240262] hub 1-0:1.0: unable to enumerate USB device on port 3
[67216.524033] usb 1-3: new high speed USB device using ehci_hcd and address 43
[67216.580259] hub 1-0:1.0: unable to enumerate USB device on port 3
[67216.868029] usb 1-3: new high speed USB device using ehci_hcd and address 44
[67216.924262] hub 1-0:1.0: unable to enumerate USB device on port 3
[67217.208033] usb 1-3: new high speed USB device using ehci_hcd and address 45
[67217.264262] hub 1-0:1.0: unable to enumerate USB device on port 3
[67217.548033] usb 1-3: new high speed USB device using ehci_hcd and address 46
[67217.604262] hub 1-0:1.0: unable to enumerate USB device on port 3
[67217.888035] usb 1-3: new high speed USB device using ehci_hcd and address 47
[67217.944262] hub 1-0:1.0: unable to enumerate USB device on port 3
[67218.228033] usb 1-3: new high speed USB device using ehci_hcd and address 48
[67218.284259] hub 1-0:1.0: unable to enumerate USB device on port 3
[67218.568029] usb 1-3: new high speed USB device using ehci_hcd and address 49
[67218.624263] hub 1-0:1.0: unable to enumerate USB device on port 3
[67218.908027] usb 1-3: new high speed USB device using ehci_hcd and address 50
[67218.964266] hub 1-0:1.0: unable to enumerate USB device on port 3
[67219.248033] usb 1-3: new high speed USB device using ehci_hcd and address 51
[67219.304260] hub 1-0:1.0: unable to enumerate USB device on port 3
[67219.588028] usb 1-3: new high speed USB device using ehci_hcd and address 52
[67219.644263] hub 1-0:1.0: unable to enumerate USB device on port 3
[67219.928036] usb 1-3: new high speed USB device using ehci_hcd and address 53
[67219.984263] hub 1-0:1.0: unable to enumerate USB device on port 3
[67220.268036] usb 1-3: new high speed USB device using ehci_hcd and address 54
[67220.324263] hub 1-0:1.0: unable to enumerate USB device on port 3
[67220.608031] usb 1-3: new high speed USB device using ehci_hcd and address 55
[67220.664265] hub 1-0:1.0: unable to enumerate USB device on port 3
[67220.948034] usb 1-3: new high speed USB device using ehci_hcd and address 56
[67221.004262] hub 1-0:1.0: unable to enumerate USB device on port 3
[67221.288030] usb 1-3: new high speed USB device using ehci_hcd and address 57
[67221.344264] hub 1-0:1.0: unable to enumerate USB device on port 3
[67221.628033] usb 1-3: new high speed USB device using ehci_hcd and address 58
[67221.684263] hub 1-0:1.0: unable to enumerate USB device on port 3
[67221.968036] usb 1-3: new high speed USB device using ehci_hcd and address 59
[67222.024262] hub 1-0:1.0: unable to enumerate USB device on port 3
[67222.308029] usb 1-3: new high speed USB device using ehci_hcd and address 60
[67222.364264] hub 1-0:1.0: unable to enumerate USB device on port 3
[67222.652035] usb 1-3: new high speed USB device using ehci_hcd and address 61
[67222.708266] hub 1-0:1.0: unable to enumerate USB device on port 3
[67222.992039] usb 1-3: new high speed USB device using ehci_hcd and address 62
[67223.048267] hub 1-0:1.0: unable to enumerate USB device on port 3
[67223.332028] usb 1-3: new high speed USB device using ehci_hcd and address 63
[67223.388266] hub 1-0:1.0: unable to enumerate USB device on port 3
[67223.672032] usb 1-3: new high speed USB device using ehci_hcd and address 64
[67223.728266] hub 1-0:1.0: unable to enumerate USB device on port 3
[67224.012030] usb 1-3: new high speed USB device using ehci_hcd and address 65
[67224.068266] hub 1-0:1.0: unable to enumerate USB device on port 3
[67224.352034] usb 1-3: new high speed USB device using ehci_hcd and address 66
[67224.408264] hub 1-0:1.0: unable to enumerate USB device on port 3
[67224.692032] usb 1-3: new high speed USB device using ehci_hcd and address 67
[67224.748267] hub 1-0:1.0: unable to enumerate USB device on port 3
[67225.032031] usb 1-3: new high speed USB device using ehci_hcd and address 68
[67225.088269] hub 1-0:1.0: unable to enumerate USB device on port 3
[67225.372032] usb 1-3: new high speed USB device using ehci_hcd and address 69
[67225.428266] hub 1-0:1.0: unable to enumerate USB device on port 3
[67225.712031] usb 1-3: new high speed USB device using ehci_hcd and address 70
[67225.768267] hub 1-0:1.0: unable to enumerate USB device on port 3
[67226.052039] usb 1-3: new high speed USB device using ehci_hcd and address 71
[67226.108267] hub 1-0:1.0: unable to enumerate USB device on port 3
[67226.392042] usb 1-3: new high speed USB device using ehci_hcd and address 72
[67226.448274] hub 1-0:1.0: unable to enumerate USB device on port 3
[67226.732036] usb 1-3: new high speed USB device using ehci_hcd and address 73
[67226.788971] hub 1-0:1.0: unable to enumerate USB device on port 3
[67227.072035] usb 1-3: new high speed USB device using ehci_hcd and address 74
[67227.128268] hub 1-0:1.0: unable to enumerate USB device on port 3
[67227.416029] usb 1-3: new high speed USB device using ehci_hcd and address 75
[67227.472266] hub 1-0:1.0: unable to enumerate USB device on port 3
[67227.756028] usb 1-3: new high speed USB device using ehci_hcd and address 76
[67227.812267] hub 1-0:1.0: unable to enumerate USB device on port 3
[67228.096034] usb 1-3: new high speed USB device using ehci_hcd and address 77
[67228.152266] hub 1-0:1.0: unable to enumerate USB device on port 3
[67228.436040] usb 1-3: new high speed USB device using ehci_hcd and address 78
[67228.492272] hub 1-0:1.0: unable to enumerate USB device on port 3
[67228.776036] usb 1-3: new high speed USB device using ehci_hcd and address 79
[67228.832267] hub 1-0:1.0: unable to enumerate USB device on port 3
[67229.116033] usb 1-3: new high speed USB device using ehci_hcd and address 80
[67229.172269] hub 1-0:1.0: unable to enumerate USB device on port 3
[67229.456037] usb 1-3: new high speed USB device using ehci_hcd and address 81
[67229.512268] hub 1-0:1.0: unable to enumerate USB device on port 3
[67229.796036] usb 1-3: new high speed USB device using ehci_hcd and address 82
[67229.852267] hub 1-0:1.0: unable to enumerate USB device on port 3
[67230.136033] usb 1-3: new high speed USB device using ehci_hcd and address 83
[67230.192268] hub 1-0:1.0: unable to enumerate USB device on port 3
[67230.476050] usb 1-3: new high speed USB device using ehci_hcd and address 84
[67230.532276] hub 1-0:1.0: unable to enumerate USB device on port 3
[67230.816034] usb 1-3: new high speed USB device using ehci_hcd and address 85
[67230.872267] hub 1-0:1.0: unable to enumerate USB device on port 3
[67231.156030] usb 1-3: new high speed USB device using ehci_hcd and address 86
[67231.212271] hub 1-0:1.0: unable to enumerate USB device on port 3
[67231.496033] usb 1-3: new high speed USB device using ehci_hcd and address 87
[67231.552267] hub 1-0:1.0: unable to enumerate USB device on port 3
[67231.836039] usb 1-3: new high speed USB device using ehci_hcd and address 88
[67231.892269] hub 1-0:1.0: unable to enumerate USB device on port 3
[67232.180044] usb 1-3: new high speed USB device using ehci_hcd and address 89
[67232.236274] hub 1-0:1.0: unable to enumerate USB device on port 3
[67232.520128] usb 1-3: new high speed USB device using ehci_hcd and address 90
[67232.576277] hub 1-0:1.0: unable to enumerate USB device on port 3
[67232.860033] usb 1-3: new high speed USB device using ehci_hcd and address 91
[67232.916269] hub 1-0:1.0: unable to enumerate USB device on port 3
[67233.200034] usb 1-3: new high speed USB device using ehci_hcd and address 92
[67233.256264] hub 1-0:1.0: unable to enumerate USB device on port 3
[67233.540033] usb 1-3: new high speed USB device using ehci_hcd and address 93
[67233.596521] hub 1-0:1.0: unable to enumerate USB device on port 3
[67233.880041] usb 1-3: new high speed USB device using ehci_hcd and address 94
[67233.936272] hub 1-0:1.0: unable to enumerate USB device on port 3
[67234.220034] usb 1-3: new high speed USB device using ehci_hcd and address 95
[67234.276269] hub 1-0:1.0: unable to enumerate USB device on port 3
[67234.560245] usb 1-3: new high speed USB device using ehci_hcd and address 96
[67234.617374] hub 1-0:1.0: unable to enumerate USB device on port 3
[67234.900041] usb 1-3: new high speed USB device using ehci_hcd and address 97
[67234.956269] hub 1-0:1.0: unable to enumerate USB device on port 3
[67235.240038] usb 1-3: new high speed USB device using ehci_hcd and address 98
[67235.296269] hub 1-0:1.0: unable to enumerate USB device on port 3
[67235.580037] usb 1-3: new high speed USB device using ehci_hcd and address 99
[67235.636270] hub 1-0:1.0: unable to enumerate USB device on port 3
[67235.920042] usb 1-3: new high speed USB device using ehci_hcd and address 100
[67235.976270] hub 1-0:1.0: unable to enumerate USB device on port 3

```


and the sticks stopped working on either of my 3 desktops (jaunty/xp/vista) or my netbook (AAO with linpus).


In fact in jaunty a window with file list popped up after a minute or two, but when I tried to delete the file from the usb stick it just closed and went back to nothing...  couldn't replicate the behaviour.



On windows the behaviour is a bit different...  either nothing happens...  or I get unknown usb device message.



I have a feeling that somehow ubuntu messed up the data on the devices and now they dont work anywhere...   is there a way to force a format or something if I cannot even save my files?

---

### Post by Th3Professor on 2009-06-20
> **Th3Professor said:**
> I plug a USB stick into the computer and it doesn't mount.

I've tried checking /media, used various commands, lspci, dmesg, fdisk, etc., but not really sure how to get it to mount.

It's not sda1, that's a hard drive, and yet howto pages online say to mount that. Of course it'll be different on different computers, yet I'd think it'd be possible to at least find out which /dev I can use to mount it under.

Any ideas?

Thanks!

Multiple pages and still pretty much nothing lol. :p {bump} ;)

---

### Post by NiksaVel on 2009-06-21
A friend of mine pointed out that I probably have a messed up usb port which seems to be frying my usb sticks...     seems to be the most logical solution as all the sticks seem to have hardware problems...

---

### Post by ubunter760 on 2009-06-21
I have problems with USB sticks intermittently since upgrading from Intrepid.  Some work, most don't.  I don't have a solution or anything valuable to add, just though I would take a giant bite of this crap sandwich with the rest of you.

---

