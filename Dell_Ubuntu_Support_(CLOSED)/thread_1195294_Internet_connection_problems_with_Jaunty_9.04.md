---
title: "Internet connection problems with Jaunty 9.04"
date: 2009-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hipowershooter on 2009-06-23
Bear with me as I am a NOOB to Ubuntu, but previously worked extensively with UNIX (1989-1996), so there I may be a bit rusty.

I recently acquired a Dell Inspiron 700m with Ubuntu 8.10 installed by the previous owner. I used it without issue for several weeks, and took the plunge and installed 9.04. The installation went without issue, and I thought I was going to be very happy, until I turned it back on again. 

Since then  Network Manager would show a good connection, for either wired or wireless, but I could not connect to Internet via wire, and wireless was at best a maybe. I searched the forums and over and over again read about issues with networking and 9.04.  I downloaded and made an ISO disk of 8.10, did a new install and have not looked back. My question is  this: Is this a known issue with 9.04, and if so, when will there be a definitive fix? What I could see lead me to believe it was not hardware specific, though it maybe. The posts I did read seemed to make it look like it could affect just about any make or model hardware, but was pretty much associated with 9.04.

---

### Post by pytheas22 on 2009-06-23
I would suspect that the issue is hardware specific, although given that it affects both wired and wireless, I'm wondering if it may just be a bug with NetworkManager (in that case, you should be able to use an alternative connection manager like [wicd]("http://wicd.sourceforge.net") with no problem).  If you could please post the output of the following commands in the terminal, we'll know exactly which network devices you have:
```

lspci -nn
lshw -C Network
```

If you could post a link to some of the other posts you were reading that suggest this is a non-hardware specific issue in 9.04, that would be helpful as well.  I hadn't heard of anything like that.

---

### Post by ernits on 2009-07-08
Hi there!

I'm also facing the problem with the internet connection with Ubuntu 9.04. It drops from 2-5min.

As asked, here are the outputs,

[COLOR="Red"]lspci -nn

00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
05:03.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
05:04.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
05:04.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 01)
05:04.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
05:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)[/COLOR]

[COLOR="Red"] lshw -C Network

WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:05:03.0
       logical name: wmaster0
       version: 01
       serial: 00:c0:a8:d6:01:fc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=10.28.27.173 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:62:6d:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:5c:db:d2:d5:3c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
[/COLOR]
[COLOR="Black"]
I also tried wicd, it increased the connection time but it still dropped. I noticed that wicd has no VPN connection, is it correct? That's necessary for me, so the change for wicd wouldn't be an option without VPN connection.

I would appreaciate if you could help me to solve this...! :)[/COLOR]

Thanks!

---

### Post by pytheas22 on 2009-07-08
ernits: I would suspect a problem with your wireless driver.  Things may work better if you compile a more recent version of the driver from source.  To do that, first go to [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/) and download the file named compat-wireless-2.6.tar.bz2.  Save it to your desktop.  Then run these commands:
```

sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

Then reboot and try the wireless again.  Is it any better?

---

### Post by venkyms on 2009-07-10
Hi,

I had the same problem connecting to wireless network, and updated the latest one, but didnt help me in connecting instead my system freezes

regards
venkat

---

### Post by pytheas22 on 2009-07-10
venkyms: I'm not sure what you mean.  Did you recompile your wireless driver using the instructions in this thread?  Or did you upgrade Ubuntu or something?  What was the problem originally--did your wireless fail to connect at all, or did you have the same problem as the other posters in this thread, where the connection dropped after a few minutes?

I also don't know which hardware you have; I would need to see the output of these commands to know that:
```

lspci -nn
lshw -C Network
```

---

### Post by venkyms on 2009-07-10
Hi pytheas22

I installed Ubuntu 9.04 64bit, then did all the updates
sudo apt-get update

then tried.. connecting to the wireles.. , i was able to see the signal level, but never getting connected when i try so followed the command to recompile the latest from the website u mentioned. Then also i was not able to connect.

will post the hardware info soon, i am in office now :)

Thanks for the response

Regards
venkat

---

### Post by venkyms on 2009-07-10
Hi pytheas22

here is my hardware information

[COLOR="Red"]venkat@venkyms:~$ lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation MCP79 Host Bridge [10de:0a82] (rev b1)
00:00.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a88] (rev b1)
00:03.0 ISA bridge [0601]: nVidia Corporation MCP79 LPC Bridge [10de:0aae] (rev b2)
00:03.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0aa4] (rev b1)
00:03.2 SMBus [0c05]: nVidia Corporation MCP79 SMBus [10de:0aa2] (rev b1)
00:03.3 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a89] (rev b1)
00:03.5 Co-processor [0b40]: nVidia Corporation MCP79 Co-processor [10de:0aa3] (rev b1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa5] (rev b1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa6] (rev b1)
00:06.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa7] (rev b1)
00:06.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa9] (rev b1)
00:08.0 Audio device [0403]: nVidia Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Bridge [10de:0aab] (rev b1)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
00:0b.0 SATA controller [0106]: nVidia Corporation MCP79 AHCI Controller [10de:0ab9] (rev b1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac4] (rev b1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0aa0] (rev b1)
00:15.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac6] (rev b1)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
00:17.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
00:18.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
01:07.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
01:07.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
01:07.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
01:07.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
01:07.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
02:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 9200M GS [10de:06e8] (rev a1)
03:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 9400M G [10de:0866] (rev b1)
06:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
venkat@venkyms:~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:19:df:88:36
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:5f:62:2c:ef
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0e:f9:2f:70:26:98
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
venkat@venkyms:~$ 
[/COLOR]

help me to fix this issue

---

### Post by 0pul3nce on 2009-07-10
[COLOR=Red][COLOR=Black]You say "[/COLOR][/COLOR]could not connect to Internet via wire" [COLOR=Red][COLOR=Black]That's confusing[/COLOR]
[/COLOR][COLOR=Red][/COLOR][COLOR=Red][/COLOR]
Let me clarify 
The Ethernet works in your network manager.
However you have no connection to the internet. *do other computers on the network?

[COLOR=Red][COLOR=Black]I'm using 64 bit have an Ethernet of 32 width, my product is [/COLOR][/COLOR]MCP67 Ethernet.

---

### Post by pytheas22 on 2009-07-11
venkyms: so you see the wireless network in NetworkManager, but when you click to connect, it does not succeed?  Does it work if you disable security on your router?

You may also have better luck using [wicd]("http://wicd.sourceforge.net"), an alternative to NetworkManager.  You can install wicd in Ubuntu 9.04 by typing:
```

sudo apt-get install wicd
```

Then launch it form the Applications>Internet menu.  Does it work any better?

---

### Post by ernits on 2009-07-12
Hi Pytheas22,

thank you very much for the input! 

i'm still testing it but it seems much better!  :guitar:

---

### Post by ernits on 2009-07-12
Hi there!
Unfortunately the problem persists... that's why I'm reviewing the thread... sorry.

Yesterday I tested the solution for about 3 hours, and in comparison with the previous situation it increased the connection time.

Today I came back testing, and stayed all day working with the connection dropping with different time intervals.

I confirmed with colleagues using the same wireless and everything is ok with their connections.

I tried WICD...but with no lucky, it connects but doesn't allow me to use firefox (stays offline). I also tried WICD with another browser, Epiphany and it didn't work. There's no proxy, just as info.

Any other suggestion?

---

### Post by ernits on 2009-07-13
Hi there! 
Unfortunately the problem persists... that's why I'm reviewing the thread... sorry.

Yesterday I tested the solution for about 3 hours, and in comparison with the previous situation it increased the connection time.

Today I came back testing, and stayed all day working with the connection dropping with different time intervals. 

I confirmed with colleagues using the same wireless and everything is ok with their connections.

I tried WICD...but with no lucky, it connects but doesn't allow me to use firefox (stays offline). I also tried WICD with another browser, Epiphany and it didn't work. There's no proxy, just as info.

Any other suggestion? :)

---

### Post by pytheas22 on 2009-07-13
ernits: sorry to hear you're still having trouble.  My next suggestion would be to install ndiswrapper, which will drive the card using Windows drivers.  ndiswrapper provides fewer features but might be more reliable.  To get that set up, run these commands (while connected to the Internet):
```

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget ftp://ftp.dlink.com/Wireless/dwlg630_revC/Drivers/dwlg630_driver_300.zip
unzip dwlg630_driver_300.zip
sudo ndiswrapper -i Drivers/net5211.inf
echo ndiswrapper | sudo tee -a /etc/modules
echo ath5k | sudo tee -a /etc/modprobe.d/blacklist
echo ath9k | sudo tee -a /etc/modprobe.d/blacklist
echo ath_pci | sudo tee -a /etc/modprobe.d/blacklist
sudo update-initramfs -k $(uname -r) -u
```

Then reboot and hopefully things will work.  If they still don't, please post the output of:
```

lshw -C Network
uname -rm
ndiswrapper -l
dmesg | grep -e ndis -e wlan
```

---

### Post by venkyms on 2009-07-14
pytheas22 : i tried wicd and it works fine, but unfortunately i last my UMTS card module in this network manager, is there anything available to have my UMTS card work with this network manager

Thanks a lot
venkat

---

### Post by pytheas22 on 2009-07-14
venkyms: unfortunately I don't think there's any plugin for wicd for UMTS cards.  What you could do is use wicd and NetworkManager at the same time.  wicd says you're not supposed to do this, but it seems to work alright on my computer.

To install wicd and NetworkManager at the same time, follow these steps:

1. install NetworkManager again by typing:
```

sudo apt-get install network-manager-gnome
```

This may force you to uninstall wicd.  That's alright; we'll reinstall it below.

2. download the [wicd installer]("http://ubuntu.secs.oakland.edu/pool/universe/w/wicd/wicd_1.5.9-2_all.deb") and save it to your desktop.

3. open a terminal and type this command to install the wicd package that you just downloaded, telling the package manager to ignore the dependency conflict with NetworkManager:
```

cd ~/Desktop
sudo dpkg --force-all -i wicd*deb
```

You should now have both wicd and NetworkManager installed.  I'd recommend right-clicking on the NM icon and choosing "Disable networking" when you're just using the wireless, which you can connect to via wicd.  When you need to use your UMTS card, close wicd, reenable NetworkManager and use the device there.

Again, I can't promise that having NetworkManager and wicd installed at the same time won't cause problems, but it seems to be alright on my computer.

---

### Post by venkyms on 2009-07-16
pytheas22 : it was a good idea.. and i did the same... and i did one more thing installed linux-backports-modules-jaunty, it really boosted my signal strength, thanks for helping me to fix the issue

Regards
Venkat

---

### Post by ernits on 2009-07-21
hi pytheas22!

thanks again for the help!

i realized that the problem lies in no secure wireless. 

i'm now using a vpn connection at work and there's no problem at all, the connection is completely stable.

seems a little bit odd for me... but the connection at home works fine for my colleagues and it also worked for me before the upgrade. 

would you have any other suggestion? i'm really considering a downgrade to 8.04... :(

thanks for the attention!

---

### Post by pytheas22 on 2009-07-21
ernits: I'm not sure exactly what you mean.  The connection only works when your there is no wireless password, or when there is a wireless password?

---

### Post by ernits on 2009-07-21
hi pytheas22,

I'm mean the wireless security, like WEP/WPA/WPA2. 

At home it's a wireless without this password security, and at work I'm using a VPN connection.

---

### Post by pytheas22 on 2009-07-21
I'm not sure why you would have performance problems when there is *no* wireless security.  I'd expect the behavior to be the other way around.  Maybe there's some other difference between your network at work and the one at home that explains the behavior.  Could you please post the output of these commands when you're connected both at home and at work:
```

iwconfig
sudo iwlist scan
```

That will show information about the networks; maybe something will stand out as different between the two, and you can change your home network accordingly.

---

### Post by camberofculdi on 2009-09-01
I too have connection issues, Seems to be timing out, or slowing down greatly with my wireless.  This is my hardware info:

~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
03:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
0d:06.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 01)
0d:06.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
0d:06.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 03)

~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:1d:72:e6:54:0e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5764m-v3.34 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:17:c4:54:aa:42
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.2.11 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:f2:ab:ce:d5:78
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by pytheas22 on 2009-09-01
**camberofculdi**: I'm not sure what's wrong, but in general the ath9k driver has a lot of issues.  One thing that might help is to switch to wicd, an alternative connection manager.  You can install it by typing:
```

sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.

If wicd doesn't make a difference, you can try installing the backports package with:
```

sudo apt-get install linux-backports-modules-jaunty
```

That will install a newer version of the ath9k driver that my work better.

---

