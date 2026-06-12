---
title: "hardware problems"
date: 2005-09-12
forum: Desktop Environments
---

### Post by Strongbad on 2005-09-12
I am having some troable with my modem, and my cd drives, my modem is only going about half speed, and my cdrom drive and my burner are going realy slow. The modem is a 3COM USRobotics model 5610 hardware modem, my burner is a 48X tdk usb external drive, and I don't know much about my cdrom drive, exept that it's an ide 32X drive. The modem has had me stumped for a while, I have tryed different dialing programs, and various configureations, but it still runs realy slowly. The connection is allways timing out, and I get error messages in firefox often. I have flow control enabled in wvdial, but it hasn't helped any. With the cdrom drives, I am getting very slow ripping and burning speeds. I know it's not a problem with the hardware because I have plugged my burner into my windows machine and it worked fine. I have dma enabled for both devices and it hasn't helped any.
 Any ideas? :-?

---

### Post by mlomker on 2005-09-12
[QUOTE=Strongbad]I have dma enabled for both devices and it hasn't helped any.[/QUOTE]

DMA is good but how many bits is it transferring at?  You'll want it set to 32-bit.

```

root@mlomkernote:/etc/udev # hdparm -v /dev/dvd

/dev/dvd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

```

The command is **hdparm -c1d1 /dev/dvd**

---

### Post by Strongbad on 2005-09-13
That command you gave me worked for my ide drive, but It gives me this message when I try to do it with my usb drive, :-?  I know that that is the address, because that's what I type in when I play a cd with xmms. Any ideas?

/dev/scd0:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument

---

### Post by mlomker on 2005-09-13
[QUOTE=Strongbad]That command you gave me worked for my ide drive, but It gives me this message when I try to do it with my usb drive, :-? [/QUOTE]

Yeah, I was just hoping it'd help with the drive on your IDE controller.  Add that command to the end of the /etc/init.d/bootmisc.sh file...otherwise it'll get reset on every reboot.

Oh, you should definitely check out your hard disks as well.

hdparm -v /dev/hda  (or whatever the drive is).

sudo fdisk -l (will give you the drive devices if you're not sure).

---

### Post by Strongbad on 2005-09-14
Thanks! Is there something I could do with my usb drive though? I know it works fine on other systems. Is there a driver or something I could download? Or is there another config file for external hardware? I will try just about anything at this point. Oh, and does anybody know anything about, or had a similar problem that I'm having with my modem?

---

### Post by mlomker on 2005-09-15
[QUOTE=Strongbad]Thanks! Is there something I could do with my usb drive though? I know it works fine on other systems. Is there a driver or something I could download? Or is there another config file for external hardware? I will try just about anything at this point. Oh, and does anybody know anything about, or had a similar problem that I'm having with my modem?[/QUOTE]

USB seems to be slower in linux and especially in Ubuntu.  I've seen the same thing with my flash drive.  There's something going on there.

I'd recommend a new thread in the hardware forum for your modem problem.

---

### Post by Strongbad on 2005-09-15
Hmmm.... Oh well, maybe they will fix it in breezy badger :) 

Thanks for all your help!

---

