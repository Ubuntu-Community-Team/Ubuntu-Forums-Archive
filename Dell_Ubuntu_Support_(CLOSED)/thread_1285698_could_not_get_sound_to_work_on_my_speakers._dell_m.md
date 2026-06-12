---
title: "could not get sound to work on my speakers. dell mini 10v"
date: 2009-10-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shiningkenmonster on 2009-10-08
I could not get the sound speakers to work on my dell mini 10v. I am using Canonical's Ubuntu 8.04.3. Not Dell's 8.04 Ubuntu. all updates installed. even the restricted-extras!

The sound speakers worked for previously installed os, which are: Dell's Ubuntu 8.04, Jaunty Jacklope netbook remix, Ubuntu Moblin Remix Developer Edition and Karmic Koala netbook beta.

the reason why i switched to Canonical's Ubuntu 8.04.3 is because I didn't like the "bugs" on the other systems. I just wanted something more stable.

Canonical's Ubuntu 8.04.3 sound does work with an earphone/headphones.
but speakers does not work. How do i get them to work?

---

### Post by Brandon Williams on 2009-10-08
I remember that this was necessary on Jaunty at some point, maybe it's necessary on Hardy, too: Open the mixer and look for the control for the speaker. Turn it all the way up.

What bugs were you seeing on Dell's 8.04 that you don't see on Canonical's 8.04? I've been running Dell's 8.04 on my 10v since I got it and I haven't had any problems with it that would drive me to try a different version of the distro.

---

### Post by shiningkenmonster on 2009-10-08
yes, the mixer settings are all the way up. nothing is muted. 

i can hear sounds when i plug in an ear piece/headphone. and yes, the mixer setting is the same. its turn all the way up.

is there a way to enable my speakers to work on my dell mini 10v?

---

### Post by shiningkenmonster on 2009-10-08
well, i was an early adapter of the dell mini 9, since Nov 2008 and i was using dell's ubuntu 8.04 from the beginning. at that time, installing anything .deb files and the installing a application on the terminal would not work.
It took until Jan 2009, for them to fix it.
I always think dell takes a long time to update their systems.

i bought a dell mini 10v.  When going out to public places to use wifi, when the wifi is temporary down for a minute. My Dell Ubuntu 8.04 would freeze up almost everytime the wifi is down. 

I thought the freezing was terrible compare to Windows Millennium Edition.

Someone else on this forum had the same problem as me using the Dell's Ubuntu 8.04 with the freezing due to wifi problems. He called dell, and the tech support told him to reinstall the dell ubuntu os. he did, and the problem still happen. Than he installed Jaunty Jacklope from Canonical. He said he never experience the problem again.

---

### Post by Zoot7 on 2009-10-08
Try installing the alsamixer
```
sudo apt-get install gnome-alsamixer
```

Then see if anything is muted there. Chances are your problem is just a muted channel.
Using this app is what got the 2 headphone sockets on my XPS M1530 working okay.

---

### Post by shiningkenmonster on 2009-10-09
i just installed gnome-alsamixer. nope, all of the settings are to full volume. i even played around with the settings.

the sound speakers aren't working

---

### Post by Brandon Williams on 2009-10-09
Have you tried the fix suggested in [this post](http://ubuntuforums.org/showthread.php?t=314383)? I'm not sure which of the model values will work for you, but you might as well try with:
```
options snd-hda-intel model=dell
```
to start with.

---

### Post by shiningkenmonster on 2009-10-10
ah yes, that reminds me of this a person who installed Ubuntu 8.10 dekstop on his dell mini 9 blog. He wrote instructions which were:
 
in the terminal:
```
sudo gedit /etc/modprobe.d/alsa-base

```

and add the following command at the bottom of the text editor:
```
options snd-hda-intel model=dell
```
saved it.

and he rebooted. and he opened the mixer and put the volume settings all the way up. the sound worked just like that.

I just tried that. it didn't work. than i tried changing the "model" value in the gedit to:

```
options snd-hda-intel model=red
options snd-hda-intel model=snd_hda_intel
```
all rebooted. still no go.

I have Master, PCM, Capture, Digital all checked.

hmm, i think i might be getting closer to getting the speakers to work. but i am still stuck with them not working

---

### Post by shiningkenmonster on 2009-10-12
```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

$ lshw -class multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

---

### Post by shiningkenmonster on 2009-10-16
is the solution Jaunty and Karmic installs?

---

