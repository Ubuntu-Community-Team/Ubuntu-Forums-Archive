---
title: "Sony PSP on Dapper. (Won't mount)"
date: 2007-08-26
forum: Gaming &amp; Leisure
---

### Post by Nathan Otis on 2007-08-26
SO I want to plug my Sony PSP in to my (Dapper) Ubuntu machine for file transfers and what not. I'm accustomed to things "just working" in Ubuntu and was surprised when the PSP did not simply show up on my desktop like my phone or iPod normally does.

So I went out and searched. I found a couple system setting things to check:

[B][U]    *      Navigate to "System" > "Administration" > "User and Groups"
    *      Choose the user, click on "Properties"
    *      Go to the "User Privileges" tab

Should have the "Access external storage devices automatically" option checked.[/U][/B]

Done. I can see it in places/computer, but can't mount it. Won't show up on the desktop, so then I found:

[B][U]If your usb device doesn't appear on your desktop, you should check that the automount action is enabled in the preferences:

    *      Navigate to "System" > "Preferences" > "Removable Drives and Media"
    *      Verify that all "Mount removable drives when..." are checked.
[/U][/B]
Done. Still doesn't mount.

Then I ran Terminal with the command "DMESG" both before and after plugging in the device. I got the following results before (this is just the end of the string):

********************************
[17179744.816000] eth0: increased tx threshold, txcfg 0xd0f01008.
[17179759.776000] eth0: increased tx threshold, txcfg 0xd0f0100a.
[17179759.868000] eth0: increased tx threshold, txcfg 0xd0f0100c.
[17179777.884000] eth0: increased tx threshold, txcfg 0xd0f0100e.
********************************

And After (again, just the end of the string):

********************************
[17179744.816000] eth0: increased tx threshold, txcfg 0xd0f01008.
[17179759.776000] eth0: increased tx threshold, txcfg 0xd0f0100a.
[17179759.868000] eth0: increased tx threshold, txcfg 0xd0f0100c.
[17179777.884000] eth0: increased tx threshold, txcfg 0xd0f0100e.
[17180205.164000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[17180205.296000] usb 3-1: not running at top speed; connect to a high speed hub[17180205.464000] Initializing USB Mass Storage driver...
[17180205.464000] scsi0 : SCSI emulation for USB Mass Storage devices
[17180205.464000] usb-storage: device found at 3
[17180205.464000] usb-storage: waiting for device to settle before scanning
[17180205.464000] usbcore: registered new driver usb-storage
[17180205.464000] USB Mass Storage support registered.
[17180210.468000]   Vendor: Sony      Model: PSP               Rev: 1.00
[17180210.468000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17180210.480000] usb-storage: device scan complete
[17180210.540000] Driver 'sd' needs updating - please use bus_type methods
[17180210.552000] SCSI device sda: 8110080 512-byte hdwr sectors (4152 MB)
[17180210.552000] sda: Write Protect is off
[17180210.552000] sda: Mode Sense: 00 6a 20 00
[17180210.552000] sda: assuming drive cache: write through
[17180210.568000] SCSI device sda: 8110080 512-byte hdwr sectors (4152 MB)
[17180210.572000] sda: Write Protect is off
[17180210.572000] sda: Mode Sense: 00 6a 20 00
[17180210.572000] sda: assuming drive cache: write through
[17180210.572000]  sda: sda1
[17180210.580000] sd 0:0:0:0: Attached scsi removable disk sda
[17180210.596000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17180211.424000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180211.428000] FAT: count of clusters too big (126559)
[17180211.428000] VFS: Can't find a valid FAT filesystem on dev sda1.
********************************

I'm no genius, but it looks like a problem with the format on the memory stick. Thing is, I formatted just before running DMESG. There is some mention of the "SD" driver. I've searched for info on updating it, but I've come up empty handed.

Does this give anyone the info they need to help a brother out?

---

### Post by Nathan Otis on 2007-08-26
Ok this is interesting...

I'm reading over the output from DMESG and I noticed the bit about the file system... So I jumped over to Windows and did a full format of the memory stick. Back to Ubuntu, plug in the PSP, go to USB mode, and there it is!!

"Great!", I thought for a moment. Then I jumped out of USB mode, had the PSP format the memory card so all the correct directory structure is on there, and it's gone again.

Something about the firmware I'm running (3.52 M33) doesn't like Ubuntu. Anyone have ideas or gotten this running before?

---

### Post by jacob01 on 2007-08-26
yea  that is weird i have a psp and im running firmware 2.8 (i wanted to run some home brew apps so i decided not to upgrade) and running feisty and when i format the memory card using the psp it is still detected go into windows and see what the psp formates the memory card as i believe my psp formates my psp to fat ill check yea i pluged my psp in while in psp mode and ran a command 

sudo fdisk -l and it said 
 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         990      126703+   6  FAT16


yea and the psp 2.8 formates the memory stick to fat16
 try pluging in your psp into you computer with the psp formated stick and run sudo fdisk -l and see if it detects you psp

worth a try


is m33 a hacked psp firmware ?

i haven't kept up on that suff

i stopped when i could run homeberew on 2.8

---

### Post by Nathan Otis on 2007-08-26
Ok, if I read this right, Ubuntu sees the PSP:

[B]otis@otis-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        2040     1028160   82  Linux swap / Solaris
/dev/hda3            2041        7299    42242917+  83  Linux

Disk /dev/sda: 4152 MB, 4152360960 bytes
128 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 7936 * 512 = 4063232 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1021     4050960    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 4, 0) logical=(0, 4, 8)
Partition 1 has different physical/logical endings:
     phys=(989, 127, 0) logical=(1020, 120, 15)
Partition 1 does not end on cylinder boundary.
[/B]

The memory card is Fat16... So what's that mean? Why isn't Ubuntu seeing it?

3.52 M33 is a custom firmware. A Russian hacker picked up where DarkAleX left off with 3.51oe

---

### Post by Nathan Otis on 2007-08-30
Bueller?

---

### Post by Nathan Otis on 2007-08-30
The error message I'm getting when I try to mount the PSP says words to the effect that I have a bad "superblock" on /dev/sda1.

Is that bad memory? I've not heard of a superblock... Though a google search turns up a lot of information I don't fully understand... It sure seems like bad memory. I think I'm going to get another memstick and see if that fixes this (and a couple other issues I've been having).

---

### Post by jacob01 on 2007-08-31
> **Nathan Otis said:**
> Ok, if I read this right, Ubuntu sees the PSP:

[B]otis@otis-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        2040     1028160   82  Linux swap / Solaris
/dev/hda3            2041        7299    42242917+  83  Linux

Disk /dev/sda: 4152 MB, 4152360960 bytes
128 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 7936 * 512 = 4063232 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1021     4050960    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 4, 0) logical=(0, 4, 8)
Partition 1 has different physical/logical endings:
     phys=(989, 127, 0) logical=(1020, 120, 15)
Partition 1 does not end on cylinder boundary.
[/B]

The memory card is Fat16... So what's that mean? Why isn't Ubuntu seeing it?

3.52 M33 is a custom firmware. A Russian hacker picked up where DarkAleX left off with 3.51oe

i dont think the /dev/sda1 is your memory stick that is usually a sata hard drive

my psp was recognized as /dev/sdb1

---

### Post by jacob01 on 2007-08-31
> **Nathan Otis said:**
> Ok, if I read this right, Ubuntu sees the PSP:

[B]otis@otis-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        2040     1028160   82  Linux swap / Solaris
/dev/hda3            2041        7299    42242917+  83  Linux

Disk /dev/sda: 4152 MB, 4152360960 bytes
128 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 7936 * 512 = 4063232 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1021     4050960    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 4, 0) logical=(0, 4, 8)
Partition 1 has different physical/logical endings:
     phys=(989, 127, 0) logical=(1020, 120, 15)
Partition 1 does not end on cylinder boundary.
[/B]

The memory card is Fat16... So what's that mean? Why isn't Ubuntu seeing it?

3.52 M33 is a custom firmware. A Russian hacker picked up where DarkAleX left off with 3.51oe

oh ok yea hmm could that have any thing to do with it  since you flashed a new bios/rom into the psp maybe ubuntu isnt recognizing it as a removeable device but as another computer or drive

that might explain why it was recognized as a /dev/sda1
also how big is you memory card    1 gig

i don't know how some one would go about installing a hard drive i don't have that much experience but maybe try restarting your computer and let it boot up with you psp pluged in and in the usb mode 

or you could try to mount it like some one would mount an external hard drive

---

### Post by Nathan Otis on 2007-08-31
Booting with it plugged in and USB mode on doesn't work.

The Memstick is 4gb.

When I go to Places/Computer, Ubuntu sees that the PSP is plugged in, lists it as "Sony Music Player", but when I go to mount it, Ubuntu throws the following error:

[B]Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

Details>
mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or other error
in some cases useful info is found in syslog - try
dmesg | tail or so

error: could not execute pmount[/B]

---

### Post by jacob01 on 2007-08-31
> **Nathan Otis said:**
> Booting with it plugged in and USB mode on doesn't work.

The Memstick is 4gb.

When I go to Places/Computer, Ubuntu sees that the PSP is plugged in, lists it as "Sony Music Player", but when I go to mount it, Ubuntu throws the following error:

[B]Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

Details>
mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or other error
in some cases useful info is found in syslog - try
dmesg | tail or so

error: could not execute pmount[/B]

i dont know what to tell you other than point out the obvious, for some reason dapper or your computer cant read fat16 file systems but yea at least you could get it to work bu formating it in windows 

what you could do is upgrade to feist 7.04

or you can format your psp mem stick in windows then just leave it and if you ever need to format it again just format it with windows.

i dont have any other ideas

that is really strange though. it recognizes the psp but it doesn't mount like you said 

you dont have a mod chip by any chance do you?
or did you just flash a new rom on your psp

 sorry about that i thought this was your psp "/dev/sda1 * 1 1021 4050960 6 FAT16" i dont know for sure i have no idea what that is

Disk /dev/sda: 4152 MB, 4152360960 bytes
128 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 7936 * 512 = 4063232 bytes
this is your psp correct? i think so about 4 gig  

why did you say your psp was fat16

it doesnt say that it is fat 16

the other one does the /dev/sda1  hmmmm..

sorry /dev/sda1 is the psp it has 1 partition ok i got it now and it is fat16. yea i dont know?

it must be something to do with 6.10 (dapper)

---

### Post by Nathan Otis on 2007-09-01
> **jacob01 said:**
> what you could do is upgrade to feist 7.04

Interesting. I'll think about that.

> or you can format your psp mem stick in windows then just leave it and if you ever need to format it again just format it with windows.

That's a negative. I run custom firmware (which is probably most of the problem), but I need to run CFW to play PSX games and back up UMDs.

> you dont have a mod chip by any chance do you?
or did you just flash a new rom on your psp

No mod chip, just the CFW.

> it must be something to do with 6.10 (dapper)

Feisty, you say... Hmmmm. Is that the new "We'll support this for a long time" version?

---

### Post by jacob01 on 2007-09-01
yea my psp will mount on fiesty but i not sure about dapper

that is the only other advice i have  is to upgrade to feisty wich is the latest stable version of ubuntu.

but i am not sure about your 4 gig memory card could that have some thing to do with it. dapper not being able to mount a removable storage device that big?

---

### Post by Nathan Otis on 2007-09-01
This morning I upgraded to Edgy and then to Feisty (wasn't aware you could go from Dapper directly to Feisty...

Plugged in the psp, selected USB mode, no love.

Went to Best Buy, dropped almost a hundie on a new 4gb memstick and I'm here to tell you it actually matters! I plugged in my PSP to the Feisty with the new memstick and I'll be darned if an icon didn't show up on my desk top.

Now it's not "perfect" because Ubuntu thinks my PSP is an iPod. But it shows up at least!

Thanks for the suggestions and assistance.

---

### Post by anjilslaire on 2007-09-01
> **Nathan Otis said:**
> 
Went to Best Buy, dropped almost a hundie on a new 4gb memstick and I'm here to tell you it actually matters! I plugged in my PSP to the Feisty with the new memstick and I'll be darned if an icon didn't show up on my desk top.
.

Not surprising. I've read quite a bit about lots of 4gig duo pro's not being legitimate cards & causing quite a bit of issues. 
Glad you got it sorted out.

I'm running 3.52 M33-4 with  a 2gig SanDisk & everything is fine here.

BTW, what is everybody's favorite method to convert video to their PSPs?

---

### Post by jacob01 on 2007-09-01
ffmpeg all the way 

this is what i do cd to the directory change -i to the name of the vid and press enter

here a template for you

ffmpeg -i file name -f psp -r 14.985 -s 320x240 -b 768 -ar 24000 -ab 32 M4V00002.MP4

that converts it to mp4/acc and also makes the file smaller so it works the best for me

---

### Post by anjilslaire on 2007-09-01
cool, thanks

---

### Post by anjilslaire on 2007-09-02
hmm.
The script provides great video output, and the audio is synced correctly. However, the volume is WAYYYY too low. The audio is extremely quiet. Is there an option to add to increase the volume level?

Thanks again.

---

### Post by jacob01 on 2007-09-02
i dont know it woks great for me but maybe a solution would be to change the  -ab the audio bit rate or to change the -ar the audio rate 

try to raise the -ar since i think the -ab is the audio bit rate which controls the  sound quality and the -ar is the sampling rate/audio     raise it by changing the 24000 to a higer number it might take ome messing around to get it right

other than that i dont know  

are there any problems with your video having low sound

---

### Post by anjilslaire on 2007-09-02
Thanks,
After posting, I started looking into ffmpeg options further, and found the option **-vol** and modified the code as follows:
```

ffmpeg -i file name -f psp -r 14.985 -s 320x240 -b 768 -ar 48000 -ab 32 -vol 5000 output.MP4

```
Originally I kep -ar at 24000, but at a higher volume, the audio was very poor quality. After upping it to 48000, it is much better.

The issue is:
Random videos downloaded from the net seem to have fine volume levels. However, I prefer to encode my DVDs into xvid for playback and store the discs away safely. However, when I encode the xvids to .mp4 with ffmpeg, the audio was almost silent, even with the volume at maximum.
Altering your code as above seems to fix this, and only makes the .mp4 file about 20mb larger. A complete episode of "Lost", for example goes from my  540mb "source" to 156mb for my psp.
Thanks again for the help.

---

