---
title: "Dell mini 12 no internet connection"
date: 2009-06-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Topazio785 on 2009-06-13
Hello,

Newbie to Ubuntu!

I just purchased a dell mini 12 pre-installed with Ubuntu 8.04.  It was working great, had wireless working immediately - wired did not work but I was planning to use mainly wireless so no biggie.

I installed all the updates and lo and behold wireless no longer works, wired doesn't work!!  Sigh.  

I re-installed Ubuntu from the CD Dell sent and still no luck. :( Bad move, my part! 
 I found a few posts and tried to follow the instructions but could not get very much as the steps mostly involved downloading and installing from internet.

Please explain everything in detail as I am new to Ubuntu.

Would installing 8.10 be a good idea?  How would I download the ISO file to a windows machine (that is connected to the internet) and create a file that I can use in Ubuntu to install?  

Any help you can offer me is truly appreciated.

Thank You,

---

### Post by coffeeaddict22 on 2009-06-13
Hi,
Sounds like fun.  A connection of some sort makes life a whole lot easier.  Try the following.
```
ifconfig down
ifconfig up

```
if you've got no success, could you open a terminal, type in the following commands, and cut and paste the output back please?
```
lshw -C network
lspci (although we only need to see the lines that refer to your network cards)
iwconfig

```
If you do get a wired connection, make sure it's not a Simpson moment (doh!): Check in System/Administration/Hardware Drivers.  If there's a driver lised in there and not enabled, enable it.

---

### Post by Topazio785 on 2009-06-13
Thanks, I've added my results below.


[B]ifconfig down
ifconfig up[/B]

results:
	 	 cathy@cathy:~$ ifconfig down  
 down: error fetching interface information: Device not found  
 

**lshw -C network**

	 	 cathy@cathy:~$ lshw -C network  
 bash: lshw: command not found  
 
**lspci **(although we only need to see the lines that refer to your network cards)

	 	 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)  
 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)  
 [B]
iwconfig[/B]

	 	 cathy@cathy:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth1      IEEE 802.11  Nickname:"" 
           Access Point: Not-Associated    
            
 eth0      no wireless extensions.  
 
[/code]If you do get a wired connection, make sure it's not a Simpson moment (doh!): Check in System/Administration/Hardware Drivers.  If there's a driver lised in there and not enabled, enable it.[/quote]

The only device driver listed is wl and it is enabled

Thanks, Cathy

---

### Post by coffeeaddict22 on 2009-06-14
OK, sorry, forgot the mini Ubuntu install doesn't have lshw.
Can you try ```
lspci -v
``` and post back the stuff that refers to your network devices in there?

---

### Post by Topazio785 on 2009-06-15
Here are the results:

	 	 cathy@cathy:~$ lspci -v  
 00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0  
 

 00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07) (prog-if 00 [VGA controller])  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 17  
 	Memory at d8100000 (32-bit, non-prefetchable) [size=512K]  
 	I/O ports at 1800 [size=8]  
 	Memory at d0000000 (32-bit, non-prefetchable) [size=128M]  
 	Memory at d8380000 (32-bit, non-prefetchable) [size=128K]  
 	Capabilities: <access denied>  
 

 00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 22  
 	Memory at d83a0000 (64-bit, non-prefetchable) [size=16K]  
 	Capabilities: <access denied>  
 

 00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07) (prog-if 00 [Normal decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0  
 	I/O behind bridge: 00002000-00002fff  
 	Memory behind bridge: 50000000-500fffff  
 	Prefetchable memory behind bridge: d8400000-d84fffff  
 	Capabilities: <access denied>  
 

 00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07) (prog-if 00 [Normal decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0  
 	Memory behind bridge: d8000000-d80fffff  
 	Capabilities: <access denied>  
 

 00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07) (prog-if 00 [UHCI])  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 18  
 	I/O ports at 1820 [size=32]  
 

 00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07) (prog-if 00 [UHCI])  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 19  
 	I/O ports at 1840 [size=32]  
 

 00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07) (prog-if 00 [UHCI])  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 20  
 	I/O ports at 1860 [size=32]  
 

 00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07) (prog-if 20 [EHCI])  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 21  
 	Memory at d83a4000 (32-bit, non-prefetchable) [size=1K]  
 	Capabilities: <access denied>  
 

 00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: fast devsel  
 

 00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07) (prog-if 80 [Master])  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0  
 	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]  
 	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]  
 	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]  
 	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]  
 	I/O ports at 1810 [size=16]  
 

 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 223  
 	I/O ports at 2000 [size=256]  
 	Memory at d8410000 (64-bit, prefetchable) [size=4K]  
 	Memory at d8400000 (64-bit, prefetchable) [size=64K]  
 	[virtual] Expansion ROM at d8420000 [disabled] [size=128K]  
 	Capabilities: <access denied>  
 

 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)  
 	Subsystem: Broadcom Corporation Unknown device 04b5  
 	Flags: bus master, fast devsel, latency 0, IRQ 16  
 	Memory at d8000000 (64-bit, non-prefetchable) [size=16K]  
 	Capabilities: <access denied>  
   
 cathy@cathy:~$  
 
Thanks,
Cathy

---

### Post by Topazio785 on 2009-06-15
I just realized that I needed to use sudo for this command so here are the results again.

	 	 cathy@cathy:~$ sudo lspci -v  
 [sudo] password for cathy:  
 00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0  
 

 00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07) (prog-if 00 [VGA controller])  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 17  
 	Memory at d8100000 (32-bit, non-prefetchable) [size=512K]  
 	I/O ports at 1800 [size=8]  
 	Memory at d0000000 (32-bit, non-prefetchable) [size=128M]  
 	Memory at d8380000 (32-bit, non-prefetchable) [size=128K]  
 	Capabilities: [d0] Power Management version 2  
 	Capabilities: [b0] Vendor Specific Information  
 	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-  
 

 00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 22  
 	Memory at d83a0000 (64-bit, non-prefetchable) [size=16K]  
 	Capabilities: [50] Power Management version 2  
 	Capabilities: [70] Express Unknown type IRQ 0  
 

 00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07) (prog-if 00 [Normal decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0  
 	I/O behind bridge: 00002000-00002fff  
 	Memory behind bridge: 50000000-500fffff  
 	Prefetchable memory behind bridge: d8400000-d84fffff  
 	Capabilities: [40] Express Root Port (Slot+) IRQ 0  
 	Capabilities: [90] Subsystem: Dell Unknown device 02b1  
 	Capabilities: [a0] Power Management version 2  
 

 00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07) (prog-if 00 [Normal decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0  
 	Memory behind bridge: d8000000-d80fffff  
 	Capabilities: [40] Express Root Port (Slot+) IRQ 0  
 	Capabilities: [90] Subsystem: Dell Unknown device 02b1  
 	Capabilities: [a0] Power Management version 2  
 

 00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07) (prog-if 00 [UHCI])  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 18  
 	I/O ports at 1820 [size=32]  
 

 00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07) (prog-if 00 [UHCI])  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 19  
 	I/O ports at 1840 [size=32]  
 

 00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07) (prog-if 00 [UHCI])  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 20  
 	I/O ports at 1860 [size=32]  
 

 00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07) (prog-if 20 [EHCI])  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 21  
 	Memory at d83a4000 (32-bit, non-prefetchable) [size=1K]  
 	Capabilities: [50] Power Management version 2  
 	Capabilities: [58] Debug port  
 

 00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: fast devsel  
 

 00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07) (prog-if 80 [Master])  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0  
 	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]  
 	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]  
 	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]  
 	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]  
 	I/O ports at 1810 [size=16]  
 

 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)  
 	Subsystem: Dell Unknown device 02b1  
 	Flags: bus master, fast devsel, latency 0, IRQ 223  
 	I/O ports at 2000 [size=256]  
 	Memory at d8410000 (64-bit, prefetchable) [size=4K]  
 	Memory at d8400000 (64-bit, prefetchable) [size=64K]  
 	[virtual] Expansion ROM at d8420000 [disabled] [size=128K]  
 	Capabilities: [40] Power Management version 3  
 	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+  
 	Capabilities: [70] Express Endpoint IRQ 1  
 	Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2  
 	Capabilities: [cc] Vital Product Data  
 

 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)  
 	Subsystem: Broadcom Corporation Unknown device 04b5  
 	Flags: bus master, fast devsel, latency 0, IRQ 16  
 	Memory at d8000000 (64-bit, non-prefetchable) [size=16K]  
 	Capabilities: [40] Power Management version 3  
 	Capabilities: [58] Vendor Specific Information  
 	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-  
 	Capabilities: [d0] Express Endpoint IRQ 0  
 

 cathy@cathy:~$  
 cathy@cathy:~$  
 
Thanks,
Cathy

---

### Post by coffeeaddict22 on 2009-06-15
Rats.  lspci should give you the drivers, and they're likely to be your problem..  eg my output looks like this: ```
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
	Subsystem: Dell Device 020d
	Flags: bus master, fast devsel, latency 0, IRQ 2302
	Memory at fdfc0000 (32-bit, non-prefetchable) [size=128K]
	Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ff00 [size=32]
	Capabilities: <access denied>
	[B]Kernel driver in use: e1000e
	Kernel modules: e1000e[/B]

```
can you try running```
lsmod
``` and post the output back?

---

### Post by Topazio785 on 2009-06-15
here are the results

	 	 cathy@cathy:~$ lsmod  
 Module                  Size  Used by  
 parport_pc             36260  0  
 ppdev                  10372  0  
 parport                37704  2 parport_pc,ppdev  
 dcdbas                  9504  0  
 rfcomm                 41232  2  
 l2cap                  25472  13 rfcomm 
 hci_usb                16540  2  
 bluetooth              60900  7 rfcomm,l2cap,hci_usb  
 uvcvideo               58116  0  
 compat_ioctl32          2304  1 uvcvideo  
 videodev               29440  1 uvcvideo  
 v4l1_compat            15492  2 uvcvideo,videodev  
 v4l2_common            18304  2 uvcvideo,videodev  
 psb                   162856  2  
 i2c_algo_bit            7300  1 psb  
 wl                   1077012  0  
 acpi_cpufreq           10796  1  
 drm_psb               188488  3 psb  
 agpgart                34760  1 drm_psb 
 cpufreq_userspace       5156  0  
 cpufreq_conservative     8712  0  
 cpufreq_powersave       2688  0  
 cpufreq_stats           7104  0  
 snd_seq_midi            9376  0  
 snd_seq_oss            35328  0  
 snd_seq_dummy           4868  0  
 snd_pcm_oss            42144  0  
 snd_hda_intel         349712  2  
 snd_seq_midi_event      8320  2 snd_seq_midi,snd_seq_oss  
 snd_rawmidi            25632  1 snd_seq_midi  
 snd_hwdep              10500  1 snd_hda_intel  
 snd_pcm                78596  2 snd_pcm_oss,snd_hda_intel  
 snd_page_alloc         11400  2 snd_hda_intel,snd_pcm  
 snd_mixer_oss          17792  1 snd_pcm_oss  
 snd_seq                53968  6 snd_seq_midi,snd_seq_oss,snd_seq_dummy,snd_seq_midi_event  
 snd_timer              24836  2 snd_pcm,snd_seq  
 snd_seq_device          9484  5 snd_seq_midi,snd_seq_oss,snd_seq_dummy,snd_rawmidi,snd_seq  
 snd                    56868  15 snd_seq_oss,snd_seq_dummy,snd_pcm_oss,snd_hda_intel,snd_rawmidi,snd_hwdep,snd_pcm,snd_mixer_oss,snd_seq,snd_timer,snd_seq_device 
 soundcore               8800  1 snd  
 ieee80211_crypt_tkip    11520  0  
 r8169                  33156  0  
 ieee80211_crypt         6912  2 wl,ieee80211_crypt_tkip  
 iTCO_wdt               13092  0  
 iTCO_vendor_support     4868  1 iTCO_wdt  
 serio_raw               7940  0  
 psmouse                40336  0  
 fuse                   50324  3  
 ahci                   28420  0  
 squashfs               49032  0  
 unionfs                73168  0  
 ehci_hcd               37900  0  
 isofs                  36004  0  
 zlib_inflate           18176  2 squashfs,isofs 



 	 	 [SIZE=3]I was going to try to install this:[/SIZE]
 [SIZE=3]Broadcom's Linux kernel space hybrid driver for[/SIZE]
 [SIZE=3]use with Broadcom BCM43224-based (device ID 4353) hardware.[/SIZE]  [SIZE=3]But I could not get past this step[/SIZE] [SIZE=3]5.  Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`[/SIZE]  [SIZE=3]Could not find file 2.6.xx.xx[/SIZE] 
 Thanks, 

Cathy

---

### Post by Topazio785 on 2009-06-15
The Dell support page gave me drivers for wired/wireless but only has windows xp drivers.  I've read many posts about ndiswrapper, will this help and how can I get it installed to  my mini?  I can download things with my windows machine and copy to a USB key or CD and transfer over to my mini but I don't know the commands to install these things.  

Thanks again,
Cathy

---

### Post by coffeeaddict22 on 2009-06-15
Don't reinstall the wl driver.  It's loaded (or at least listed in lsmod).
Need to know what driver is being used.  Can you download lshw and run that?
Another command that may help: what is the output of ```
nm-tool
```

---

### Post by Topazio785 on 2009-06-16
here are the results of nm-tool

	 	 NetworkManager Tool  
 

 State: connected  
 

 - Device: eth1 ----------------------------------------------------------------  
   NM Path:           /org/freedesktop/NetworkManager/Devices/eth1  
   Type:              802.11 Wireless  
   Driver:            wl  
   Active:            no  
   HW Address:        00:23:08:82:EA:99  
 

   Capabilities:  
     Supported:       yes  
     Speed:           48 Mb/s  
 

   Wireless Settings  
     Scanning:        yes  
     WEP Encryption:  yes  
     WPA Encryption:  yes  
     WPA2 Encryption: yes  
 

   Wireless Networks (* = Current Network)  
     dlink:           Infrastructure Mode, Freq 2.412 MHz, Rate 62 Mb/s, Strength 100%  
     linksys:         Infrastructure Mode, Freq 2.437 MHz, Rate 62 Mb/s, Strength 20%  
     michelle:        Infrastructure Mode, Freq 2.412 MHz, Rate 62 Mb/s, Strength 20%, Encrypted (WPA) 



Cathy

---

### Post by coffeeaddict22 on 2009-06-16
it looks from that as if ifconfig up (or possibly sudo ifconfig up) should bring up your wireless network....

---

### Post by Topazio785 on 2009-06-16
sudo ifconfig up results in:

up: error fetching interface information: Device not found.

Cathy

---

### Post by Topazio785 on 2009-06-16
I am trying to install the lshw.  I downloaded it from the internet, transfered it to my mini, was able to 'unzip' (not sure of the correct terminology here) but now it's showing as locked and I can't create or install. I tried switching to root but since the file is in my home directory I can't seem to copy it either.  I've done something, I'm sure but not sure.

Sorry to be so simple here, I am new to ubuntu and linux in general.


Cathy

---

### Post by coffeeaddict22 on 2009-06-16
lshw is in the repositories- have a look in Synaptic package manager. That'd be the easiest way to install.


what's the output of ```
sudo iwlist scan
```

---

### Post by Topazio785 on 2009-06-17
Here are the results.

	 	 cathy@cathy:~$ sudo iwlist scan  
 [sudo] password for cathy:  
 lo        Interface doesn't support scanning.  
 

 eth1      Scan completed :  
           Cell 01 - Address: 00:1E:58:EF:2B:47  
                     ESSID:"dlink" 
                     Mode:Managed  
                     Frequency:2.462 GHz (Channel 11)  
                     Quality:5/5  Signal level:-25 dBm  Noise level:-15 dBm  
                     Encryption key:off  
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s  
                               12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s  
                               48 Mb/s; 54 Mb/s  
 

 eth0      Interface doesn't support scanning. 



the system keeps trying to connect to the internet to install from the repositories/synaptic package manager.

---

### Post by coffeeaddict22 on 2009-06-17
OK.  You've got a working wireless.  It's seeing a network (that's the "ESSID: dlink" line in the nm-tool output), but can't connect to it.  open the network manager, System/Preferences/Network connections, go to wireless, and add in your home network settings.  the output from nm-tool suggests most likely you haven't got the wireless security set up; it's all in the network manager screens.  You should be good to go then.

---

### Post by Topazio785 on 2009-06-17
I have been trying to use the network manager to connect and it's been difficult.  I don't have WEP or any other password set up but use the MAC address filter on my wireless router.  I've added the address of the mini to the router.  I will try again and see if I can get it to connect. - It seems to want a password entered.

Just to confirm, this would be the MAC address?
HW Address:        00:23:08:82:EA:99

Thanks for all your help,  
I will let you know how it goes.

Cathy

---

### Post by coffeeaddict22 on 2009-06-18
Should be.
Might be worth trying changing the channel on your router first.  I've a vague recollection of someone having a problem with it; it also sometimes fixes wireless glitches due to crosstalk.

---

### Post by Topazio785 on 2009-06-18
Thanks! That worked and am now connected to the internet!  I truly appreciate all of the help and I learned a bit more about Ubuntu and Linux in the process.

Cathy

---

### Post by Fangman on 2009-06-23
I had the same problem with my mini 12, but reinstall solved it. I decided to update again crossing my fingers and it seems to have worked, except firefox wouldnt load. I went ahead and reinstalled firefox and it works. 

My question is this: Is there always something that goes wrong when one updates?

---

### Post by coffeeaddict22 on 2009-06-23
Hi,
 Updating does seem to be a bit of a lottery at times.  There is a reason for that; the OS is constantly being updated.  The API's (Applications Programming Interfaces are, as best as I can make out, the instructions from one part of the software to any other on how to talk to it sensibly) tend to get stretched as time goes by, much like a language changes over time.  Inevitably, eventually things start to break, and if all components aren't updated simultaneously, bad things happen.

Your firefox issues shouldn't have happened though.  It's possible you upgraded the kernel but used firefox without updating all your programs.  

The wireless problem and your firefox issue are possibly due to the same issue: config files in the /home directory.  Upgrades from 8.04 through 9.04 had wireless problems due to a whole lot of new drivers getting included in the .iso; unfortunately, previously most people ran ndiswrapper, and that installs some files in the /home directory, which doesn't upgrade... = glitch.  Firefox has a config file in the ~/.mozilla directory- if you want to look, open a browser tab and type about:config in the url bar.  I'd guess there was a compatibility issue somewhere in there.  There's a few articles around on how to play with mozilla config; [here's one.]("http://www.linuxjournal.com/article/8004")  
Essentially, /home doesn't update (it's your personal files, so that's sensible); that means any config files in it can be error magnets.
But, at the end of the day, it's still a good OS to play in! :)

---

