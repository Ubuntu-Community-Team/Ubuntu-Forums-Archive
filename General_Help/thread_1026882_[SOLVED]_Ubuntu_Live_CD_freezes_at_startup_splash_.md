---
title: "[SOLVED] Ubuntu Live CD freezes at startup splash screen"
date: 2008-12-31
forum: General Help
---

### Post by INH on 2008-12-31
My previous problem with the startup freezing (to which the first 2 posts in this thread were addressed) was solved.  Now my wireless card, an Atheros 5007 pre-installed card, will not toggle on in Ubuntu.  In Windows, it usually toggles on during startup.  In Ubuntu, it doesn't toggle on during start up, and when I hit the button after startup, nothing happens.  Is this a simple problem of needing drivers or something else?

---

### Post by pytheas22 on 2008-12-31
One possibility is that the CD that you created is corrupted.  Try burning a second CD, and make sure to burn it at a low speed.

It's also possible that the .iso file itself that you downloaded was corrupted in transit.  You should take a checksum of the file, as explained on the page that you originally consulted, if you haven't already.

You may also want to try installing using the [alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").  In some cases this works where the live installer won't.  Note that the alternate CD, unlike the live CD, doesn't provide an option to run Ubuntu directly from the CD; your only option is to install to the hard disk.

You could also try installing using [wubi]("http://wubi-installer.org/"), if you have Windows on this computer.

Finally, there may be some kind of issue with your particular computer that makes Linux not like it.  If you tell us as specifically as possible the model of your computer, we can google to see if anyone else has had issues starting Ubuntu on it.

Also, how much memory do you have in your computer?  You should have at least 256 megabytes to run the live CD.

---

### Post by dcstar on 2008-12-31
> **INH said:**
> I'm looking into using Ubuntu, so I burned a live CD for it following the instructions on [this](http://www.psychocats.net/ubuntu/iso) webpage, put the CD in the drive and started the computer up.  I saw my regular startup splash screen, then it showed me this Ubuntu splash screen:

[img]http://www.psychocats.net/ubuntu/images/dualboot02.png[/img]

I selected the "Try Ubuntu without any change to your computer" option, and hit enter.  The computer froze.  I thought, "Oh, it's just being slow", and left it sitting there for 5-10 minutes.  It was still frozen, the only way I could get off of it was by powering down the computer.  So, I did that, booted up again, and instead of the first option hit the "Check CD for Defects" option.  Same thing, only with the third option highlighted instead of the first.  I tried "Test Memory".  Same thing.  Does anybody know why this might be happening?

Select the F4 option to boot up in low graphics mode and see how that goes.

---

### Post by INH on 2009-01-01
Alright, well I got it to install using wubi - thanks for the tip.  Now I have trouble with my wireless card.  I'm using an HP/Compaq CQ50-215NR laptop, and it has a WiFi toggle button right next to the power button.  Unfortunately, neither the WiFi nor this button works on Ubuntu.  When I boot up Windows, it usually turns the WiFi on during startup.  Do I need drivers, or is this some other problem.

Thanks.

---

### Post by pytheas22 on 2009-01-01
If you could please post the output of the following commands, I'll be able to tell you how to make the wifi work:
```

lshw -C Network
uname -rm
lspci -nn
lsusb
dmesg | grep adio
```

---

### Post by INH on 2009-01-01
the "lshw -C Network" command give the following output:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:55:6e:07
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.108 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:05:b7:15:74:da
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


The "uname -rm" command gives:

2.6.27-9-generic i686


The "lspci -nm" command gives:

00:00.0 "0500" "10de" "0754" -ra2 "103c" "360a"
00:01.0 "0601" "10de" "075e" -ra2 "103c" "360a"
00:01.1 "0c05" "10de" "0752" -ra1 "103c" "360a"
00:01.3 "0b40" "10de" "0753" -ra2 "103c" "360a"
00:01.4 "0500" "10de" "0568" -ra1 "103c" "360a"
00:02.0 "0c03" "10de" "077b" -ra1 -p10 "103c" "360a"
00:02.1 "0c03" "10de" "077c" -ra1 -p20 "103c" "360a"
00:04.0 "0c03" "10de" "077d" -ra1 -p10 "103c" "360a"
00:04.1 "0c03" "10de" "077e" -ra1 -p20 "103c" "360a"
00:06.0 "0101" "10de" "0759" -ra1 -p8a "f03c" "360a"
00:07.0 "0403" "10de" "0774" -ra1 "103c" "360a"
00:08.0 "0604" "10de" "075a" -ra1 -p01 "" ""
00:09.0 "0101" "10de" "0ad0" -ra2 -p85 "103c" "360a"
00:0a.0 "0200" "10de" "0760" -ra2 "103c" "360a"
00:0b.0 "0604" "10de" "0569" -ra1 "" ""
00:14.0 "0604" "10de" "077a" -ra1 "" ""
00:18.0 "0600" "1022" "1300" -r40 "" ""
00:18.1 "0600" "1022" "1301" "" ""
00:18.2 "0600" "1022" "1302" "" ""
00:18.3 "0600" "1022" "1303" "" ""
00:18.4 "0600" "1022" "1304" "" ""
02:00.0 "0300" "10de" "0845" -ra2 "103c" "360a"
07:00.0 "0200" "168c" "001c" -r01 "103c" "137a"


The "lsusb" command gives:  

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



The "dmesg | grep adio" command gives nothing.  Amd I doing something wrong?

---

### Post by pytheas22 on 2009-01-01
Thanks for the information.  I think I know what's wrong.  Could you please post the output of these commands now in order to help figure out how to fix it:
```

lsmod | grep ath
sudo modprobe ath_pci
iwconfig
dmesg | grep -e ath
sudo rmmod ath_pci
sudo modprobe ath9k
iwconfig
```
> 
The "dmesg | grep adio" command gives nothing. Amd I doing something wrong?

No, don't worry about this; it's ok if this command came up blank.

---

### Post by INH on 2009-01-01
lsmod | grep ath:

ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci



sudo modprobe ath_pci came up blank.


iwconfig:  

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



dmesg | grep -e ath:

[   14.311653] ath_hal: module license 'Proprietary' taints kernel.
[   14.337269] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   14.462388] ath_pci: 0.9.4
[   14.462445] ath_pci 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   14.462458] ath_pci 0000:07:00.0: setting latency timer to 64
[   19.636448] ath_pci 0000:07:00.0: PCI INT A disabled



sudo rmmod ath_pci came up blank.


sudo modprobe ath9k came up blank as well.


iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



All of the sudo commands you gave me are coming up blank.  Am I doing something wrong here too, or are they supposed to?


Thanks for your time! :)

---

### Post by pytheas22 on 2009-01-01
Please run these commands (you will need to be plugged into the Internet via ethernet first; if that's impossible, let me know):

```
sudo apt-get update
sudo apt-get install linux-backports-modules-intrepid
```

This will download a new driver for your card.  After you finish with those commands, reboot your computer, and please post the output of:
```

lsmod | grep ath
sudo rmmod ath_pci
sudo rmmod ath9k
sudo rmmod ath5k
sudo modprobe ath5k
sudo iwlist scan
dmesg | grep -e ath -e wlan
```

It's alright if some commands don't return anything; some of them (like 'rmmod') don't unless there's an error.

---

### Post by INH on 2009-01-01
ok, I did that:


lsmod | grep ath:

ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci
ath5k                 106496  0 
lbm_cw_mac80211       210728  1 ath5k
lbm_cw_cfg80211        39696  2 ath5k,lbm_cw_mac80211
led_class              12164  1 ath5k



sudo rmmod ath_pci: 

ERROR: Module ath_pci does not exist in /proc/modules


sudo rmmod ath9k:


ERROR:  Module ath9k does not exist in /proc/modules


sudo rmmod ath5k: blank


sudo modprobe ath5k: blank



sudo iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


dmesg | grep -e ath -e wlan:

[   18.935107] ath5k_pci 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   18.935123] ath5k_pci 0000:07:00.0: setting latency timer to 64
[   18.935180] ath5k_pci 0000:07:00.0: registered as 'phy0'
[   19.452932] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   19.467547] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   19.480656] wlan: 0.9.4
[   19.487735] ath_pci: 0.9.4
[  235.130411] ath_pci: driver unloaded
[  362.735506] ath5k_pci 0000:07:00.0: PCI INT A disabled
[  394.155596] ath5k_pci 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[  394.155629] ath5k_pci 0000:07:00.0: setting latency timer to 64
[  394.155693] ath5k_pci 0000:07:00.0: registered as 'phy1'
[  394.202801] ath5k phy1: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)



I still can't find any wireless networks.  I think I have the driver, though, because it shows up in the Hardware Drivers.  Do I have to turn it on somehow?

---

### Post by pytheas22 on 2009-01-01
hmmm, it looks like you're closer now, but I don't know why it still complains about 'network disabled'.

If you check the box in Hardware Drivers to enable your wireless card, what happens?

---

### Post by INH on 2009-01-01
It already is enabled.  I can disable it if you want.

---

### Post by pytheas22 on 2009-01-01
Let's try using Windows drivers for your card instead of the madwifi/ath5k ones.  Please run these commands:

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz
tar xvf ar5007eg-*.tar.gz
cd ar5007eg*
cd ar5007eg
sudo ndiswrapper -i net5211.inf
ndiswrapper -l
sudo rmmod ath9k
sudo rmmod ath_pci
sudo rmmod ath5k
sudo depmod -a
sudo modprobe ndiswrapper
sudo iwlist scan
dmesg | grep -e ndis -e wlan
```

Please post the output of all of these commands (some of them may have no output) so I can verify that everything completes correctly.

This should install ndiswrapper and get your card working.  If so, we can make the changes permanent (for the time being, rebooting your computer will cause you to default back to your current configuration).

---

### Post by INH on 2009-01-02
Ok, here's the results:

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 55.4kB of archives.
After this operation, 225kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com intrepid/main ndiswrapper-common 1.52-1ubuntu1 [20.2kB]
Get:2 http://us.archive.ubuntu.com intrepid/main ndiswrapper-utils-1.9 1.52-1ubuntu1 [35.1kB]
Fetched 55.4kB in 0s (59.5kB/s)             
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 135376 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.52-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.52-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.52-1ubuntu1) ...


wget http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz

--2009-01-01 23:49:50--  http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz
Resolving blakecmartin.googlepages.com... 74.125.47.118
Connecting to blakecmartin.googlepages.com|74.125.47.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 285621 (279K) [application/octet-stream]
Saving to: `ar5007eg-32-0.2.tar.gz'

100%[======================================>] 285,621      517K/s   in 0.5s    

2009-01-01 23:49:51 (517 KB/s) - `ar5007eg-32-0.2.tar.gz' saved [285621/285621]


tar xvf ar5007eg-*.tar.gz

ar5007eg-32-0.2/
ar5007eg-32-0.2/ar5007eg/
ar5007eg-32-0.2/ar5007eg/net5211.inf
ar5007eg-32-0.2/ar5007eg/ar5211.sys
ar5007eg-32-0.2/README


cd ar5007eg* causes header to change from me@ubuntu:~$ to me@ubuntu:~/ar5007eg-32-0.2$.  


cd ar5007eg adds "ar5007eg$" onto the above stated header.


sudo ndiswrapper -i net5211.inf

installing net5211 ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64


ndiswrapper -l

net5211 : driver installed
	device (168C:001C) present (alternate driver: ath5k)


sudo rmmod ath9k

ERROR: Module ath9k does not exist in /proc/modules


sudo rmmod ath_pci 

ERROR: Module ath_pci does not exist in /proc/modules


sudo rmmod ath5k comes up blank.


sudo depmod -a comes up blank as well.


sudo modprobe ndiswrapper comes up blank again.


sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wlan0     No scan results


dmesg | grep -e ndis -e wlan

[   19.480656] wlan: 0.9.4
[29218.831077] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[29218.874232] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[29218.875714] ndiswrapper 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[29218.875769] ndiswrapper (ZwClose:2198): closing handle 0xdccfa928 not implemented
[29218.875970] ndiswrapper 0000:07:00.0: setting latency timer to 64
[29219.207159] ndiswrapper: using IRQ 23
[29219.414210] wlan0: ethernet device 00:23:4e:5e:b2:de using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[29219.428919] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[29219.434886] usbcore: registered new interface driver ndiswrapper
```

(I use wicd instead of the default Ubuntu network manager, by the way, does that matter?) When I go into wicd, it still shows no wireless networks.

---

### Post by pytheas22 on 2009-01-02
Well, the good news is that it now looks like your wireless interface is up and running properly under ndiswrapper.  The only problem is that it apparently can't see your router, but this isn't necessarily ndiswrapper's fault.

If your router is far from your computer, could you try moving it closer?  Could you also check to see which channel the router is operating on, and see if changing it makes a difference?  Also, if the router is not in 11g mode, try changing it to that.

If ndiswrapper can see your router, you would be able to run these commands:
```

sudo modprobe -r ath9k ath5k ath_pci ndiswrapper
sudo modprobe ndiswrapper
```

and get output from the last command that looks like this:

```

chris@chris-ubuntu-laptop:~$ sudo iwlist scan
[sudo] password for chris: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:56:7D:C8
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=76/100  Signal level:-55 dBm  Noise level=-67 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000043e59aa184
                    Extra: Last beacon: 52ms ago

pan0      Interface doesn't support scanning.
```

But if your router is too far away, on a weird channel or in a mode other than 11g, ndiswrapper may not be able to see it.  Does changing the router settings help at all?

---

### Post by INH on 2009-01-02
I tried that, changing some of the settings, but nothing happened.  Besides, I doubt the router is the problem, since there are about 7 different wireless networks within range of my house.  I would think the card would pick up at least one, if it were working.  

I still think that for some reason the card is working, but not set to receive wireless.  The toggle button next to the power button on my laptop doesn't work, however.  I looked in the BIOS but I can't find any way to turn it on from there either. 

The computer still gives me 0 results for wlan0 when I run the sudo iwlist scan command.

---

### Post by pytheas22 on 2009-01-02
If there are multiple wireless networks within range of your house, then I would agree that the router's not the problem.

If there's a problem with the radio on the wireless card being turned off, dmesg should mention it.  Could you please flip the switch to turn on the card a few times, then post the output of this command:
```

dmesg
```

It will be pretty long, but hopefully it will lead to a solution.

---

### Post by pytheas22 on 2009-01-02
If there are multiple wireless networks within range of your house, then I would agree that the router's not the problem.

If there's a problem with the radio on the wireless card being turned off, dmesg should mention it.  Could you please flip the switch to turn on the card a few times, then post the output of this command:
```

dmesg
```

It will be pretty long, but hopefully it will lead to a solution.

---

### Post by INH on 2009-01-02
You were right, it was pretty long.  I pulled out the part I that I thought was what you were looking for, so you don't have to scroll through all that.  

```
[  103.940662] NET: Registered protocol family 10 
[  103.943138] lo: Disabled Privacy Extensions 
[  103.947422] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[  114.360515] eth0: no IPv6 routers present 
[  260.720039] eth0: no IPv6 routers present 
[  443.490778] ath_pci: driver unloaded 
[  451.716431] ath5k_pci 0000:07:00.0: PCI INT A disabled 
[  477.335340] ndiswrapper version 1.53 loaded (smp=yes, preempt=no) 
[  477.576048] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded 
[  477.576550] ndiswrapper 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23 
[  477.576640] ndiswrapper (ZwClose:2198): closing handle 0xdeca9828 not implemented 
[  477.577070] ndiswrapper 0000:07:00.0: setting latency timer to 64 
[  477.989757] ndiswrapper: using IRQ 23 
[  478.194274] wlan0: ethernet device 00:23:4e:5e:b2:de using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf 
[  478.208561] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK 
[  478.212809] usbcore: registered new interface driver ndiswrapper 
```

And the rest of it, in case that's not what you're looking for:

```
[    0.637778] ACPI: PCI Interrupt Link [Z014] (IRQs 19 20 21 22 23) *0, disabled. 
[    0.638027] ACPI: PCI Interrupt Link [Z015] (IRQs 19 20 21 22 23) *0, disabled. 
[    0.638275] ACPI: PCI Interrupt Link [LSMB] (IRQs 18) *10 
[    0.638521] ACPI: PCI Interrupt Link [LUS0] (IRQs 17) *11 
[    0.638766] ACPI: PCI Interrupt Link [LUS2] (IRQs 17) *7 
[    0.639017] ACPI: PCI Interrupt Link [LMAC] (IRQs 19 20 21 22 23) *11 
[    0.640123] ACPI: PCI Interrupt Link [LAZA] (IRQs 19 20 21 22 23) *10 
[    0.640371] ACPI: PCI Interrupt Link [LGPU] (IRQs 19 20 21 22 23) *10 
[    0.640619] ACPI: PCI Interrupt Link [LPID] (IRQs 19 20 21 22 23) *0, disabled. 
[    0.640866] ACPI: PCI Interrupt Link [LSI0] (IRQs 19 20 21 22 23) *11 
[    0.641113] ACPI: PCI Interrupt Link [LSI1] (IRQs 19 20 21 22 23) *0, disabled. 
[    0.641361] ACPI: PCI Interrupt Link [Z010] (IRQs 16) *5 
[    0.641612] ACPI: PCI Interrupt Link [Z011] (IRQs 16) *10 
[    0.641857] ACPI: PCI Interrupt Link [LPMU] (IRQs 18) *11 
[    0.641934] Linux Plug and Play Support v0.97 (c) Adam Belay 
[    0.641934] pnp: PnP ACPI init 
[    0.641934] ACPI: bus type pnp registered 
[    0.649238] pnp: PnP ACPI: found 12 devices 
[    0.649238] ACPI: ACPI bus type pnp unregistered 
[    0.649238] PnPBIOS: Disabled by ACPI PNP 
[    0.649238] PCI: Using ACPI for IRQ routing 
[    0.652469] NET: Registered protocol family 8 
[    0.652469] NET: Registered protocol family 20 
[    0.652469] NetLabel: Initializing 
[    0.652469] NetLabel:  domain hash size = 128 
[    0.652469] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.652469] NetLabel:  unlabeled traffic allowed by default 
[    0.652469] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31 
[    0.652469] hpet0: 3 32-bit timers, 25000000 Hz 
[    0.653715] tracer: 772 pages allocated for 65536 entries of 48 bytes 
[    0.653718]    actual entries 65620 
[    0.653863] AppArmor: AppArmor Filesystem Enabled 
[    0.653896] ACPI: RTC can wake from S4 
[    0.656048] Switched to high resolution mode on CPU 0 
[    0.656680] Switched to high resolution mode on CPU 1 
[    0.656704] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved 
[    0.656712] system 00:03: ioport range 0x360-0x361 has been reserved 
[    0.656716] system 00:03: ioport range 0x4d0-0x4d1 has been reserved 
[    0.656720] system 00:03: iomem range 0xff800000-0xff800fff has been reserved 
[    0.656731] system 00:0a: ioport range 0x1000-0x107f has been reserved 
[    0.656734] system 00:0a: ioport range 0x1080-0x10ff has been reserved 
[    0.656737] system 00:0a: ioport range 0x1200-0x127f has been reserved 
[    0.656741] system 00:0a: ioport range 0x1280-0x12ff has been reserved 
[    0.656744] system 00:0a: ioport range 0x1400-0x147f has been reserved 
[    0.656747] system 00:0a: ioport range 0x1480-0x14ff has been reserved 
[    0.656755] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved 
[    0.656759] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved 
[    0.656762] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved 
[    0.656766] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved 
[    0.656770] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved 
[    0.692448] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01 
[    0.692451] pci 0000:00:08.0:   IO window: disabled 
[    0.692457] pci 0000:00:08.0:   MEM window: disabled 
[    0.692461] pci 0000:00:08.0:   PREFETCH window: disabled 
[    0.692470] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02 
[    0.692474] pci 0000:00:0b.0:   IO window: 0x4000-0x4fff 
[    0.692479] pci 0000:00:0b.0:   MEM window: 0xc1000000-0xc1ffffff 
[    0.692483] pci 0000:00:0b.0:   PREFETCH window: 0x000000c4000000-0x000000dfffffff 
[    0.692723] pci 0000:00:14.0: PCI bridge, secondary bus 0000:07 
[    0.692726] pci 0000:00:14.0:   IO window: disabled 
[    0.692737] pci 0000:00:14.0:   MEM window: 0xc2000000-0xc20fffff 
[    0.692746] pci 0000:00:14.0:   PREFETCH window: disabled 
[    0.692768] pci 0000:00:08.0: setting latency timer to 64 
[    0.692776] pci 0000:00:0b.0: setting latency timer to 64 
[    0.693241] ACPI: PCI Interrupt Link [Z012] enabled at IRQ 23 
[    0.693254] pci 0000:00:14.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23 
[    0.693263] pci 0000:00:14.0: setting latency timer to 64 
[    0.693270] bus: 00 index 0 io port: [0, ffff] 
[    0.693272] bus: 00 index 1 mmio: [0, ffffffff] 
[    0.693275] bus: 01 index 0 mmio: [0, 0] 
[    0.693277] bus: 01 index 1 mmio: [0, 0] 
[    0.693279] bus: 01 index 2 mmio: [0, 0] 
[    0.693282] bus: 01 index 3 io port: [0, ffff] 
[    0.693284] bus: 01 index 4 mmio: [0, ffffffff] 
[    0.693287] bus: 02 index 0 io port: [4000, 4fff] 
[    0.693289] bus: 02 index 1 mmio: [c1000000, c1ffffff] 
[    0.693292] bus: 02 index 2 mmio: [c4000000, dfffffff] 
[    0.693294] bus: 02 index 3 mmio: [0, 0] 
[    0.693297] bus: 07 index 0 mmio: [0, 0] 
[    0.693299] bus: 07 index 1 mmio: [c2000000, c20fffff] 
[    0.693301] bus: 07 index 2 mmio: [0, 0] 
[    0.693304] bus: 07 index 3 mmio: [0, 0] 
[    0.693318] NET: Registered protocol family 2 
[    0.705414] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[    0.705722] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.706407] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[    0.706735] TCP: Hash tables configured (established 131072 bind 65536) 
[    0.706739] TCP reno registered 
[    0.709228] NET: Registered protocol family 1 
[    0.709363] checking if image is initramfs... it is 
[    1.478353] Freeing initrd memory: 8263k freed 
[    1.478533] Simple Boot Flag at 0x38 set to 0x1 
[    1.480259] audit: initializing netlink socket (disabled) 
[    1.480276] type=2000 audit(1230914595.480:1): initialized 
[    1.486713] highmem bounce pool size: 64 pages 
[    1.486720] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[    1.489881] VFS: Disk quotas dquot_6.5.1 
[    1.489993] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    1.490120] msgmni has been set to 1730 
[    1.490267] io scheduler noop registered 
[    1.490270] io scheduler anticipatory registered 
[    1.490273] io scheduler deadline registered 
[    1.490286] io scheduler cfq registered (default) 
[    1.490710] pci 0000:00:07.0: Enabling HT MSI Mapping 
[    1.490746] pci 0000:00:08.0: Enabling HT MSI Mapping 
[    1.490784] pci 0000:00:09.0: Enabling HT MSI Mapping 
[    1.490822] pci 0000:00:0a.0: Enabling HT MSI Mapping 
[    1.490857] pci 0000:00:0b.0: Enabling HT MSI Mapping 
[    1.490922] pci 0000:00:14.0: Enabling HT MSI Mapping 
[    1.490975] pci 0000:02:00.0: Boot video device 
[    1.491167] pcieport-driver 0000:00:14.0: setting latency timer to 64 
[    1.491358] pcieport-driver 0000:00:14.0: found MSI capability 
[    1.491489] pci_express 0000:00:14.0:pcie00: allocate port service 
[    1.492188] isapnp: Scanning for PnP cards... 
[    1.501010] Clocksource tsc unstable (delta = 4397482803738 ns) 
[    1.845250] isapnp: No Plug & Play device found 
[    1.894772] hpet_resources: 0xfed00000 is busy 
[    1.894887] Serial: 8250/16550 driver4 ports, IRQ sharing enabled 
[    1.898563] brd: module loaded 
[    1.898662] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
[    1.898842] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[    1.917449] i8042.c: Detected active multiplexing controller, rev 1.1. 
[    1.929531] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    1.929539] serio: i8042 AUX0 port at 0x60,0x64 irq 12 
[    1.929542] serio: i8042 AUX1 port at 0x60,0x64 irq 12 
[    1.929546] serio: i8042 AUX2 port at 0x60,0x64 irq 12 
[    1.929549] serio: i8042 AUX3 port at 0x60,0x64 irq 12 
[    1.930053] mice: PS/2 mouse device common for all mice 
[    1.930241] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0 
[    1.930298] rtc0: alarms up to one year, y3k, hpet irqs 
[    1.930470] EISA: Probing bus 0 at eisa.0 
[    1.930477] Cannot allocate resource for EISA slot 1 
[    1.930482] Cannot allocate resource for EISA slot 3 
[    1.930485] Cannot allocate resource for EISA slot 4 
[    1.930499] EISA: Detected 0 cards. 
[    1.930503] cpuidle: using governor ladder 
[    1.930506] cpuidle: using governor menu 
[    1.931051] TCP cubic registered 
[    1.931082] Using IPI No-Shortcut mode 
[    1.931408] registered taskstats version 1 
[    1.931567]   Magic number: 9:498:741 
[    1.931794] rtc_cmos 00:06: setting system clock to 2009-01-02 16:43:17 UTC (1230914597) 
[    1.931798] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    1.931801] EDD information not available. 
[    1.932115] Freeing unused kernel memory: 424k freed 
[    1.932186] Write protecting the kernel text: 2576k 
[    1.932234] Write protecting the kernel read-only data: 936k 
[    1.953210] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
[    2.250110] fuse init (API version 7.9) 
[    2.304288] processor ACPI0007:00: registered as cooling_device0 
[    2.304370] processor ACPI0007:01: registered as cooling_device1 
[    2.422323] thermal LNXTHERM:01: registered as thermal_zone0 
[    2.435841] ACPI: Thermal Zone [TZS0] (59 C) 
[    2.442467] thermal LNXTHERM:02: registered as thermal_zone1 
[    2.447765] ACPI: Thermal Zone [TZS1] (59 C) 
[    2.960808] usbcore: registered new interface driver usbfs 
[    2.960837] usbcore: registered new interface driver hub 
[    2.960923] usbcore: registered new device driver usb 
[    2.976633] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 17 
[    2.976648] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 17 (level, low) -> IRQ 17 
[    2.976662] ehci_hcd 0000:00:02.1: setting latency timer to 64 
[    2.976666] ehci_hcd 0000:00:02.1: EHCI Host Controller 
[    2.976720] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1 
[    2.976754] ehci_hcd 0000:00:02.1: debug port 1 
[    2.976760] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported 
[    2.976780] ehci_hcd 0000:00:02.1: irq 17, io mem 0xc0007000 
[    2.980880] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver 
[    2.982839] No dock devices found. 
[    2.997064] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[    2.997254] usb usb1: configuration #1 chosen from 1 choice 
[    2.997284] hub 1-0:1.0: USB hub found 
[    2.997297] hub 1-0:1.0: 3 ports detected 
[    3.008479] SCSI subsystem initialized 
[    3.062398] libata version 3.00 loaded. 
[    3.100803] ACPI: PCI Interrupt Link [Z011] enabled at IRQ 16 
[    3.100818] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z011] -> GSI 16 (level, low) -> IRQ 16 
[    3.100833] ehci_hcd 0000:00:04.1: setting latency timer to 64 
[    3.100837] ehci_hcd 0000:00:04.1: EHCI Host Controller 
[    3.100865] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2 
[    3.100898] ehci_hcd 0000:00:04.1: debug port 1 
[    3.100904] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported 
[    3.100924] ehci_hcd 0000:00:04.1: irq 16, io mem 0xc0007400 
[    3.112028] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[    3.112213] usb usb2: configuration #1 chosen from 1 choice 
[    3.112244] hub 2-0:1.0: USB hub found 
[    3.112255] hub 2-0:1.0: 4 ports detected 
[    3.216828] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 17 
[    3.216835] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 17 (level, low) -> IRQ 17 
[    3.216851] ohci_hcd 0000:00:02.0: setting latency timer to 64 
[    3.216855] ohci_hcd 0000:00:02.0: OHCI Host Controller 
[    3.216883] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3 
[    3.216900] ohci_hcd 0000:00:02.0: irq 17, io mem 0xc0006000 
[    3.274210] usb usb3: configuration #1 chosen from 1 choice 
[    3.274243] hub 3-0:1.0: USB hub found 
[    3.274256] hub 3-0:1.0: 3 ports detected 
[    3.376850] ACPI: PCI Interrupt Link [Z010] enabled at IRQ 16 
[    3.376857] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z010] -> GSI 16 (level, low) -> IRQ 16 
[    3.376875] ohci_hcd 0000:00:04.0: setting latency timer to 64 
[    3.376879] ohci_hcd 0000:00:04.0: OHCI Host Controller 
[    3.376911] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4 
[    3.376932] ohci_hcd 0000:00:04.0: irq 16, io mem 0xc0008000 
[    3.434210] usb usb4: configuration #1 chosen from 1 choice 
[    3.434247] hub 4-0:1.0: USB hub found 
[    3.434261] hub 4-0:1.0: 4 ports detected 
[    3.536490] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61. 
[    3.536943] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22 
[    3.536959] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22 
[    3.536966] forcedeth 0000:00:0a.0: setting latency timer to 64 
[    4.057087] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:16:55:6e:07 
[    4.057093] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq lnktim msi desc-v3 
[    4.062230] pata_acpi 0000:00:06.0: setting latency timer to 64 
[    4.062696] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 21 
[    4.062710] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 21 (level, low) -> IRQ 21 
[    4.062730] pata_acpi 0000:00:09.0: setting latency timer to 64 
[    4.062740] pata_acpi 0000:00:09.0: PCI INT A disabled 
[    4.068898] ahci 0000:00:09.0: version 3.0 
[    4.068920] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 21 (level, low) -> IRQ 21 
[    4.069036] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 2 ports 3 Gbps 0x3 impl IDE mode 
[    4.069041] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio slum part 
[    4.069048] ahci 0000:00:09.0: setting latency timer to 64 
[    4.069263] scsi0 : ahci 
[    4.069384] scsi1 : ahci 
[    4.069470] ata1: SATA max UDMA/133 abar m8192@0xc0004000 port 0xc0004100 irq 222 
[    4.069474] ata2: SATA max UDMA/133 abar m8192@0xc0004000 port 0xc0004180 irq 222 
[    4.552026] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[    4.567287] ata1.00: ATAPI: Slimtype DVD A  DS8A2S-A, 6H63, max UDMA/100 
[    4.584051] ata1.00: configured for UDMA/100 
[    5.472024] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300) 
[    5.472784] ata2.00: ATA-8: ST9160827AS, 3.AHC, max UDMA/100 
[    5.472788] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32) 
[    5.473210] ata2.00: configured for UDMA/100 
[    5.476068] scsi 0:0:0:0: CD-ROM            Slimtype DVD A  DS8A2S-A  6H63 PQ: 0 ANSI: 5 
[    5.476254] scsi 1:0:0:0: Direct-Access     ATA      ST9160827AS      3.AH PQ: 0 ANSI: 5 
[    5.476443] pata_amd 0000:00:06.0: version 0.3.10 
[    5.476496] pata_amd 0000:00:06.0: setting latency timer to 64 
[    5.476621] scsi2 : pata_amd 
[    5.476707] scsi3 : pata_amd 
[    5.476748] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14 
[    5.476751] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15 
[    5.487398] scsi 0:0:0:0: Attached scsi generic sg0 type 5 
[    5.487445] scsi 1:0:0:0: Attached scsi generic sg1 type 0 
[    5.503907] Driver 'sd' needs updating - please use bus_type methods 
[    5.504082] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB) 
[    5.504108] sd 1:0:0:0: [sda] Write Protect is off 
[    5.504111] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    5.504150] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    5.504233] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB) 
[    5.504254] sd 1:0:0:0: [sda] Write Protect is off 
[    5.504257] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    5.504293] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    5.504298]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
[    5.524157] sr0: scsi3-mmc drive: 24x/6x writer dvd-ram cd/rw xa/form2 cdda pop-up 
[    5.524163] Uniform CD-ROM driver Revision: 3.20 
[    5.524265] sr 0:0:0:0: Attached scsi CD-ROM sr0 
[    5.552256]  sda1 sda2 
[    5.552406] sd 1:0:0:0: [sda] Attached SCSI disk 
[    5.632556] ata4: port disabled. ignoring. 
[    6.399919] loop: module loaded 
[    6.441674] kjournald starting.  Commit interval 5 seconds 
[    6.441690] EXT3-fs: mounted filesystem with ordered data mode. 
[   12.676980] udevd version 124 started 
[   13.040247] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2 
[   13.069045] ACPI: Power Button (FF) [PWRF] 
[   13.069153] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3 
[   13.070683] ACPI: Lid Switch [LID0] 
[   13.070777] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4 
[   13.085055] ACPI: Sleep Button (CM) [SLPB] 
[   13.085234] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5 
[   13.117043] ACPI: Power Button (CM) [PWRB] 
[   13.204285] ACPI: WMI: Mapper loaded 
[   13.795052] acpi device:0d: registered as cooling_device2 
[   13.795296] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0a/device:0b/input/input6 
[   13.820037] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no) 
[   13.993282] ACPI: AC Adapter [ADP1] (off-line) 
[   14.124192] ACPI: Battery Slot [BAT0] (battery present) 
[   14.189212] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   14.248248] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   14.386661] input: PC Speaker as /devices/platform/pcspkr/input/input7 
[   14.641405] Linux agpgart interface v0.103 
[   14.671374] cfg80211: Using static regulatory domain info 
[   14.671379] cfg80211: Regulatory domain: US 
[   14.671381] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   14.671385] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm) 
[   14.671388] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm) 
[   14.671391] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm) 
[   14.671394] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm) 
[   14.671397] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm) 
[   14.671400] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm) 
[   14.671403] cfg80211: Calling CRDA for country: US 
[   15.029845] nvidia: module license 'NVIDIA' taints kernel. 
[   15.290012] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 20 
[   15.290027] nvidia 0000:02:00.0: PCI INT A -> Link[LGPU] -> GSI 20 (level, low) -> IRQ 20 
[   15.290035] nvidia 0000:02:00.0: setting latency timer to 64 
[   15.290335] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008 
[   15.398850] ath5k_pci 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23 
[   15.398866] ath5k_pci 0000:07:00.0: setting latency timer to 64 
[   15.398906] ath5k_pci 0000:07:00.0: registered as 'phy0' 
[   15.439928] phy0: Selected rate control algorithm 'pid' 
[   15.539163] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa00000 
[   15.601128] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input8 
[   15.957327] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70) 
[   15.972147] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413) 
[   16.005235] wlan: 0.9.4 
[   16.022263] ath_pci: 0.9.4 
[   16.078168] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 19 
[   16.078183] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 19 (level, low) -> IRQ 19 
[   16.078218] HDA Intel 0000:00:07.0: setting latency timer to 64 
[   16.755545] lp: driver loaded but no devices found 
[   16.913043] EXT3 FS on loop0, internal journal 
[   36.208111] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k 
[   36.602051] type=1505 audit(1230932632.061:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4136 
[   36.817716] type=1505 audit(1230932632.278:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4141 
[   36.817982] type=1505 audit(1230932632.278:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4141 
[   36.978597] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   37.761308] powernow-k8: Found 1 AMD Athlon Dual-Core QL-60 processors (2 cpu cores) (version 2.20.00) 
[   37.761371] powernow-k8:    0 : pstate 0 (1900 MHz) 
[   37.761376] powernow-k8:    1 : pstate 1 (1000 MHz) 
[   38.480721] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use) 
[   38.565651] apm: BIOS not found. 
[   38.723404] ppdev: user-space parallel port driver 
[   41.097122] Bluetooth: Core ver 2.13 
[   41.098979] NET: Registered protocol family 31 
[   41.098991] Bluetooth: HCI device and connection manager initialized 
[   41.099000] Bluetooth: HCI socket layer initialized 
[   41.142126] Bluetooth: L2CAP ver 2.11 
[   41.142142] Bluetooth: L2CAP socket layer initialized 
[   41.182658] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   41.182675] Bluetooth: BNEP filters: protocol multicast 
[   41.373809] Bridge firewalling registered 
[   41.374087] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature. 
[   41.390624] Bluetooth: RFCOMM socket layer initialized 
[   41.391121] Bluetooth: RFCOMM TTY layer initialized 
[   41.391133] Bluetooth: RFCOMM ver 1.10 
[   41.412927] Bluetooth: SCO (Voice Link) ver 0.6 
[   41.412941] Bluetooth: SCO socket layer initialized 
[   45.780750] NET: Registered protocol family 17 
[   91.332846] CPU0 attaching NULL sched-domain. 
[   91.332868] CPU1 attaching NULL sched-domain. 
[   91.336321] CPU0 attaching sched-domain: 
[   91.336334]  domain 0: span 0-1 level MC 
[   91.336341]   groups: 0 1 
[   91.336351]   domain 1: span 0-1 level CPU 
[   91.336356]    groups: 0-1 
[   91.336366] CPU1 attaching sched-domain: 
[   91.336370]  domain 0: span 0-1 level MC 
[   91.336375]   groups: 1 0 
[   91.336382]   domain 1: span 0-1 level CPU 
[   91.336387]    groups: 0-1 
[  103.940662] NET: Registered protocol family 10 
[  103.943138] lo: Disabled Privacy Extensions 
[  103.947422] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[  114.360515] eth0: no IPv6 routers present 
[  260.720039] eth0: no IPv6 routers present 
[  443.490778] ath_pci: driver unloaded 
[  451.716431] ath5k_pci 0000:07:00.0: PCI INT A disabled 
[  477.335340] ndiswrapper version 1.53 loaded (smp=yes, preempt=no) 
[  477.576048] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded 
[  477.576550] ndiswrapper 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23 
[  477.576640] ndiswrapper (ZwClose:2198): closing handle 0xdeca9828 not implemented 
[  477.577070] ndiswrapper 0000:07:00.0: setting latency timer to 64 
[  477.989757] ndiswrapper: using IRQ 23 
[  478.194274] wlan0: ethernet device 00:23:4e:5e:b2:de using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf 
[  478.208561] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK 
[  478.212809] usbcore: registered new interface driver ndiswrapper 
[ 1170.220318] eth0: link down. 
[ 1173.689439] eth0: link up. 
[ 1359.477982] eth0: link down. 
[ 1394.860030] usb 2-1: new high speed USB device using ehci_hcd and address 2 
[ 1394.993862] usb 2-1: configuration #1 chosen from 1 choice 
[ 1394.995825] hub 2-1:1.0: USB hub found 
[ 1394.996887] hub 2-1:1.0: 4 ports detected 
[ 1395.292747] usb 2-1.4: new low speed USB device using ehci_hcd and address 3 
[ 1395.409856] usb 2-1.4: configuration #1 chosen from 1 choice 
[ 1395.521203] usbcore: registered new interface driver hiddev 
[ 1395.531639] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.1/usb2/2-1/2-1.4/2-1.4:1.0/input/input9 
[ 1395.549502] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:04.1-1.4 
[ 1395.550211] usbcore: registered new interface driver usbhid 
[ 1395.550624] usbhid: v2.6:USB HID core driver 
[ 1395.572234] usbcore: registered new interface driver lmpcm_usb 
[ 1395.573225] lmpcm_usb: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver 
[ 1396.949384] CPU0 attaching NULL sched-domain. 
[ 1396.949402] CPU1 attaching NULL sched-domain. 
[ 1396.972092] CPU0 attaching sched-domain: 
[ 1396.972100]  domain 0: span 0-1 level CPU 
[ 1396.972103]   groups: 0 1 
[ 1396.972109] CPU1 attaching sched-domain: 
[ 1396.972112]  domain 0: span 0-1 level CPU 
[ 1396.972114]   groups: 1 0 
[11626.077755] usb 2-1: USB disconnect, address 2 
[11626.077767] usb 2-1.4: USB disconnect, address 3 
[11627.903611] CPU0 attaching NULL sched-domain. 
[11627.903633] CPU1 attaching NULL sched-domain. 
[11627.909110] CPU0 attaching sched-domain: 
[11627.909121]  domain 0: span 0-1 level MC 
[11627.909129]   groups: 0 1 
[11627.909139]   domain 1: span 0-1 level CPU 
[11627.909145]    groups: 0-1 
[11627.909154] CPU1 attaching sched-domain: 
[11627.909158]  domain 0: span 0-1 level MC 
[11627.909163]   groups: 1 0 
[11627.909170]   domain 1: span 0-1 level CPU 
[11627.909177]    groups: 0-1 
[11676.026483] eth0: link up. 
[12096.912630] eth0: link down. 
[13396.963117] CPU0 attaching NULL sched-domain. 
[13396.963132] CPU1 attaching NULL sched-domain. 
[13396.965092] CPU0 attaching sched-domain: 
[13396.965101]  domain 0: span 0-1 level CPU 
[13396.965104]   groups: 0 1 
[13396.965111] CPU1 attaching sched-domain: 
[13396.965113]  domain 0: span 0-1 level CPU 
[13396.965116]   groups: 1 0 
[13406.223882] eth0: link up. 
[15287.756197] eth0: link down. 
[15291.484814] CPU0 attaching NULL sched-domain. 
[15291.484840] CPU1 attaching NULL sched-domain. 
[15291.496719] CPU0 attaching sched-domain: 
[15291.496731]  domain 0: span 0-1 level MC 
[15291.496737]   groups: 0 1 
[15291.496747]   domain 1: span 0-1 level CPU 
[15291.496753]    groups: 0-1 
[15291.496761] CPU1 attaching sched-domain: 
[15291.496766]  domain 0: span 0-1 level MC 
[15291.496770]   groups: 1 0 
[15291.496778]   domain 1: span 0-1 level CPU 
[15291.496782]    groups: 0-1 
[15349.037044] usb 2-1: new high speed USB device using ehci_hcd and address 4 
[15349.170603] usb 2-1: configuration #1 chosen from 1 choice 
[15349.171044] hub 2-1:1.0: USB hub found 
[15349.171180] hub 2-1:1.0: 4 ports detected 
[15349.464467] usb 2-1.4: new low speed USB device using ehci_hcd and address 5 
[15349.583562] usb 2-1.4: configuration #1 chosen from 1 choice 
[15349.601794] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.1/usb2/2-1/2-1.4/2-1.4:1.0/input/input10 
[15349.648989] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:04.1-1.4 
[15354.619920] CPU0 attaching NULL sched-domain. 
[15354.619940] CPU1 attaching NULL sched-domain. 
[15354.625096] CPU0 attaching sched-domain: 
[15354.625105]  domain 0: span 0-1 level CPU 
[15354.625109]   groups: 0 1 
[15354.625116] CPU1 attaching sched-domain: 
[15354.625121]  domain 0: span 0-1 level CPU 
[15354.625124]   groups: 1 0 
```

---

### Post by pytheas22 on 2009-01-03
Unfortunately I don't see anything that concretely explains why the radio on the wireless card seems to be off.  But please try these two things:

1. run these commands:
```

echo 'blacklist ath_pci' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist ath9k' | sudo tee -a /etc/modprobe.d/blacklist
echo 'blacklist ath5k' | sudo tee -a /etc/modprobe.d/blacklist
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot.  Does the wireless work now by any chance?  If not, please post the output of:
```

dmesg | grep -e ath -e wlan -e ndis -e abled
```

2. try powering off the machine completely (not hibernating or suspending), then unplug the power cable, and remove the battery if applicable.  Hold the power button down for thirty seconds, then wait a few minutes.  After five minutes, plug the computer back in, turn it on and boot directly to Ubuntu (don't boot to Windows at all until after you've booted into Ubuntu).  Does this help?  If not, what is the output of:
```

dmesg | grep abled
```

There are certain ethernet cards that Windows puts to sleep and Ubuntu can't wake up; cutting off all power so that they're forced to reset themselves is the only way to fix the problem.  I'm wondering if the same issue is happening with your wireless card.

---

### Post by INH on 2009-01-03
Neither of those worked, unfortunately.

```
dmesg | grep -e ath -e wlan -e ndis -e abled
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.004000] console [tty0] enabled
[    0.004000] SELinux:  Disabled at boot.
[    0.537311] ACPI: Interpreter enabled
[    0.608374] pci 0000:00:01.1: PME# disabled
[    0.608597] pci 0000:00:02.0: PME# disabled
[    0.608674] pci 0000:00:02.1: PME# disabled
[    0.608748] pci 0000:00:04.0: PME# disabled
[    0.608828] pci 0000:00:04.1: PME# disabled
[    0.608967] pci 0000:00:07.0: PME# disabled
[    0.609173] pci 0000:00:0a.0: PME# disabled
[    0.609220] pci 0000:00:0b.0: PME# disabled
[    0.609432] pci 0000:00:14.0: PME# disabled
[    0.639018] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.639273] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.639523] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.639772] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.640282] ACPI: PCI Interrupt Link [Z013] (IRQs 19 20 21 22 23) *0, disabled.
[    0.640531] ACPI: PCI Interrupt Link [Z014] (IRQs 19 20 21 22 23) *0, disabled.
[    0.640781] ACPI: PCI Interrupt Link [Z015] (IRQs 19 20 21 22 23) *0, disabled.
[    0.642524] ACPI: PCI Interrupt Link [LPID] (IRQs 19 20 21 22 23) *0, disabled.
[    0.643023] ACPI: PCI Interrupt Link [LSI1] (IRQs 19 20 21 22 23) *0, disabled.
[    0.649335] PnPBIOS: Disabled by ACPI PNP
[    0.657865] AppArmor: AppArmor Filesystem Enabled
[    0.696938] pci 0000:00:08.0:   IO window: disabled
[    0.696944] pci 0000:00:08.0:   MEM window: disabled
[    0.696948] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.697228] pci 0000:00:14.0:   IO window: disabled
[    0.697248] pci 0000:00:14.0:   PREFETCH window: disabled
[    0.697718] ACPI: PCI Interrupt Link [Z012] enabled at IRQ 23
[    1.483978] audit: initializing netlink socket (disabled)
[    1.898145] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.110158] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 17
[    3.268959] ACPI: PCI Interrupt Link [Z010] enabled at IRQ 16
[    3.429860] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 17
[    3.545789] ACPI: PCI Interrupt Link [Z011] enabled at IRQ 16
[    3.661895] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    4.188772] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 21
[    4.188816] pata_acpi 0000:00:09.0: PCI INT A disabled
[    4.364670] ata2: port disabled. ignoring.
[    6.194114] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.194252] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.868744] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   15.627554] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 19
[   17.065227] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   17.163477] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   17.163790] ndiswrapper 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   17.163845] ndiswrapper (ZwClose:2198): closing handle 0xf1167a28 not implemented
[   17.164041] ndiswrapper 0000:07:00.0: setting latency timer to 64
[   17.576486] ndiswrapper: using IRQ 23
[   17.780851] wlan0: ethernet device 00:23:4e:5e:b2:de using serialized NDIS driver: net5211, version: 0x50001, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   17.785521] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   17.786075] usbcore: registered new interface driver ndiswrapper
[  876.270537] lo: Disabled Privacy Extensions

dmesg | grep abled
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.004000] console [tty0] enabled
[    0.004000] SELinux:  Disabled at boot.
[    0.537311] ACPI: Interpreter enabled
[    0.608374] pci 0000:00:01.1: PME# disabled
[    0.608597] pci 0000:00:02.0: PME# disabled
[    0.608674] pci 0000:00:02.1: PME# disabled
[    0.608748] pci 0000:00:04.0: PME# disabled
[    0.608828] pci 0000:00:04.1: PME# disabled
[    0.608967] pci 0000:00:07.0: PME# disabled
[    0.609173] pci 0000:00:0a.0: PME# disabled
[    0.609220] pci 0000:00:0b.0: PME# disabled
[    0.609432] pci 0000:00:14.0: PME# disabled
[    0.639018] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.639273] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.639523] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.639772] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.640282] ACPI: PCI Interrupt Link [Z013] (IRQs 19 20 21 22 23) *0, disabled.
[    0.640531] ACPI: PCI Interrupt Link [Z014] (IRQs 19 20 21 22 23) *0, disabled.
[    0.640781] ACPI: PCI Interrupt Link [Z015] (IRQs 19 20 21 22 23) *0, disabled.
[    0.642524] ACPI: PCI Interrupt Link [LPID] (IRQs 19 20 21 22 23) *0, disabled.
[    0.643023] ACPI: PCI Interrupt Link [LSI1] (IRQs 19 20 21 22 23) *0, disabled.
[    0.649335] PnPBIOS: Disabled by ACPI PNP
[    0.657865] AppArmor: AppArmor Filesystem Enabled
[    0.696938] pci 0000:00:08.0:   IO window: disabled
[    0.696944] pci 0000:00:08.0:   MEM window: disabled
[    0.696948] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.697228] pci 0000:00:14.0:   IO window: disabled
[    0.697248] pci 0000:00:14.0:   PREFETCH window: disabled
[    0.697718] ACPI: PCI Interrupt Link [Z012] enabled at IRQ 23
[    1.483978] audit: initializing netlink socket (disabled)
[    1.898145] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.110158] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 17
[    3.268959] ACPI: PCI Interrupt Link [Z010] enabled at IRQ 16
[    3.429860] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 17
[    3.545789] ACPI: PCI Interrupt Link [Z011] enabled at IRQ 16
[    3.661895] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    4.188772] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 21
[    4.188816] pata_acpi 0000:00:09.0: PCI INT A disabled
[    4.364670] ata2: port disabled. ignoring.
[    6.194114] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.194252] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.868744] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   15.627554] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 19
[  876.270537] lo: Disabled Privacy Extensions

```

I wonder if there's something really simple that I'm missing here, that any experience Ubuntu user would figure out in like 10 seconds...

---

### Post by pytheas22 on 2009-01-04
Unfortunately I'm still entirely puzzled as to what's wrong.  The only other thing I can think of that could possibly be at fault here is some kind of IRQ conflict--there are several lines in dmesg mentioning various IRQs being disabled.  You should probably have some different options in BIOS regarding IRQ configuration; does playing around with them make any difference?

You may also want to boot to Windows and see if there's an option anywhere for forcing the radio on your wireless card to be always on.

---

### Post by INH on 2009-01-04
I can't find any IRQ configure settings in my BIOS.  

I can't find anything in Windows to help either.  It's so hard to get below skin-deep in Vista.  In making if more newbie-friendly, Microsoft made it a lot less non-newbie-friendly.  *sigh*  

I still think this problem is linked to the way the on/off button works with Windows, though.

---

### Post by INH on 2009-01-05
New development:  I don't know if this means anything, but I installed the latest atheros 5007 Madwifi drivers, and now, when I run modprobe or rmmod, it doesn't pop up with error messages about the modules being nonexistant for ath_pci and ath9k. (hope that made sense.)

---

### Post by pytheas22 on 2009-01-05
How exactly does the switch work in Windows?  And what is the exact model of your laptop?
> 
I don't know if this means anything, but I installed the latest atheros 5007 Madwifi drivers, and now, when I run modprobe or rmmod, it doesn't pop up with error messages about the modules being nonexistant for ath_pci and ath9k. (hope that made sense.)

Do you just mean that you no longer get the error messages that look like:
```

sudo modprobe -r ath_pci
ERROR: module ath_pci does not exist in /proc/modules
```

If so, that's unfortunately nothing to get excited about; this error message doesn't relate to your problem.

But if you meant something else, please explain in more detail.

---

### Post by INH on 2009-01-05
The switch is a button, rather than an actual hard switch.  I assume this means it is a "soft" switch rather than a "hard" switch, and the software for it isn't present in Ubuntu.  In Windows, when I press the button to turn the wireless on, the LED light changes from red to blue, and I can connect to wireless networks.  When I press the button again, the light changes from blue to red, and the internet connection icon in my system tray shows a red X and pops up a balloon saying that it's not connected.

As for the error messages, yeah, that's what happens; I no longer get those error messages. Now it just comes up blank, like it did before when I modprobed ath5k.

---

### Post by pytheas22 on 2009-01-06
Usually Ubuntu has no problem with software switches for wireless radio, although sometimes APCI issues get in the way.  In my experience, however, dmesg always at least mentions something about the radio if it's preventing your card from working--but maybe your driver doesn't have that ability.

What is the exact model of your laptop?

---

### Post by INH on 2009-01-06
My laptop is a Compaq Presario CQ50-215NR.  The exact specs can be found [here](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01555875&lc=en&dlc=en&cc=us&lang=en&product=3795238), although I have upgraded the RAM from 2 to 3 GB.

---

### Post by pytheas22 on 2009-01-06
I did some googling for your laptop model.  The only page that I could find that seems relevant is [here]("http://ubuntuforums.org/archive/index.php/t-940830.html"), where another user says that no matter what he tried, he couldn't even see wireless networks.

Installing ath9k drivers using the shell script in post #3 here apparently solved the problem for him.  Could you give that a try?

After running the script, you should make sure that the ath9k driver is not blacklisted.  To do that, type:
```

sudo gedit /etc/modprobe.d/blacklist
```

A file will open.  Remove any lines that say:
```

blacklist ath9k
```

or similar.

After that, reboot.  Do you have any luck seeing networks now by typing:
```

sudo iwlist scan
```

---

### Post by INH on 2009-01-06
Good news!  I got it working!  It was ridiculously simple, too... all I did was open Wicd and open the Preferences window.  The wired interface there was set as 'eth0', but there was nothing in the box for wireless, so I put in 'wlan0', closed the window, and voila!  Networks!  Not believing my eyes, I hit the 'refresh' button... and they all disappeared.  After a moment of bugged-out eyes and internal anguish, it suddenly  burst upon me that maybe I needed to reboot the computer.  I did, and it worked!  I connected to my wireless network and am now happy.  I have to say, though, I couldn't have done it without your help.  All those hours spend typing commands that you gave me, and reading the outputs, gave me the knowledge that, first, I needed to put 'wlan0' in the wireless interface box, and again, after that had worked and apparently stopped working, that I needed to reboot the computer.  You have my heartfelt thanks for all the time and effort you spent with me on this forum, even though it turned out to be (somewhat) wasted.  So, thanks again, and I'll be seeing you! :)

---

### Post by pytheas22 on 2009-01-07
I'm really glad to hear it's solved :)

I admit that I'm left a little perplexed as to why wicd could see networks while the 'sudo iwlist scan' command seemed always to come up blank.  But I guess that's irrelevant now.  Have fun with Ubuntu!

---

### Post by INH on 2009-01-07
Actually, 'sudo iwlist scan' now works.  I tried it last night.  I guess it was all in the wireless interface.

---

