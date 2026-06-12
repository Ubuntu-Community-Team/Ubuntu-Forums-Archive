---
title: "Im new at ubuntu and cannot get wireless working please help"
date: 2010-05-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by matixsf on 2010-05-28
Hello,
 I have downloaded the latest and greatest ubuntu 10. 1million, I am connected wired connection now and cannot connect via wireless(linksys wrt54g) It used to be fined but now I get a message of " you are now disconnected" everytime I try to use wireless. I also have no clue how or if I can get Itunes/Ipod to work....my daughter is dying about this Ipod thing. Sorry for the newb-ness but it is what it is, I just don't know this stuff
Thank you for any help
Todd

---

### Post by garvinrick4 on 2010-05-28
> **matixsf said:**
> Hello,
 I have downloaded the latest and greatest ubuntu 10. 1million, I am connected wired connection now and cannot connect via wireless(linksys wrt54g) It used to be fined but now I get a message of " you are now disconnected" everytime I try to use wireless. I also have no clue how or if I can get Itunes/Ipod to work....my daughter is dying about this Ipod thing. Sorry for the newb-ness but it is what it is, I just don't know this stuff
Thank you for any help
Todd Right click on applet in upper right of desktop and make sure you have wireless enabled.

---

### Post by matixsf on 2010-05-28
connections enabled

---

### Post by matixsf on 2010-05-28
my computer is a dell dimension 3000 with a new internal hardrive, forgot the name but my original crashed so we got a new one from walmart or something and since ive had to use ubuntu and lost windows and all, Just trying to get itunes/ipod and my wifi to work

---

### Post by matixsf on 2010-05-29
?

---

### Post by Dareth on 2010-05-29
So your wireless was working before...?

To answer the iPod question, go to Applications->Sound & Video->Rhythmbox Music Player. Rhythmbox has support for the iPod. Connect it normally, wait for the iPod to appear on the desktop then double click on it. It will show you everything stored on it, including the music. The music files are most definitely renamed as nonsensical things (it's how the iPod encrypts data), but dump everything into your music folder anyway. Rhythmbox reads the song title, artist, etc. from the metadata, so it will appear with the correct information in the media player. Hope this helps.

---

### Post by Kirkland14 on 2010-05-29
for your wireless try hardwiring it first and then go to system>accessories>hardware drivers.  The broadcomm drivers should be visiblie. click and install.  after that you should be ok

Kevin

---

### Post by matixsf on 2010-05-29
i know this is going to sound dumb but what do you mean hardwiring it first? 


as for the rythmbox, thank you very much it is working!!

---

### Post by matixsf on 2010-05-29
Ok, So I got the IPOD and printer working fine but I am still having a hardtime with the wireless portion, I keep having to hook back up wired to get online and restarting the Computer. Anyways I went to the SYSTEM-ADMIN-HARDWARE DRIVERS, but I kneep getting "NO Proprietary Drivers are in use on this system"

---

### Post by ugm6hr on 2010-05-29
Have a look at the wifi help link below and post details in full here.

Most important is:
```
lshw -class network
```

---

### Post by matixsf on 2010-05-29
1. I was trying to use time warner modem connected to a wrt54g wireless router so I can play ps3 online but, I got nothing so I just went strictly wired online

2. Using a dell dimension 3000 with a new 500 GB wd internal HD, Time warner motorola modem SB5101, and a lynksys wrt54gs wireless router and ubuntu 10.04million or whatever its at now

3. Time warner in 'merica

4.newest version

5. If I go wired without wireless

6. previous statement

7.--- [www.opendns.com](www.opendns.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10672ms
rtt min/avg/max/mdev = 102.864/119.987/148.819/20.506 ms

8. I have no clue what that means or how to do it

9. just ubuntu nothing else installed

---

### Post by ugm6hr on 2010-05-30
You haven't actually given the output from the commands in Q2 or Q7.

It really is a lot easier if you just post the exact output from all the commands here, but at least:
```
lshw -class network
```

---

### Post by matixsf on 2010-05-30
*-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:13:20:07:07:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=174.106.101.93 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:feaff000-feafffff ioport:ddc0(size=64)

---

### Post by ugm6hr on 2010-05-30
There is no wifi listed there at all.

This generally means there is a hardware problem, or it is switched off at BIOS (or you have not pasted the entire output here).

Is the wifi card internal, or USB?

Also give us:
```
lspci
lsusb
```

---

### Post by matixsf on 2010-05-30
> **ugm6hr said:**
> There is no wifi listed there at all.

This generally means there is a hardware problem, or it is switched off at BIOS (or you have not pasted the entire output here).

Is the wifi card internal, or USB?

Also give us:
```
lspci
lsusb
```
internal:
lspci: 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by matixsf on 2010-05-30
lsusb:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 001 Device 004: ID 05ac:1293 Apple, Inc. 
Bus 001 Device 003: ID 04a9:1727 Canon, Inc. MX300 ser
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 I dont understand how it could have been turned off or maybe it did but how would I change it back? I really appreciate this, I have no clue whats going on

---

### Post by ugm6hr on 2010-05-30
No evidence of a wifi card on either list that I can see. If it is internal, it should be on lspci - unless the computer is a very cheap laptop (which sometimes have internal USB devices).

Wired card is this one - also referred to in lshw as "product: 82562EZ 10/100 Ethernet Controller"
```
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
```

Can you access your BIOS?  It is normally done by pressing Escape, F1, F10 or F12 from the first screen you see when you turn the computer on.  This is the only thing I can think of - else the wifi card has become unplugged, or it is broken.

---

### Post by matixsf on 2010-05-30
I could be wrong and this thing not have a wifi card, I knew I didnt have an external wifi card just the wireless router so I assumed it was internal

---

### Post by ugm6hr on 2010-05-30
Your options to confirm whether you have a wifi card:
1. Open the case and look inside for a wifi card - although most internal wifi cars still have an "external" aerial that sticks out of the back.

Otherwise, it is a fair bet you don't have one, or if you do, it is not working.

---

### Post by matixsf on 2010-05-30
Awesome, I really appreciate it, going to best buy later on and probably gonna buy one 20$ or so and then let you know how it is either tonight or tomorrow

---

### Post by ugm6hr on 2010-05-30
> **matixsf said:**
> Awesome, I really appreciate it, going to best buy later on and probably gonna buy one 20$ or so and then let you know how it is either tonight or tomorrow

If you are buying a card specifically for Ubuntu, be aware that some are not 100% Ubuntu friendly.

Generally, most PCI cards work fine, but not all.  USB cards are much less likely to behave.

If you have a choice, Intel, Atheros and now Broadcom cards behave well.  Be aware that some RT chipsets which are advertised as Linux-compatible, are actually less compatible with the newer kernels (as I have learned). Consider using google to find one that is suitable - just search for "10.04" or "lucid" and the name of the card in google.

---

### Post by matixsf on 2010-05-30
so call me a liar, wife threw a fit about this thing so we ended up leaving bestbuy, I have tried to look for the bios on the startup page and the only thing I see is the BIOS a02

---

### Post by nhasian on 2010-05-31
Did you buy a wireless adaptor from best buy?  if you have a desktop I strongly doubt that it came with wifi, you'd have to install one yourself.  I dont know what your setup is like, but if you can just use an ethernet cable it is much better than wifi anyway :lolflag:

---

### Post by adsrikanth on 2010-06-01
I had problems with connecting to a wireless network, so I disabled 'bluetooth' and then 'disabled networking and then re-enabled it'. It worked for me, in my case  bluetooth and wireless were conflicting, not sure why?

---

