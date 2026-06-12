---
title: "A couple questions"
date: 2005-09-01
forum: Desktop Environments
---

### Post by Jordan Meeter on 2005-09-01
1) How do I change my hostname?

2) How do I configure Ubuntu to play sound?

Thanks!

---

### Post by plb on 2005-09-01
for hostname edit /etc/hostname

sound config there is a guide on the wiki or ubuntuguide site I'm sure

---

### Post by Jordan Meeter on 2005-09-01
I'm sorry, you're dealing with a first class nub. I literally installed Ubuntu no more than an hour ago. You'll have to be a little more in-depth that that. =\

---

### Post by Wolki on 2005-09-01
[QUOTE=Jordan Meeter]1) How do I change my hostname?

2) How do I configure Ubuntu to play sound?

Thanks![/QUOTE]

1) open a terminal. type "sudo gedit /etc/hostname". In the file that opens, replace the word with the hostname you want to use.

2) ubuntu should do that automatically. If it doesn't it usually means something is wrong, We need more information to help you then, like the sound card you're using. This problem may be easy to fix, but a few sound cards are difficult/impossible because there are no drivers.

---

### Post by Jordan Meeter on 2005-09-01
Awesome, thank you. I got the first part.

Now, onto the second part. What is the best way to find out what soundcard I'm using?

---

### Post by plb on 2005-09-01
[QUOTE=][/QUOTE]
 from a terminal lspci might help you out ;]

---

### Post by Jordan Meeter on 2005-09-01
Here is what I got back:> 0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Re gisters (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process  Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graph ics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Dev ice (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Contro ller (rev 03)
**0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4 -L/ICH4-M) AC'97 Audio Controller (rev 03)**
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem  Controller (rev 03)
0000:01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000  Controller (PHY/Link)
0000:01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controlle r
0000:01:06.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01 )
0000:01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless  LAN Controller (rev 03)

I bolded the part that I thought might be useful, but I have no idea.

---

### Post by Jordan Meeter on 2005-09-02
Help? =\

---

### Post by plb on 2005-09-02
hm I _believe_ the module for that is snd_intel8x0 although I could be wrong. To be honest I don't use ubuntu much its on one of my machines but my primary machine is a debian box. Ubuntu correctly detected my sound upon installation so I never had to tinker with it. On my debian box however I just installed alsa-base then from a terminal ran alsaconf which correctly detected and setup my sound card then did a alsactl store to save my setting maybe this will work for you. Although I'm sure before you want to resort to this you may want to follow the sound guide for ubuntu. And as a last resort you can always roll your own kernel. The command lsmod might also be of some help you to it should tell you if the snd module is loaded or not

---

### Post by az on 2005-09-02
Okay, you can change your hostname in the networking GUI by clicking on a tab.  (System - Administration- Networking)

The intelx810 sound module is blacklisted by default because it caused some hardware problems.  This may not be the case for you, but you need to take it off the blacklist

You need to use the commandline for that

sudo gedit

and open the /etc/hotplug/blacklist file.  Comment out the line with the intelx810 sound module name in it (put a "#" in front of it).  It is the last line in the file, I think.

then reboot.


You can also just run

sudo /etc/init.d/hotplug restart

but rebooting is simpler.

---

### Post by Jordan Meeter on 2005-09-02
Okay, on the last line, I put # before 'snd_intel8x0m".

Also, after I changed my hostname, I've been getting errors, namely> sudo: unable to lookup jordan-ubuntu via gethostbyname()

(gedit:8680): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

[Edit] Also, when I go to System > Administration > Networking it just says "Starting Networking..." in the taskbar and then just disappears. :???:

---

