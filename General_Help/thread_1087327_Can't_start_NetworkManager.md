---
title: "Can't start NetworkManager"
date: 2009-03-04
forum: General Help
---

### Post by larryma on 2009-03-04
I'm using Ubuntu 8.10 and setup a nice wireless network connection on a Dell Precision M60 laptop and Level One WPC-0300 wireless G PCMCIA card--until now.

After working beautifully for a few weeks, now there is no connection. When clicking on the NetworkManager Applet 0.7.0 icon, it says, "NetworkManager is not running."

I tried sudo /etc/init.d/networking restart. In the bash window it replies with the single line below, then the std bash prompt, as though nothing happened.
"* Reconfiguring network interfaces... [OK]"

Also tried /usr/bin/nm-applet, but says already taken.

Anyway, I think the applet is working because I can see and interact with the icon.

But how do I get NetworkManager to start and begin wireless networking again?

Larry

PS My cat has lately been sleeping on the keyboard, which has caused some problems by the keys she's pressed, but not sure this is the case here.

---

### Post by RedSingularity on 2009-03-04
I had the same problem but all i did is restart the comp.  How about reinstalling Network Manager?

---

### Post by larryma on 2009-03-04
Thanks, Shadow121! Yes, I tried restarting a number of times, no luck.

Reinstall sounds good. Can you, please, walk me through the process? 

Do I have to uninstall first? Is this done through command line or gui of some sort?

Larry

---

### Post by RedSingularity on 2009-03-04
System>Administration>Synaptic Package Manager.  Once there, in the search bar at the top enter "network".  You will see "network-manager-gnome" and "network manager".  Right click the green boxes and click reinstall.  Then hit the apply button at the top.

---

### Post by larryma on 2009-03-04
Thanks! Straight forward. Unfortunately, when I mark for reinstall and hit apply, it is looking to download from the internet--but I don't have internet!

How can I reinstall without internet connection? The files are not on the local drive? Are they on the Ubuntu install disk? Or can I download somehow to usb stick or cd then put in laptop?

Thanks. Sorry for the trouble.

Larry

---

### Post by RedSingularity on 2009-03-04
Check [HERE]("http://ubuntuforums.org/showthread.php?t=286445").  Its similar to your situation.  The fact that its for an older distribution of ubuntu should not matter.  Try it out.

EDIT:  Turns out a link for the download doesnt work.  We need to find a download of network manager and then you can use that guide.

---

### Post by RedSingularity on 2009-03-05
Try [HERE](http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.7/NetworkManager-0.7.0-rc1.tar.bz2) for the download.

---

### Post by RedSingularity on 2009-03-05
Ya know i was just thinking........you say you have the applet in the system tray in the panel?  Can you get a screenshot?  When you click it does it give an option for wireless or not at all?

What you can also do if all else fails is use an entirely different network manager called Wicd located [HERE](http://downloads.sourceforge.net/wicd/wicd_1.5.9_all.deb?use_mirror=internap).  When you go to install this it may say there is a conflict with the exsisting network manager.  Just go to the package manager like before and instead of right clicking "reinstall" click "completly remove" on the gnome-network-manager.  Then you can install Wicd.

---

### Post by larryma on 2009-03-05
I downloaded to usb, then to laptop and extracted to /tmp. However, these files vary from the example because they are not deb files, at least by name.

The extracted folder is called NetworkManager-0.7.0. I tried adding a line to the sources.list file: deb file:/tmp NetworkManager-0.7.0/ Error malformed.

Also tried deb file:/tmp/NetworkManager-0.7.0 In this case, apt-get ran, but many errors. Same with deb file:/tmp nm-debs/

Maybe I'm just not substituting from the example properly. Sorry.

Any suggestions?

Larry

---

### Post by larryma on 2009-03-05
I am enclosing some screen shots of the desktop to show what is visible in the original case.

Since the screen shots, I did install wicd and got connected. (which means I uninstalled gnome nm) I was able to download and extract network-manager-applet_0.7.0~~svn20081020t000444.orig.tar.gz 

But I don't know how to install this. Can I install with a package manager or do I have to do configure/make/etc?

wicd is not finding my PCMCIA wireless card, so I think I want to go back to gnome, unless someone disagrees.

Thanks in advance for the help!

Larry

---

### Post by RedSingularity on 2009-03-05
It seem you dont have the drivers for your wireless in the PC anymore.  Somehow they got deleted.  We need to get some info on your card to find the drivers.  Type "lspci" into terminal and post the output into the next post.

---

### Post by larryma on 2009-03-05
thanks. will post this aftn.
L

---

### Post by larryma on 2009-03-06
here is the output from the lspci command:

home@home-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX Go700 (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
03:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


Thanks for the help!
Larry

---

### Post by RedSingularity on 2009-03-06
You need wireless drivers located [HERE](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2).  Download to desktop, extract to desktop, then in terminal type "cd ~/Desktop/compat-wireless-2009-03-06".  Then type "make" and finally type "sudo make install".  When finished type "sudo make load".  Restart computer.

---

### Post by larryma on 2009-03-06
Shadow, didn't seem to work. Still doesn't see the PCMCIA card I don't think. However, I may have messed up the install: I rebooted before "sudo make load" After I realized the mistake, I ran the sudo make load command again, seemed happy, and I rebooted again. But no wireless.

I ran the lspci command as shown below. Hope you can help!

home@home-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX Go700 (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
03:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

---

### Post by RedSingularity on 2009-03-06
Ok, try [THESE](http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.bz2?use_mirror=voxel) drivers then.  

 Download to desktop, extract to desktop, then in terminal type "cd ~/Desktop/madwifi-0.9.4".  Then type "make".

---

### Post by larryma on 2009-03-07
Still not working. Perhaps all the information and history about this laptop is not available. First, using the standard install network manager (gnome?), I had no problem seeing or connecting to wireless networks. However, when the PCMCIA card from Level 1 was installed, the network manager had some trouble because two wireless devices were working at the same time, the PCMCIA and the internal wireless. The internal wireless is old (wireless b) while the PCMCIA is new (wireless g). My network is g, so I eventually found that I could turn on/off the internal card and solve the conflict through function F2 keystroke. So I had a fine connection until recently.

Perhaps I should reload the gnome wireless manager? I think you directed me to some files earlier, but I didn't know how to install them since I download the files onto a usb memory stick and then xfer to the laptop.

The other possibility I can think of is to reinstall the OS. Is there some way to do this without wiping the data I have on the laptop? 

I appreciate all the time you are spending on this. Thanks! Here is the latest lspci:

home@home-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX Go700 (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
03:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

Larry

---

### Post by RedSingularity on 2009-03-07
At this point i think your best bet would be to reinstall the OS (though i would like to try one more thing).  You said it was working at one point........

As for erasing data, what sort of data do you want to save?  Do you have other operating systems on there?  Or is it files in Ubuntu you want to save?

Oh and do you know the manufacturer/model of your PCMCIA card?  Maybe you can give me their website?

One more thing...post  "sudo lshw -c network" and "sudo cardctl"

---

### Post by larryma on 2009-03-07
I don't have any other os loaded and, on second thought, don't have anything too important otherwise, so reinstall is ok.

The PCMCIA card is WPC-0300 Level One by CP Technologies, url: cptechusa.com. I am posting the lshw command below. The cardctl command came back "command not found."

Larry

home@home-laptop:~$ sudo lshw -c network
[sudo] password for home: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:2b:97:db
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5705-v3.11 latency=32 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:50:ca:e0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
  *-network DISABLED
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:11:6b:62:1b:eb
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 66:14:98:97:0f:93
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by RedSingularity on 2009-03-07
Yeah i think you need the reinstall.  Look [HERE]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLevelOne").  As you can see your shipset should work just fine.  I cant figure out what went wrong.  If you want i can get someone else in here that may be able to help you out.  Or you can just do the reinstall.  Let me know.

---

### Post by larryma on 2009-03-07
Thanks. I'll do a reinstall and hope the problem is gone and does not reoccur. Will post back with reinstall results.

Larry

---

### Post by RedSingularity on 2009-03-07
Sounds good.  If it still does not work it will be easier to fix with a fresh install.

---

### Post by larryma on 2009-03-08
Shadow121,

I did the clean reinstall and now everything works fine. Not sure what the problem was before, but if it reoccurs, I will write in.

Thank-you for all your help! I appreciate your time.

Larry

---

### Post by RedSingularity on 2009-03-08
No problem buddy :)

---

