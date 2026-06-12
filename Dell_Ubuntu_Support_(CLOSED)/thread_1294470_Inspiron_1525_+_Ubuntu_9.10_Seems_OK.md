---
title: "Inspiron 1525 + Ubuntu 9.10 Seems OK"
date: 2009-10-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by azumi123 on 2009-10-18
As there are questions about 1400 x 900 res I just thought I'd
report the 9.10 (beta?) release seems to work ok.

My story so far:
I have an Inspiron 1525 + 4Gb ram 1400x900 display and conexant modem 
and Matshita BluRay writer.
It came with Vista installed so I used it that way until I couldn't
take it any longer and just formatted the hard drive to get rid of it.

I then did a clean install of Ubunto 9.10 and it just worked first time. 
I then enabled bluetooth (Vista just never worked at all with that) and like magic my mouse started working after I clicked the 2 buttons needed to install it. (So far I'm a very happy bunny !!!)

All the apps and stuff seem very nice and all work with no problems, but of course UBUNTU doesn't have dialup modem support (Rather stupidly IMHO)

So now I have a problem -

After about 6 hours I discovered I needed and located:

1. An ALSA driver for the sound card - it seems the conexant is one of these stupid software modems (some designers should be drowned at birth) 

2. The conexant driver has gone missing from the Dell site but eventually I found one 

3. Then I needed Gnome-Network-Manager and here I'm stuck in the usual Linux "whats the difference between a software hack and a software application"  loop, endlessly running around transfering dependancies 
from my win98 box on a cruzer stick. The Dell USB's worked perfectly too.

OK Now we have a problem as one of the dependancies (gettext tools) just refuses to install and that's where I'm stuck.

I also can't seem to get the UDF 2.50 driver I found on sourceforge to install but didn't try too hard and will look into it. I have BluRay so I want to use it. Excuses don't interest me.

I expect I'll have trouble playing DVD's and working with BluRay but I'm hoping there are solutions out there because I'll have to try and install 
winME instead if not. (Oh yes it does... ;-) )

Anyway if anyone is still reading thats where my Inspiron is at right now. 
If I get anything else working I'll try and log it here in case it helps someone.

Az.

---

### Post by jessiebrownjr on 2009-10-18
I originally did a wipe on mine with nothing but Ubuntu but at that point I was still playing WoW, now I just code and browse the net so I don't boot into windows anymore..  only problem I have had on my 1525 is the xorg driver which i bet is fixed or will be fixed by the end of the month.  GL!

---

### Post by Matt_Rapp on 2009-10-25
Hey all,

I just downloaded the 9.10 Release Candidate and ran it from a USB Drive to see if everything will come together next week. My Broadcom wi-fi card was not recognized automatically as it has been in previous releases, but after awhile a notification appeared saying that there were restricted drivers available for my wi-fi card. I'm typing this from my normal 9.04 installation so I can't copy the exact names over but there was one that said it could extract the correct driver from a file, like ndiswrapper I know but this was showing up in the hardware driver prompt, and ndiswrapper which claimed to work for about five model numbers of Broadcom cards. I chose the second one as I had no file and rebooted for it to take effect. On Reboot my wi-fi card was still not picked up and the hardware drivers prompt showed the driver I chose as installed but not in use. What should I do to get this working once the full build comes out next week? I'm on an inspiron 1525 that's only about a year old. Here is the out put from lshw -C network.

Any ideas?

```
root@i1525-Ubuntu-Laptop:/home/i1525# lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:dd:7e:7c
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e2:81:69:2a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.0.66 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:2e:7c:7b:2c:0a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@i1525-Ubuntu-Laptop:/home/i1525# 
```****

---

### Post by chuckyp on 2009-10-25
With the broadcomm cards you need the firmware. The restricted drivers manager should help you install the bcm43xx firmware package.

---

### Post by Matt_Rapp on 2009-10-26
Okay, where is it going to get the bcm43xx firmware package if it can't connect to the net? Will everything just sort it self out if I chose the other driver and hook up to an Ethernet cable, or do I have to hunt down the driver file for windows?

---

### Post by lightshayde on 2009-11-21
My friend recently installed 9.10 on his Inspiron; I got the Broadcom STA driver enabled but now, even though he can connect to his wireless network, Ubuntu will not let him access the internet. 
Ideas?

---

### Post by Matt_Rapp on 2009-11-21
I don't know what to say, can he get on the net when hooked up through a different connection like Ethernet? Could check the modem if you haven't done that already.

I still haven't gotten my wireless to work, what did you do for yours?

---

### Post by Frankenpunk on 2009-11-22
I just installed 9.10 on my Inspiron 1525, with Vista pre-installed. Vista is still there and shows up in Grub.

My broadcom wifi did not work, and I didn't have an ethernet cable to connect the laptop to. So this is what I did, and it works splendid:

Download the appropriate driver from here (32 or 64 bit):
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Follow these instructions:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

[COLOR="SlateGray"]For noobs, wherever the instructions start with a "#" mark, you need to type that into (Applications > Accessories >) Terminal. There are some parts where it refuses to do what you ask. In such cases, type "sudo" (without the quotes, of course) before the command. For example, if it reads:
[INDENT]# rmmod b43[/INDENT]
you would type this into the terminal:
[INDENT]rmmod b43[/INDENT]
and if it says that it didn't do it, type
[INDENT]sudo rmmod b43[/INDENT]
then you'll have to type in your root password
(search "how to make sudo password" if you don't know about that)

Also, the lines that ask me to blacklist didn't work for me, even with sudo; e.g. the following instruction:
[INDENT]# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
[/INDENT]
So I worked around that by doing this in the terminal:
[INDENT]sudo gedit /etc/modprobe.d/blacklist.conf[/INDENT]
and I added these lines to the bottom of the document, saved, and closed it.
[INDENT]blacklist ssb[/INDENT]
[INDENT]blacklist b43[/INDENT][/COLOR]
Once all that is done, open System > Administration > Hardware Drivers and Activate the Broadcom STA wireless driver. If it doesn't show up, first run System > Administration > Update Manager, and update your system.
Then it will work even when you reboot.

---

### Post by andy_savage on 2009-12-01
Thanks [Frankenpunk]("http://ubuntuforums.org/member.php?u=708754"). It worked for me too...  :)

---

### Post by foogoo on 2009-12-18
Thank you Frankenpunk!! Excellent instructions!

---

### Post by reiki on 2009-12-20
I am interested in what you did for an ALSA driver for the conexant sound.

I have a new Dell Zino HD with a conexant sound card and the rear analog jack does not get recognized. Current'y jave my speakers connected to teh headphone jack on the front.... not exactly pretty. :)

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Using Codec : Conexant CX20561 (Hermosa).

The jack works fine in Win7 ... just not working in Ubuntu 9.10

---

### Post by StormyWolf on 2010-02-04
I've been seaching for hours to get my wifi working on Ubuntu trawling through tonnes of feeds and forums and your simple links to the guide and drivers got me up and running in seconds. Much appreciated!!!

---

