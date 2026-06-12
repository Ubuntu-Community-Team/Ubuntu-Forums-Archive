---
title: "Dell Servers question"
date: 2007-11-23
forum: Dell  Ubuntu Support
---

### Post by xeo_pt on 2007-11-23
I'm thinking of installing Dell serves,r the SC and T series,
my question is: are the network and the RAID controllers compatibly with Ubuntu?
I now they certify RH and Suse.

Thanks in advance.

---

### Post by defishguy on 2007-11-23
If you have access to the actual hardware specs (the who made it and what the model is type) please post them here and we can be a lot more help to you.

---

### Post by xeo_pt on 2007-12-05
> **defishguy said:**
> If you have access to the actual hardware specs (the who made it and what the model is type) please post them here and we can be a lot more help to you.

Thanks for your answer I'm wait for three! Dell server
and will install Ubunutu, then I will post the problems :p:p

---

### Post by sr20ve on 2007-12-05
> **xeo_pt said:**
> Thanks for your answer I'm wait for three! Dell server
and will install Ubunutu, then I will post the problems :p:p

So which models did you order?

---

### Post by xeo_pt on 2007-12-06
> **sr20ve said:**
> So which models did you order?

1 SC 440
1 T105
1 PE860

They will be use for different purposes, the PE860 will be a Asterisk server.

I'm looking forward to get then because it's the first time I buy Dell, witch is not a common brand around here and to know if they work with Ubunut.

---

### Post by xeo_pt on 2007-12-16
The first as arrived it's a T105:
[http://www1.euro.dell.com/content/products/productdetails.aspx/pedge_t105?c=pt&cs=RC1078554&l=pt&s=pad](http://www1.euro.dell.com/content/products/productdetails.aspx/pedge_t105?c=pt&cs=RC1078554&l=pt&s=pad)

the only difference from the standard model is a board with two 1Gb NICs.
Ubuntu 7.10 boot without problems and find the 3 NICs and the RAID 1 array. =D> 
the output of lspci is:
> 00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f1)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express
04:00.0 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (rev 06)
04:00.1 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (rev 06)
05:00.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1068E PCI-Express Fusion-MPT SAS (rev 0 8)

The system is installed and works fine!

---

### Post by tercel04 on 2008-02-23
I have been struggling with T-105 for a while now.
the 32 bit 7.10 Desktop works no problems.
But the  x86_64 live CD wont boot up at all. It hangs ...and i have no access to logs or anything. Thus far i did not get any where with the 64bit desktop ubuntu. 
Did you guys install the server version or alternate version og x86_64

FYI...
64 bit RHEL and CentOS 4.6 install no problems. (They dont recognize the network card - it needs to be installed with the drivers on dell CD)


ALso Failed
64 bit Cent OS 5.1 fails to recognize the presence of CD rom (it does the isolinux fine )
Fedora 8 and 9 DVDs...
Conclusion: DVDs dont work(??)

---

### Post by xeo_pt on 2008-02-24
I have a T-105 with 7.10 and it works great.
I think it as the 64 bit version but I will check this week and post here.

---

### Post by ChaosParser on 2008-02-24
If Dell has drivers for RedHat, (.rpm)s then you can MAKE it work with ubuntu.  All drivers can be converted from .rpm to .deb via Alien. 

[http://www.howtoforge.com/converting_rpm_to_deb_with_alien](http://www.howtoforge.com/converting_rpm_to_deb_with_alien)

---

### Post by tercel04 on 2008-02-24
32 bit ubuntu has no problems recognizing the devices on T105.
As for 64 bit....I havent been able to load the live CD...so i cant say if it does.

Infact RHEL had problems detecting the ethernet. But the rpm on the cd takes care of it.

I am going to try installing the Ubuntu 64 bit server CD ...I will post my findings

---

### Post by tercel04 on 2008-02-24
Ok...I tried to install the ubuntu-7.10-server-amd64 and it craped out.
It couldnt recognise the disk in the cdrom drive.(this is after it booted off the same cd and i selected option to install)

---

### Post by blkno1 on 2008-04-02
I just received a brandy new T105 and am having this same problem with the ubuntu-7.10-server-amd64 DVD not being seen.  Anyone find a work around for this. :confused:

---

### Post by xeo_pt on 2008-04-02
What version do you install?
x64 or x86?

---

### Post by blkno1 on 2008-04-02
been trying the x64 one.

---

### Post by xeo_pt on 2008-04-02
> **blkno1 said:**
> been trying the x64 one.

try the x86

---

### Post by drr104 on 2008-04-03
Have you tried the AMD64-server 8.04 beta on the T105? Since there seems to be a problem with Centos 5.1 (x64) also, perhaps this has been fixed in the newer kernel. Thats just a guess, but since 8.04 is LTS and released soon it might be worth trying.

(I'm going to be getting the same machine shortly and am hoping to run a 64-bit OS on it, so I'll try 8.04 when I get it)

---

### Post by blkno1 on 2008-04-04
yeah the 8.04 BETA was a no go.  Couldnt see the DVD.  Not one i86_64 distro i could grab worked.  I threw Gutsy Server on it for now, runnin slick.

---

### Post by flippbonq on 2008-04-07
> **blkno1 said:**
> yeah the 8.04 BETA was a no go.  Couldnt see the DVD.  Not one i86_64 distro i could grab worked.  I threw Gutsy Server on it for now, runnin slick.

i was able to get 8.04 beta installed on my t105 using a usb stick [#]("http://bonq.net/flipp/2008/04/03/dell-poweredge-t105-ubuntu-usb-drive-install/").   i just followed this guide : [http://edoceo.com/liber/ubuntu-live-usb](http://edoceo.com/liber/ubuntu-live-usb)

one thing i didn't try but should have was to rerun the 8.04 alternatives install with  [unetbooting]("http://lubi.sourceforge.net/unetbootin.html"), once i had done the original install from a live-cd on a usb stick. 

i have a 600gb software raid (3x300gb drives) running on the t105 now also. i'm definitely happy with how quiet the server is.... i might pick up another one if they go back on sale for $250-ish anytime soon.

---

### Post by drr104 on 2008-04-08
I was going to suggest doing a network install (I assume thats possible with Ubuntu); I was able to get Centos 5.1 64bit installed by using the netinstall iso and downloading the rest. Everything seems to work fine.

I was very surprised by how quiet it is! Its a shame you can only fit two hdds though.

Also, $250?! Dell list the T105 as £99 ex VAT, so once you've added VAT and p&p its about £174 (~$343) :(

---

### Post by flippbonq on 2008-04-08
> **drr104 said:**
> 
I was very surprised by how quiet it is! Its a shame you can only fit two hdds though.

i used a 5.25->3.5 adapter for a 3rd harddrive and put the 4th harddrive where the floppy would have gone. i was just happy that the bios saw 4 hdds because the system docs lead me to believe that only 2 of the sata ports were active.

---

### Post by drr104 on 2008-04-09
> **flippbonq said:**
> i used a 5.25->3.5 adapter for a 3rd harddrive and put the 4th harddrive where the floppy would have gone. i was just happy that the bios saw 4 hdds because the system docs lead me to believe that only 2 of the sata ports were active.

Ah, hadn't thought of that... I assume theres no issue with the temperature of those drives? Can't see that there would be, but it doesn't seem like it was really designed for four HDDs.

Also, does lmsensors work on Ubuntu? I dont think any sensors were found when I tried it on Centos 5.1, would be nice to be able to monitor the temperatures.

---

### Post by flippbonq on 2008-04-09
i haven't had any issues w/ temps so far... the 5.25 adapter i used needs to be replaced with a different one, right now i can hear a little bit of disk noise/vibration on heavy i/o but it's not annoying so it's not an issue.

i just did an apt-get lm-sensors and sensors now reports :
[INDENT]$ sensors -f
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +98.6°F                                    
Core1 Temp:  +87.8°F  [/INDENT]

let me know if you want my sensors.conf file to try under centos. here's the modules that i2c/lmsensors currently has loaded on my system
[indent]
$ lsmod | grep i2c
i2c_algo_bit            8452  1 ivtv
i2c_nforce2             8704  0 
i2c_core               28544  12 wm8775,cx25840,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,ivtv,i2c_algo_bit,tveeprom,i2c_nforce2
[/indent]

(there's a pvr500 in the box, that's where the ivtv modules are coming from)

---

