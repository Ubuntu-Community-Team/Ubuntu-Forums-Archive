---
title: "Problems installing on Dell mini 9"
date: 2009-03-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mtbsoft on 2009-03-04
I got a Dell mini 9 recently with XP on it and tried to dual boot it (16Gb SSD and 16Gb SD for common area).  Trouble is that I don't have a USB CD so I've been using an image from a USB drive, created using unetboot.

All goes fine until about 90% through then it bombs just before installing grub (I'll try again tonight and post the actual error).  This is starting to hack me off.

I'm just wondering how other mini 9 users have installed Ubuntu on theirs.

---

### Post by armandh on 2009-03-04
I dual boot XP and Ubuntu 8.10 [xp used only for quickbooks.]
on a 16 gig mini9

I bought a usb 5" drive case on amazon and installed a spare dvd/cd drive. I have since booted from live a usb created using 8.04's option under "system>administration>create usb start up disk" but not I've installed from there yet.

I used a live partition utility to create a primary active NTFS partition about half the size and I installed non dell XP to that partition. the dell driver disk made everything work.

I installed Ubuntu 8.10 selecting the "guided use unpartitioned space" partition option. it created an extended partition and installed Ubuntu and a swap partition to it. Grub worked as expected

after updates I added the one CL of code to get sound, added flash, added medibuntu.org for DVDs etc. and added compiz manager for all the glitz and glory and set up wireless lan last.

I use a 4G flash memory for removable, common to both, storage.

recovery disks supplied by dell do not install the OS rather they format the whole drive and copy the os.

if you are using the dell XP I would use a live partition manager to reduce the size of the partition to about half and install 8.10 as above.

---

### Post by Rallg on 2009-03-04
I had no problem with my 16G mini 9 XP, installing Ubuntu as dual-boot from USB-untebootin.

But I did not use a separate SD at any point. When you say that it is common storage, do you mean that it is just a place to put files, or are you trying to make it your Ubuntu home directory? Was the SD card in place, when you were performing the install?

Try this: Using the live Ubuntu from the USB, does it interact well with your SD card? If not, does it make a difference whether the card is in place when you boot from the USB, or whether you first complete the boot then insert the card?

---

### Post by notwen on 2009-03-04
I also dual-boot my Mini 9, w/ XP Home UMPC and Hardy.  Did you use [Unetbootin]("http://unetbootin.sourceforge.net/") by chance to create your USB drive installer?

I installed XP first, re-sized my partition, then installed Hardy.  Afterwards I added my SDHC card and have it set in my /etc/fstab to automount in Ubuntu and XP mounts it automatically anyway.

---

### Post by jaywatkins on 2009-03-04
Hello,

How did you guys get the wifi to work?  I have the Dell drivers CD copied to a USB flash-drive, but can't seem to find the wireless driver. I too, am using a UNetBootin flash-drive to try 8.10 and see if it picks up my hardware before installation.

The Mini-9 has a 16GB SSD, w/2GB of RAM and came from Dell w/Linux already installed.  I am looking to just have Ubuntu or Xubuntu 8.10 installed instead.

Thanks

---

### Post by Mig Daddy on 2009-03-04
I am running 8.10 as the only OS on my Mini.  After installation, the wireless card was detected automatically.  It asked me if I wanted to install the proprietary Broadcomm driver.  Just say yes and everything should work just fine.

---

### Post by Rallg on 2009-03-04
My mini 9 (originally with XP) worked immediately with WiFi in Ubuntu 8.10, both on the live USB, and after installation. I did not fool with the Dell drivers. Upon installation, the Ubuntu hardware manager told me that a proprietary WiFi driver was available (my WiFi was already working). So I downloaded the proprietary driver, and it still works.

Later, I removed XP, and the Ubuntu WiFi still works. I removed Dell's own little partition, too, without problem. However, I recommend leaving the Dell partition in place. It is handy to have some FAT storage when you need to update the BIOS.

If you are trying to use Ubuntu prior to 8.10 on the mini 9, I recommend using 8.10 instead.

---

### Post by anjilslaire on 2009-03-04
I installed 8.10 via usb by creating it with Ubuntu's own "Create a USB Startup Disk" from within Intrepid on my desktop.

After creating, I stuck the udb into my mini 9, booted, and installed. 

If you need help, I recommend this:
[http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

---

### Post by jaywatkins on 2009-03-04
Hello,

I have seen that.  What about the sound?

---

### Post by armandh on 2009-03-04
> **jaywatkins said:**
> Hello,

I have seen that.  What about the sound?


SOUND FIXED
[http://ubuntuforums.org/showthread.php?t=984058](http://ubuntuforums.org/showthread.php?t=984058)

---

### Post by jaywatkins on 2009-03-04
Nice blog/tutorial here as well.

[http://www.ubuntumini.com/2008/10/ubuntu-810-intrepid-ibex-on-dell-mini-9.html](http://www.ubuntumini.com/2008/10/ubuntu-810-intrepid-ibex-on-dell-mini-9.html)

---

### Post by N74JW on 2009-03-04
The suggestion from the posted thread did not enable my sound adapter.

Anywhere else I could look?

Thanks

---

### Post by anjilslaire on 2009-03-04
There must be something going, because adding the line
```

options snd-hda-intel model=dell

```
to /etc/modprobe.d/alsa-base, rebooting, and turning the Speaker volume up ***will*** solve the sound issue on a dell mini with x86 8.10 installed.

---

### Post by mtbsoft on 2009-03-05
Well ain't that just the darned way of it!  I try again tonight (the fifth time so far) and the damned thing works - you guys just talking about it fixed it good, nice one fellas!

Seriously though, the only thing I can think of is that I connected the install session to the net tonight and I don't remember doing that before - maybe that was it.

I'll trawl throught the various information you've all provided and get this thing set up nicely, thanks for the information.

@Rallg: I meant that the SD card would be a FAT32 common area between XP and Linux.

---

### Post by jaywatkins on 2009-03-05
There are two files in /etc/modprobe.d/  alsa-base and alsa-base~  I will try modifying the alsa-base~ file and see what's what.  I also kept the original Dell Ubuntu installation.  The same file in that install is somewhat different.

Thanks for the help!

---

### Post by jaywatkins on 2009-03-05
The alsa-base file from the Dell install of Ubuntu did not work.  Modifying the backup copy of alsa-base file also did not fix the problem.

When I use the "Sounds" applet to try an assign a device, there are numerous suggestions and when I click "Test" on any one of them a bouncing dialog opens instructing me to "Click OK to finish".  Nothing actually happens though...

This has to be able to work as it does with the previous version of Ubuntu, installed by Dell.  Too bad Dell branded their install with Yahoo and that stupid task-bar, or I would just keep it.

Below is my alsa-file:

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=dell

---

### Post by jaywatkins on 2009-03-05
Curious... If I select "HDA Intel ALC268 Analog (ALSA) for sound playback event in the "Sound Preferences" dialog, the following error is produced.

audiotestsrc wave=sine freq=512!
audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback.

No other sound option gives this result.

Thanks

---

