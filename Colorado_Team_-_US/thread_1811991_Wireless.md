---
title: "Wireless"
date: 2011-07-25
forum: Colorado Team - US
---

### Post by Harley36 on 2011-07-25
I would like some info on the Colorado Team. I live in Westminster, Co
I also have an ubuntu wireless problem and need direction on how to use this forum to get help.
I am new to wireless using Ubuntu,but have never gotten it to work in any version up to an including 11.04 I can see the networks and it says I am connected but I can not get on the internet. I have an older laptop (Dell Inspiron 9300) with an Intel Pro/Wireless 2915 ABG. Every thing I read says the Linux driver is in the kernel. The driver being used is ipw 2200. Can you help me?
John Payne

---

### Post by Blasphemist on 2011-07-26
Welcome! From what I can tell quickly, you have the right default driver. When you click on your wireless network, are you prompted for a password? How do you have the wireless router set up? Did you set up the router yourself? What router make and model is it? 

As for using this forum, I don't see much activity on it but it shows up on my User CP so I do see it all the time. I sometimes don't notice new posts on it since it happens so infrequently. You're normally better off to post into the appropriate forum in the main community but I'm certainly willing to try and help. Usually people with a special expertise pay attention to related forums and that is usually the best help available. I do see a fair number of us coloradan's on the forums but I've never been to any meeting of us if there are any.

---

### Post by Harley36 on 2011-07-26
Hi Jim, thanks for the reply. yes It does ask for a password and says I am connected. I did set up the router myself and Windows does fine. It is setup to not broadcast ssid and use WPA2 Personal. Router is a Cisco (linksys) WRT160 V3.
I really need to learn how to use this forum

---

### Post by Blasphemist on 2011-07-27
Good morning John, I've got something to start with to help get to more specific information. I'll keep working on this as I can today and I know I have seen other good troubleshooting info that I ran into when working on another pc. This is the troubleshooting basics for this that I think you should look at. There is some broadcom specifics but I wouldn't focus just on that. [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Troubleshooting_Your_Wireless_LAN](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Troubleshooting_Your_Wireless_LAN)

```
Troubleshooting Your Wireless LAN

Linux wireless troubleshooting tools are quite extensive and provide a variety of useful information to help you get your network working. This section covers many important strategies that will compliment the use of more conventional procedures such as scanning your /var/log/messages file.
Check The NIC Status

When using WLAN methodology, the iwconfig, iwlist, and iwspy commands can provide useful information about the status of your wireless network. Take a closer look.
The iwconfig Command
In addition to using the regular ifconfig command to check the status of your NIC, you can use the iwconfig command to view the state of your wireless network, just don't specify any parameters. Specifically, you can see such important information as the link quality, WAP MAC address, data rate, and encryption keys, which can be helpful in ensuring the parameters across your network are the same. For example:
[root@bigboy tmp]# iwconfig
eth0      IEEE 802.11-DS  ESSID:"homenet"   Nickname:"bigboy"
          Mode:Managed   Frequency:2.462GHz  Access Point: 00:09:5B:C9:19:22
          Bit Rate:11Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:98D1-26D5-AC   Security mode:restricted
          Power Management:off
          Link Quality:36/92   Signal level:-92 dBm  Noise level:-148 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:0   Missed beacon:0
[root@bigboy tmp]#
The iwlist Command
The iwlist command can provide get further information related to not just the NIC, but the entire network, including the number of available frequency channels, the range of possible data rates, and the signal strength. This example uses the command to verify the encryption key being used by the NIC, which can be very helpful in troubleshooting security related difficulties on your network.
[root@bigboy tmp]# iwlist key
...
...
eth0      2 key sizes : 40, 104bits
          4 keys available :
                [1]: 9671-36DE-AC (40 bits)
                [2]: off
                [3]: off
                [4]: off
          Current Transmit Key: [1]
          Security mode:open
...
...
[root@bigboy tmp]#
The iwlist command can verify the speed of the NIC card being used, 11Mb/s in this case. This can be helpful in determining possible reasons for network slowness, especially as poor signal quality can result in the NIC negotiating a low bit rate with its WAP.
[root@bigboy tmp]# iwlist rate
...
...
eth0      4 available bit-rates :
          1Mb/s
          2Mb/s
          5.5Mb/s
          11Mb/s
          Current Bit Rate:11Mb/s
...
...
[root@bigboy tmp]#
For further information on the iwlist command, consult the man pages.
The iwspy Command
The iwspy command provides statistics on the quality of the link between your NIC and another wireless device on the network. It doesn't run all the time; you have to activate iwspy on your interface first. When not activated, iwspy gives a "no statistics to collect" message.
[root@bigboy root]# iwspy eth0
eth0      No statistics to collect
[root@bigboy root]#
Activation requires you to specify the target IP address and the wireless NIC interface through which it can be found.
[root@bigboy tmp]# iwspy eth0 192.168.1.1
If you use the iwspy command without the IP address it provides WLAN statistics with a typical/reference value against which it can be compared. In the example that follows the signal is considered fairly strong, with a 64/92 quality value versus a typical 36/92 value, but it could be weak by the historical values on your network. It's good to check this from time to time for fluctuations.
[root@bigboy tmp]# iwspy eth0
eth0      Statistics collected:
    00:09:5B:C9:19:22 : Quality:0  Signal level:0  Noise level:0
    Link/Cell/AP      : Quality:64/92  Signal level:-51 dBm   Noise level:-149 dBm (updated)
    Typical/Reference : Quality:36/92  Signal level:-62 dBm   Noise level:-98 dBm
[root@bigboy tmp]#
To switch off iwspy monitoring, add the off argument.
[root@bigboy root]# iwspy eth0 off
Check For Interrupt Conflicts

Devices slotted into your PCI bus are generally assigned an interrupt value by the system, which the system uses to signal its need to communicate with the device. Multiple devices on the bus can have the same interrupt, but the system will access each one using a different memory address to avoid confusion. Sometimes this automatic allocation of interrupt (IRQ) values and memory locations is flawed and overlaps do occur, causing devices to fail.
Before configuring your WLAN software, you should ensure that the wireless NIC card doesn't have an interrupt that clashes with another device in your computer. Insert the card in an empty slot in your Linux box according to the instructions in its manual, reboot, and inspect your /var/log/messages file again:
[root@bigboy tmp]# tail -300 /var/log/messages
Look carefully for any signs that the card is interfering with existing card IRQs. If there is a conflict, there will usually be a warning or "IRQ also used by ..." message. If that is the case, move the card to a different slot or otherwise eliminate the conflict by disabling the conflicting device if you don't really need it.
You should also inspect your /proc/interrupts file for multiple devices having the same interrupt
[root@bigboy tmp]# cat /proc/interrupts
11:     4639     XT-PIC     wlan0, eth0      (potentially bad)
 
[root@bigboy tmp]# cat /proc/interrupts
11:     4639     XT-PIC     wlan0            (good)
 
Interrupt conflicts are usually more problematic with old style PC-AT buses; newer PCI-based systems generally handle conflicts better. The prior (potentially bad) /proc/interrupts example came from a functioning PCI-based Linux box. It worked because, although the interrupt was the same, the base memory addresses that Linux used to communicate with the cards were different. You can check both the interrupts and base memory of your NIC cards by using the ifconfig -a command:
[root@bigboy tmp]# ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:08:C7:10:74:A8
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:11 Base address:0x1820 

wlan0 Link encap:Ethernet HWaddr 00:06:25:09:6A:B5
inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:215233 errors:0 dropped:0 overruns:0 frame:0
TX packets:447594 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:39394014 (37.5 Mb) TX bytes:126738425 (120.8 Mb)
Interrupt:11 Memory:c887a000-c887b000

[root@bigboy tmp]#
Kernel Errors

Messages related to how compatible your wireless card is with your version of the Linux master program, or kernel, can usually be found in one of two places. The /var/log/messages file, and through the use of the dmesg command.
Using the /var/log/messages File
When you find p80211 Kernel errors in the /var/log/messages file, they usually point to an incorrectly configured SSID or may also be caused by a NIC card with an outdated firmware version. For example:
Nov 13 22:24:54 bigboy kernel: p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
Using the dmesg Command
Another good source of information is the dmesg command which shows errors encountered by the kernel. In this case the firmware (microcode) for a Broadcom 43XX NIC could not be found. This was fixed by using the ndiswrapper technique explained in this chapter.
[root@bigboy tmp]# dmesg
...
...
bcm43xx: PHY connected
b43-phy0 debug: Adding Interface type 2
b43-phy0 ERROR: Microcode "bcm43xx_microcode5.fw" not available or  load failed.
b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 4)
bcm43xx: core_up for active 802.11 core failed (-2)
[root@bigboy tmp]# dmesg
Can't Ping Default Gateway

If you can't ping the default gateway, first check for kernel log errors.
If there are no errors in /var/log/messages and you can't ping your gateways or obtain an IP address, then check your /etc/sysconfig/network-scripts/ configuration files for a correct IP configuration and your routing table to make sure your routes are OK. You can also check to see if your Linux box is out or range of the WAP using the iwconfig command.
"Unknown Device" Errors

Look for "unknown device" or "no such device" errors in your log files or on your screen during installation or configuration. These may be caused by:
A NIC card that hasn't been correctly inserted in the PCI slot
Incompatible hardware.
For example, you might see incompatible hardware errors in /var/log/messages:
00:0c.0 Network controller: BROADCOM Corporation: Unknown device 4301 (rev01)
Subsystem: Unknown device 1737:4301
Flags: bus master, fast devsel, latency 64, IRQ 5
Memory at f4000000 (32-bit, non-prefetchable) [size=3D8K]
Capabilities: [40] Power Management version 2
Or, you might see errors on the screen:
Dec 1 01:28:14 bigboy insmod: /lib/modules/2.4.18-14/net/prism2_pci.o: init_module: No such device
Dec 1 01:28:14 bigboy insmod: Hint: insmod errors can be caused by incorrect module parameters, including invalid IO or IRQ parameters. You may find more information in syslog or the output from dmesg
Dec 1 01:28:14 bigboy insmod: /lib/modules/2.4.18-14/net/prism2_pci.o: insmod wlan0 failed
Hermes Chipset Errors

I have seen cases where Linux compatible NIC cards with the Hermes chipset fail to respond after the system has been running for a few days with errors in the /var/log/messages file similar to these.
May  7 22:26:26 bigboy kernel: hermes @ e0854000: BAP0 offset timeout: reg=0x8044 id=0xfc80 offset=0x0
May  7 22:26:26 bigboy kernel: eth1: Error -110 setting multicast list.
May  7 22:26:26 bigboy avahi-daemon[1701]: Withdrawing address record for 216.10.119.243 on eth1.
May  7 22:26:26 bigboy avahi-daemon[1701]: Leaving mDNS multicast group on interface eth1.IPv4 with address 216.10.119.243.
May  7 22:26:26 bigboy avahi-daemon[1701]: IP_DROP_MEMBERSHIP failed: No such device
May  7 22:26:26 bigboy avahi-daemon[1701]: iface.c: interface_mdns_mcast_join() called but no local address available.
May  7 22:26:26 bigboy avahi-daemon[1701]: Interface eth1.IPv4 no longer relevant for mDNS.
May  7 22:26:27 bigboy kernel: hermes @ e0854000: Timeout waiting for command 0x0002 completion.
May  7 22:26:27 bigboy kernel: eth1: Error -110 disabling MAC port
May  7 22:26:31 bigboy kernel: hermes @ e0854000: ng Error -16 issuing command 0x0021.
May  7 22:26:31 bigboy kernel: hermes @ e0854000: Error -16 issuing command 0x0021.
May  7 22:26:31 bigboy kernel: eth1: Error -110 setting MAC address
May  7 22:26:31 bigboy kernel: eth1: Error -110 configuring card
Connectivity is usually only restored after a reboot. The best solution to the problem has been to either use ndiswrapper or replace the NIC with a truly compatible device.
Broadcom SoftMac Errors

If your configuration is correct, and your NIC fails to work while adding repeated failed SoftMAC authentication requests messgaes to your /var/logs/messages file, as seen here, you may have a Linux incompatibility issue with your NIC.
May 15 20:02:04 bigboy kernel: bcm43xx: set security called, .level = 0, .enabled = 0, .encrypt = 0
May 15 20:02:04 bigboy kernel: bcm43xx: set security called, .level = 0, .enabled = 0, .encrypt = 0
May 15 20:02:04 bigboy kernel: bcm43xx: set security called, .level = 0, .enabled = 0, .encrypt = 0
May 15 20:02:04 bigboy kernel: bcm43xx: set security called, .level = 0, .enabled = 0, .encrypt = 0
May 15 20:02:04 bigboy kernel: bcm43xx: set security called, .level = 0, .enabled = 0, .encrypt = 0
May 15 20:02:04 bigboy kernel: SoftMAC: Scanning finished: scanned 14 channels starting with channel 1
May 15 20:02:04 bigboy kernel: SoftMAC: Queueing Authentication Request to 00:18:39:ea:5c:ac
May 15 20:02:04 bigboy kernel: SoftMAC: Cannot associate without being authenticated, requested authentication
May 15 20:02:04 bigboy kernel: SoftMAC: Sent Authentication Request to 00:18:39:ea:5c:ac.
May 15 20:02:04 bigboy kernel: SoftMAC: generic IE set to dd160050f20101000050f20201000050f20201000050f202
May 15 20:02:04 bigboy kernel: SoftMAC: Already associating or associated to 00:18:39:ea:5c:ac
May 15 20:02:04 bigboy kernel: SoftMAC: Open Authentication completed with 00:18:39:ea:5c:ac
May 15 20:02:04 bigboy kernel: SoftMAC: sent association request!
May 15 20:02:04 bigboy kernel: SoftMAC: associated!
May 15 20:02:04 bigboy kernel: SoftMAC: Associate: Scanning for networks first.
Try using ndiswrapper as a quick solution to this problem.
ndiswrapper Errors

There are a number of common errors that can occur with the use of ndiswrappers. Here are some common examples.

CONFIG_4KSTACKS errors During Installation
Sometimes your ndiswrapper installation will give CONFIG_4KSTACKS errors, like the one that follows, due to a kernel incompatibility:
*** WARNING: Kernel seems to have 4K size stack option (CONFIG_4KSTACKS) removed; many Windows
drivers will need at least 8K size stacks. You should read wiki about 4K size stack issue. Don't
complain about crashes until you resolve this.
...
...
[root@bigboy ndiswrapper-1.16]#

This is common with default Fedora installations, and ndiswrapper may work perfectly with this limitation. If you had no CONFIG_4KSTACKS type errors or are willing to test ndiswrapper even though they exist, then you can proceed with your installation in the normal fashion. The following steps will show you how to recover from this error cleanly.
1.	The ndiswrapper website lists websites at the following URL from which you can download kernels with larger 16K stacks. This will be faster than creating your own.
http://ndiswrapper.sourceforge.net/mediawiki/index.php/Fedora
Remember to download a kernel that matches your system architecture and kernel version. This can be ascertained using the uname -a command. Here our system is running Fedora Core 5 kernel version 2.6.16-1.2122 on an i686 platform.
[root@bigboy linux]# uname -rp
2.6.16-1.2122_FC5 i686
[root@bigboy linux]#
If you choose to download the purpose built kernel then do so. Install the RPM, reboot and then continue to the section, "Installing and Configuring ndiswrapper".
If you decide to create your own kernel, then follow the next steps.
2.	You have reached this step because you have decided to recompile your kernel. It is not a difficult process, there are only a few steps, but the compilation time can be lengthy. The first step is to install the kernel source files. This is covered in Chapter 33, "Modifying the Kernel to Improve Performance".
3.	After installing the sources, you'll have to prepare for compiling a new kernel customized for use with ndiswrapper. The first step is to clean up any temporary files that may have existed from any previous compilations you may have done by using the make mrproper command. You'll then need to use the make oldconfig command to create a default version of the .config file Linux will use in compiling your new customized kernel.
[root@bigboy tmp]# cd /usr/src/linux
[root@bigboy linux]# make mrproper
[root@bigboy linux]# make oldconfig

4.	 Edit the .config file and set the CONFIG_4KSTACKS variable to "n".
[root@bigboy linux]# vi .config

#
# File: /usr/src/linux/.config
#

#CONFIG_4KSTACKS=y
CONFIG_4KSTACKS=n

[root@bigboy linux]#

5.	 The kernel compilation process also reads the file Makefile to determine the new name of the kernel to be used. The EXTRAVERSION variable in this file adds a suffix to the kernel name to help you track version numbers. Edit Makefile and set the EXTRAVERSION to -ndis-stk16 so that the new kernel will be easily identifiable as a version that supports ndiswrapper.
[root@bigboy linux]# vi Makefile

#
# File: /usr/src/linux/Makefile
#

EXTRAVERSION = -ndis-stk16

[root@bigboy linux]#

6.	 Compile the kernel and its modules with the following series of make commands. Make sure they finish without error and remember that this can be a lengthy process.
[root@bigboy linux]# make; make modules_install; make install

7.	 If you installed a new version of the kernel, you'll now have to ensure that your system selects the correct kernel version when it reboots. This will require you to edit the /etc/grub.conf file as outlined in Chapter 33, "Modifying the Kernel to Improve Performance".
8. Shutdown your system, install the NIC card and boot up. The system will now load your new kernel which you can verify with the uname command.
[root@bigboy linux]# uname -r
2.6.16-ndis-stk16
[root@bigboy linux]#

9. If you installed a new version of the kernel and your system fails to reboot correctly, refer to the "Kernel Crash Recovery" section of Chapter 33, "Modifying the Kernel to Improve Performance" for help. When you get your system to reboot correctly, revise your installation steps and make sure you had originally installed the correct version.
With your new kernel running, its time to reinstall and configure ndiswrapper.
Incorrect Drivers
Using an incorrect driver will cause errors to be displayed when you run the dmesg command. Here is a simple error message in which part of the driver initialization process failed:
[root@bigboy tmp]# 
...
...
...
wlan0: ndiswrapper ethernet device 00:06:25:1b:b2:a9 using driver
wmp11v27, 14E4:4301:1737:4301.5.conf
ndiswrapper (set_auth_mode:702): setting auth mode to 3 failed
(C0010015)
[root@bigboy tmp]#
The best way to fix this is to obtain the correct driver, unload the ndiswrapper module from memory, uninstall the old driver, install the new driver and then reload ndiswrapper. Here are the steps with the necessary commands:
1.	Download the driver package from the correct source and extract the contents to your Linux system. 2.	Verify that the ndiswrapper module has been loaded using the lsmod command, and then remove it from memory using the rmod command.
[root@bigboy tmp]# lsmod
 Module                  Size  Used by
 ...
 ...
 ndiswrapper           145584  0 
 ipv6                  225504  16 
 autofs4                19204  1 
 [root@bigboy tmp]# rmmod ndiswrapper

3.	Get a listing of the installed drivers using the ndiswrapper command with the -l flag, and then remove the desired driver using the ndiswrapper -r flag.
[root@bigboy tmp]# ndiswrapper -l
Installed drivers:
wmp11v27                driver installed, hardware present 
[root@bigboy tmp]# ndiswrapper -r wmp11v27 
[root@bigboy tmp]# 
4.	Install the new driver with the ndiswrapper -i flag and verify that the driver was loaded with the ndiswrapper -l flag.
[root@bigboy tmp]# ndiswrapper -i bcmwl5.inf
Installing bcmwl5
[root@bigboy tmp]# ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 
[root@bigboy tmp]#
5.	Use depmod to reload the module tables for the operating system.
[root@bigboy tmp]# depmod -a 
6.	Use modprobe to reload the ndiswrapper module into memory.
[root@bigboy tmp]# modprobe ndiswrapper
7.	Finally, verify that there were no loading problems with the dmesg command. If there weren't any, configure your wlan0 interface like any other Linux NIC interface on your system.
8.	At this stage, even with no errors, a reboot may be necessary in order to get your wireless card to work.
It is always a good idea to use the correct drivers to reduce the risk of installation failure. Fortunately this recovery procedure should get your system to function correctly.
NICs that are Incompatible with ndiswrapper
The ndiswrapper module works by assuming that the Linux operating system does not recognize the NIC card. If Linux does recognize the card, then ndiswrapper won't load correctly. The ndiswrapper -l command will list installed drivers, there will be ndiswrapper entries in the /var/log/messages file but the dmesg command won't mention the status of the ndiswrapper module loading process at all and activating the wlan0 interface will fail.
[root@bigboy tmp]# ifup wlan0
ndiswrapper device wlan0 does not seem to be present, delaying initialization.
[root@bigboy tmp]# ndiswrapper -l
Installed drivers:
netma311                driver installed, hardware present 
[root@bigboy tmp]# dmesg | grep ndiswrapper
[root@bigboy tmp]#
The previous example shows these symptoms when using ndiswrapper with a Linux compatible Netgear ma311 NIC.
Invalid module format Errors
The ndiswrapper package installs itself as a module that works closely with the Linux kernel. If you upgrade your kernel, ndiswrapper can stop working. In such cases reinstalling ndiswrapper can cause "Invalid module format" errors like this:
[root@bigboy tmp]# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper
(/lib/modules/2.6.23.9-85.fc8/misc/ndiswrapper.ko): Invalid module format
[root@bigboy tmp]#
The solution to this is to remember to always run the make distclean command before any of the other installation related make commands. This guarantees that the module will be compatible with your new kernel.


```

---

### Post by Harley36 on 2011-07-27
Thanks. I have to go out for a few hours, but will get with this as soon as I get back.
John

---

### Post by Blasphemist on 2011-07-27
John, I found a page or two that might help. Please look at this from the link that follows it.
> Troubleshooting

Examine the kernel ring buffer (dmesg(1)) to verify required firmware files are being loaded by the driver. If requested firmware is not available, no wireless interface will be created.
Ensure the firmware-ipw2x00 package is installed, then reinsert the relevant driver module as described above.
ipw2200: If you receive a "Failed to send TX_POWER: Command timed out." message, add irqpoll to your kernel command line.
[http://wiki.debian.org/ipw2200](http://wiki.debian.org/ipw2200)

Also, from this page that might help, there are links to quite a few pages that might help depending on where this goes.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

I think looking at the kernel ring buffer if the place to start. You can see that from the log viewer.

---

### Post by Harley36 on 2011-07-28
Just got back--family emergency--had to leave town. I don't give up easily, but am just about at the end of the line. This is getting further into Ubuntu than I am prepared for at this time. I will keep working with your suggestions and will try a USB wireless adapter. I have to order one for my lady as she wants to leave Quest and get back on my network with Comcast from her office upstairs, mine is downstairs so we will use wireless. She uses XP, so I don't see a problem there.
John

---

### Post by Blasphemist on 2011-07-28
Here's one thing you might do if you have any doubt at all about the router set up. Boot your wife's pc to the live cd or usb and connect to the wireless. If no issues, you have eliminated for sure you router setup.

Watch out though. I left my install cd with my sister and she installed it. She's been using it since and hasn't needed one question answered. 

Try to look at like a good puzzle that is just challenging you.

---

