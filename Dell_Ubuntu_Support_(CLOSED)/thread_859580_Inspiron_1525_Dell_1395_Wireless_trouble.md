---
title: "Inspiron 1525 Dell 1395 Wireless trouble"
date: 2008-07-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jfrantziv on 2008-07-14
I just dual-booted with ubuntu and vista, and i'm having trouble with my wireless card. i'm very new to linux altogether, so bear with me...

when i use the terminal and insert:

[sudo apt - remove ndisgtk ndiswrapper - common ndiswrapper - utils - 1.9] 

i get the response:

[E:couldn't find package ndisgtk]

My System/Admin/Hardware Drivers shows a "wl" enabled but not in use. I don't know what to do to make that thing be in use!

Help!

---

### Post by falcon61102 on 2008-07-15
If you could, go into your terminal and run the following commands, then post the output here.
```
lspci
```
and
```
lshw -C network
```

That will give us some background on your machine so we can start helping.

---

### Post by maxubu on 2008-07-16
Here is what i get on my Dell Inspiron 9400:

lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
max@stromboli:~/bin$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:f2:07:ea
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.104 latency=64 module=ssb multicast=yes

Are there any links we should look at to resolve this problem?

---

### Post by falcon61102 on 2008-07-16
Yeah... There are plenty of links.  I have a similar card and after pouring through a bunch of links I was able to piece together a process that works pretty well.  I'll copy it on here and included in it are the links that I got my info from so you can use those as reference.  As a note: I made this up for someone how had already installed ndiswrapper once, if you haven't done that, then ignore any errors about ndiswrapper not being present as you will install it towards the middle of the walk through.  Also, in the first series of code, if you get erros, just keep going.  That section is to make sure you shut down any running modules but if you don't have them running, they return errors.  Any questions or errors, just post and I'll help you out.  

Ok... This is going to be a compilation of two HowTo's:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

If you have a wired connection in Ubuntu, use it and you can copy the download links directly, otherwise you'll have to download them seperately and use a flash drive or shared drive that Ubuntu can access.  Either way it will work, but having a wired connection makes it go a lot faster.

The first thing we want to do is stop ndiswrapper and the other modules from running:
```
sudo rmmod ndiswrapper
sudo rmmod b44
sudo rmmod b43
sudo rmmod b43legacy
sudo rmmod ssb
```

Now that we don't have any modules loaded in the kernal we can remove the old ones and install the new ones.  

First we want to blacklist the drivers we don't want to run.  To do this we need to edit the blacklist.
```
sudo gedit /etc/modprobe.d/blacklist
```

If it's not already listed you want to add the following entries:
```
blacklist bcm43xx
blacklist ssb
```
Save and Close the File.

Since you have tried installing previous drivers and it didn't work, we want to start with a clean slate.  

To Unistall your current drivers:
```
sudo ndiswrapper -r bcmwl5
```

To remove ndiswrapper:
```
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
```

REBOOT

Now it's time for a fresh install.
```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
mkdir -p ~/bcm43xx/ndiswrapper; cd ~/bcm43xx/ndiswrapper
sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz -Ondiswrapper.tar.gz
tar xvzf ndiswrapper.tar.gz
cd ndiswrapper*
make distclean
make
sudo make install
```

This is going to download the newest version of ndiswrapper and extract it to a folder in your Home directory.  It is then going to make the install to use.

Now it's time to download the correct drivers for your card.  Based on lspci you have a Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) so you need the following drivers:
```
 cd ~/bcm43xx
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
unzip R174291-pruned.zip
```

That will download and unzip the drivers into the bcm43xx folder in you Home folder.

To reinstall the drivers using ndiswrapper you should be able to copy and paste this:
```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Once that completes the new drivers should be installed.  You may see your Wireless access points listed now.  If so, you're good to go.  Based on experience with that card, you're gonig to have to use the Hardy Bug Fix though.  To test this run:
```
sudo lshw -C network
```

Under the section for your wireless card you should see a line towards the bottom that contains Module=  If that says Module=ssb then you need the bug fix:
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44
```

Try that sequence first, see if you can see the wireless access points in under "Wireless Networks" and run:
```
sudo lshw -C network
```
To see if it still says Module=ssb.  If you can access the net and you no longer see Module=ssb then you got it, if not skip this next step and go down below.  To ensure that your system loads these settings at boot use the following:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```


If the above settings didn't work, go through the above bug fix again, this time stopping once you reach:
```
sudo modprobe ndiswrapper
```
And then try to access your wireless.  You should now have access if the above didn't work.  Again you are going to want to ensure these load up at each boot so run:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```

You should now be able to get online.  I hope so anyway... :)

Like I said in the beginning, this is a compilation of:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

And all credit due for figuring all this out goes to the orinal writers (can't find their names).

---

### Post by unutbu on 2008-07-16
Thank you for the very clear instructions, falcon61102.
However, I'm litte confused here:

```
cd ~/bcm43xx
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
unzip R174291-pruned.zip
```

Was this supposed to be

```
cd ~/bcm43xx
sudo apt-get install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
```

---

### Post by falcon61102 on 2008-07-16
Oopss... yeah, it was... my edit job was a little too quick... thanks.  How's everything else look?

---

### Post by unutbu on 2008-07-16
It looks good to me, though I don't have this NIC, so I can't say for sure... Nevertheless, many thanks.

---

### Post by falcon61102 on 2008-07-16
Thanks... Just trying to help out where I can.

---

### Post by stats on 2008-07-21
just goto System/Admin/Hardware Drivers uncheck it, and check it again. it should change to in use.
to make the change permanent add "wl" to the end of /etc/modules file

---

### Post by hyperknox on 2008-09-01
Hello everyone. I'm having similar problems trying to use my wireless card. The weirdest thing is, in System -> Admin -> Hardware Drivers, wl is "enabled" and "in use". 
I'm running UbuntuStudio, kernel 2.6.24-19-rt on a Dell Inspiron 1525 and I'm a total noob. 
I tried to follow the instructions given to maxubu, but the thing is I don't get module=ssb and module b43 is not installed. 

Any hints? Thanks in advance.

--------------------------------------------
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
------------------------------
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:47:6c:3b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.32.168 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:b9:66:49
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
------------------------------------

---

### Post by falcon61102 on 2008-09-01
Welcome.

As far as the fix that stats recommended, I really don't have any idea if that works, but if you go through the walkthrough I posted above you shouldn't have any problems.  If you decide to go that route, go back and undo any changes that you've done up to this point, it will make thigs easier in the long run.  If you have any questions or get any errors, just keep posting here and we'll help you out.

---

### Post by hyperknox on 2008-09-01
I actually got it working. Following this tutorial
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I realised I had installed the wrong Windows Driver (it was very similar, though). The best way to do it is using ndisgtk. 

Once I solved that problem, all I had to do was to uncheck and re-check the device driver in system -> admin -> hardware drivers, install ndiswrapper and configure its graphical frontend. 
The last and crucial step (i was about to give up) was to deactivate my wired connection.

---

### Post by falcon61102 on 2008-09-01
Glad you got it working.

---

### Post by RandomUser46 on 2008-09-15
I just don't get it for some reason... I've gotten everything else working, but the driver doesn't say "In Use", and I can't see a wireless connection option for my laptop. Agh.

I've got a Dell Inspiron 1525 with the Wireless 1395 card like the other folks here, but one thing I noticed when I checked the config on Ubuntu was that it wasn't just *network, it was *network-unclaimed or something like that.

Anybody have an idea what's going wrong, or should I post more stats/info? Thanks in advance!

---

### Post by neymac on 2008-09-17
See this [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")
and this
[http://vladgh.com/2008/05/31/dell-wireless-1395-card-and-ubuntu-hardy-heron/]("http://vladgh.com/2008/05/31/dell-wireless-1395-card-and-ubuntu-hardy-heron/")

---

