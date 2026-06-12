---
title: "Dell Wireless-N 1520 freezes on Karmic"
date: 2010-03-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by capitalm on 2010-03-04
Hi,

I own a Studio 1458 with Dell Wireless-N 1520 (Broadcom BCM4353)

The driver worked fine at first, but stops working after a few minutes. There is no warning of any sort, it simply cannot connect. After another few minutes, the system freezes. During the first reboot, the speaker beeps 1,2,3,4. I have to reboot again to get it working.

I tried both the supplied STA driver and the one supplied on Broadcom website [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php). Doesn't make any difference.

lspci
```
00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Arrandale PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
05:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
ff:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

```

Any ideas?

---

### Post by chris00 on 2010-05-08
Same problem here too, brand new Dell Studio 1558 with the following network hardware...

eth1: Broadcom BCM4353 802.11 Hybrid Wireless Controller 5.60.48.36

Usually it will connect to the network after a reboot but will then lose connection in the not too distant future. Sometimes it will be just a few minutes before it is lost, other times maybe a few hours.

It wouldn't be too bad if it would automatically reconnect, but even though the connection is set to do this it still asks for the password every time.

Any help would be much appreciated.

Thanks,
Chris

---

### Post by simon_w on 2010-05-08
Hmm, I have a new Studio 1458 with, I presume, the same wireless hardware, but I haven't experienced any problems.  I'm away from that machine right now, but when I get back to it (probably tomorrow) I'll check and confirm that it is the same.

As far as I remember, I've been using the Broadcom binary drivers as installed by the Restricted Drivers manager.

---

### Post by chris00 on 2010-05-09
Just FI, I am also using the Broadcom STA proprietary wireless driver.

---

### Post by sheik.yerbouti on 2010-05-09
Same problem here with Lucid LTS 10.04. Using Broadcom proprietary drivers as well. Is the problem with Broadcom?

Perhaps some useful information here [http://ubuntuforums.org/showthread.php?t=1398426:](http://ubuntuforums.org/showthread.php?t=1398426:)

Here is how to get the Broadcom  BCM4353 card to work :

Do not install any proprietary drivers when prompted. Remove the bcmwl-kernel-source package if it is installed.

Download the appropriate driver (for x86 or x64) from here : [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Follow the instructions in README.txt.

Note : In instruction 4 in README, you will need root's privilege to execute modprobe and insmod. You can issue sudo.

However, you have to load the module (issue modprobe and insmod) every time you boot. You may write a shell script and set it to execute at every boot.

---

### Post by simon_w on 2010-05-09
I can confirm that I'm using a Broadcom BCM4353 device under Lucid (10.04 LTS - 64bit version, which *might* be relevant).  I'm using the binary STA driver from Broadcom as installed by the Restricted Drivers manager.  I have had no problems whatsoever up to now.  No dropouts, no sluggishness, no failure to connect.

@sheik.yerbouti - have you tried those steps yourself?  I can't see how it would make any difference at all, since the version of the driver you link to is *exactly* the same as the one in the bcmwl-kernel-source package in Lucid.  If you're still running Karmic it's probably worth upgrading to the driver on that page, but if you're running Lucid don't bother - it won't help.

To those still having problems with the latest driver (either supplied by Lucid or from the Broadcom site), it would be good to see some more information.  In particular, to know which kernel you are running (post `uname -a`), and then look for relevant information in `/var/log/syslog` and/or `/var/log/messages` and '/var/log/dmesg` when the wireless drop out.  (you can use 'System -> Administration -> Log File Viewer' for convenience).

I'm by no means the last word on these things, but I'll help as much as I can.

simon

---

### Post by OooBuntuRox on 2010-05-10
[SIZE=2]I have the 1545/ 15n. It has a broadcom card and uses the sts driver. When I last did a reinstall using 9.10 iso I had a problem. I'm not if this was coincidence or if will help you but my card stopped responding. I thought it was dead. Then I remembered the keyboard shortcut [Fn]-[F2] that can be used to toggle the wifi on and off. Sure enough, the card started working. It's been just fine ever since. I have no idea what or how the wifi card toggled off.

My 15n came with 8.10. I upgraded to 9.04. I liked 9.04 better than 9.10. I stayed with 9.04 until 10.04 came out. I have only been using 10.04 (64 bit) a few days actually. I love it except for one thing. I have an intermittent system freeze during boot. The desktop appears and just before the upper/ lower panels load, the system freezes. All I get is a blank desktop background.

I have to [ctrl]-[alt]-[del] to reboot. Then it boots fine the next time.

One plus for me in 10.04, My sound works fantastic. In earlier versions you could barely hear it when it was turned ALL the way up. Now it can play louder than the internal speaker can comfortably handle.

Hope this helps, OooBuntuRo[/SIZE]x:guitar:

---

### Post by shiningkenmonster on 2010-05-11
hello. I have a dell mini 10v. I used to have the dell wireless N card of 1520. its a half mini card.

upon installing the karmic koala a while back ago. I installed the STA Broadcom drivers. 

I had the same problem. It would freeze up, not work sometimes, download speeds would be extremely slow. 

i used to have a dell mini 9. and that machine works super fast on my home internet.

something was weird on the dell.com website. they didn't offer the dell-wireless-n 1520 card for my dell mini 10v anymore. It used to say its not supported for linux. 

I called dell and complained. they said since i was still under the 1 year warranty. they sent me the old wifi model card. which is the Dell Wireless 802.11g (1397) Mini Card. I opened my dell mini 10v baby up. unscrewed it and took out the two ports/plugs. than i installed the older model of the mini card. put in the plugs and closed it up.

when i did a fresh reinstall. and installed the STA Broadcom drivers. The wifi issue disappear. The internet speed just as fast as my other machine. no wanting to connect when it doesn't want to.

the wifi issue with the dell wireless-n 1520 happens with the Canonical version of Ubuntu. When you use Dell's version of Ubuntu. the wireless-n-1520 wifi works fine with it.

---

### Post by sagyvolkov on 2010-05-12
shiningkenmonster, what is the "Dell version of Ubuntu"?
you can only buy older laptops with Ubuntu from Dell, and these don't carry 1520s at all.
Can you please elaborate how you got this version and if you now have no issues at all with the 1520?

Thanks.

---

### Post by sheik.yerbouti on 2010-05-12
OK, I got mine working in Lucid 10.04 LTS at 100%. Here are the steps I followed:

1. Download and copy the Dell wireless driver [R239087.exe] to the Ubuntu desktop. Extract to its own directory.

2. From Synaptic Package Manager, install ‘ndisgtk’ in Ubuntu.

3. Open System > Administration > Windows Wireless (this is the Ndiswrapper driver installation tool created by ‘ndisgtk’).

4. Select ‘Install New Driver’ by pointing to the appropriate .inf file in the directory where the drivers were extracted.

5. Open System > Administration > Hardware Drivers to install and activate the Broadcom BR43 proprietary driver.

6. Using Synaptic Package Manager, install Wicd. (I know, Wicd is not required, but it is *so* much better than network manager.)

7. Make sure the network cable is unplugged. Sometimes my copy of Ubuntu will refuse to connect to wireless if a wired connection is present. Reboot.

8. Wicd will scan for wireless networks. If your network is hidden (mine is) right-click on the network button to scan and select <hidden> and you will be prompted for connection information.

NOTE: The only Dell driver I found was for 64-bit Win7. I'm running 64-bit Ubuntu and had no problem. Query whether the 64-bit Win7 driver would choke in 32-bit Ubuntu? I do not know whether all these steps are required, but I performed these steps in this order and it worked.

---

### Post by OooBuntuRox on 2010-05-13
[SIZE=3]> **sagyvolkov said:**
> shiningkenmonster, what is the "Dell version of Ubuntu"?
you can only buy older laptops with Ubuntu from Dell, and these don't carry 1520s at all.
Can you please elaborate how you got this version and if you now have no issues at all with the 1520?

Thanks.[/SIZE] [SIZE=3]

Follow these links and poke around:

[http://linux.dell.com/files/ubuntu/](http://linux.dell.com/files/ubuntu/)

[http://linux.dell.com/files/ubuntu/lucid/iso-images/](http://linux.dell.com/files/ubuntu/lucid/iso-images/)

[http://en.community.dell.com/support-forums/software-os/w/linux/ubuntu-9-04-dell-factory-recovery-iso.aspx](http://en.community.dell.com/support-forums/software-os/w/linux/ubuntu-9-04-dell-factory-recovery-iso.aspx)

[http://en.community.dell.com/support-forums/software-os/w/linux/ubuntu-8-04-dell-factory-recovery-iso.aspx](http://en.community.dell.com/support-forums/software-os/w/linux/ubuntu-8-04-dell-factory-recovery-iso.aspx)

Good Luck, OoobuntuRox :guitar:

[/SIZE]

---

