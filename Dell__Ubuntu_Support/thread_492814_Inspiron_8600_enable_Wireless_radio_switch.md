---
title: "Inspiron 8600 enable Wireless radio switch"
date: 2007-07-05
forum: Dell  Ubuntu Support
---

### Post by leivae on 2007-07-05
I have just installed Ubuntu 7.04 on my Dell Inspiron 8600 and it works beutifully, EXCEPT I can't seem to get the Wireless radio working. Listing the hardware it shows up but as DISABLED. Using the <Fn>+<F2>, which is the normal way of switching the radio on/off has no effect. Does anyone have any solution for me?

PS:  I am totallt new to Linux and will need a "tea spoon" approach ;)

---

### Post by sj3fk3 on 2007-07-05
Step 1: Read: [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
Step 2: Read: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
(you **should** be using WPA)

After that see if you still can't get it to work. If you still can't get it to work open a terminal and type lspci <enter? and iwconfig <enter> and paste the output here.

---

### Post by leivae on 2007-07-05
Hi,
I tried to follow the instructions but came shrt as I could not find my device in the Networking GUI (eth1). I have the following output for you:


From lshw command:
*-network:1 DISABLED
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@02:03.0
                logical name: eth1
                version: 03
                serial: 00:0b:7d:08:b7:5a
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20

From iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

leiv@leiv-laptop:~$ lspci
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
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

To me it looks like it recognizes the wireless card but fail to enable it. 
Does this make any sense?

Regards

---

### Post by metalheart on 2007-07-05
Do the indication light on the laptop switches on (or blinks) after you press Fn + F2. Maybe the wireless is turned off in the BIOS?

---

### Post by sj3fk3 on 2007-07-05
> **leivae said:**
> Hi,
I tried to follow the instructions but came shrt as I could not find my device in the Networking GUI (eth1). I have the following output for you:


To me it looks like it recognizes the wireless card but fail to enable it. 
Does this make any sense?

Regards

Yes it does, the driver needs a piece of binary firmware code. Look in this forum for fwcutter or google Ubuntu and fwcutter and you will find the HOW-TO.

---

### Post by leivae on 2007-07-06
No indicator blink. Should not be switched off in BIOS as I have not changed it. It worked perfectly well under Windows XP.

Regard

---

### Post by leivae on 2007-07-06
> **sj3fk3 said:**
> Yes it does, the driver needs a piece of binary firmware code. Look in this forum for fwcutter or google Ubuntu and fwcutter and you will find the HOW-TO.

Well I found a post in the forum that looked promising, 
([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)) but I quickly ran into problems.

leiv@leiv-laptop:~$ uname -r
2.6.20-16-generic
leiv@leiv-laptop:~$ sudo apt-get install bcm43xx-fwcutter
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Reading state information ... Ferdig    
bcm43xx-fwcutter er allerede nyeste versjon.
0 oppgraderte, 0 nylig installerte, 0 å fjerne og 0 ikke oppgradert.
1 pakker ikke fullt installert eller fjernet.
Må hente 0B med arkiver.
Etter utpakking vil 0B ekstra diskplass bli brukt.
Setter opp bcm43xx-fwcutter (006-1) ...
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
dpkg: Feil ved behandling av bcm43xx-fwcutter (--configure):
 underprosessen post-installation script returnerte feilstatus 1
Det oppsto feil ved behandling av:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

Sorry about the Norwegian mix, but you probably got the idea. What now?

Rgds

---

### Post by neptho on 2007-07-06
> **leivae said:**
> Well I found a post in the forum that looked promising, 
([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)) but I quickly ran into problems.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Rgds

You have a proxy set.  Look for a Proxy setting in /etc/apt.conf or /etc/apt.conf.d/ - either remove the file (if not using a proxy) or set it to the full URL of your proxy.

For most of the world, it's safe to just remove it.

It'll look something like this:

```
 Acquire::http::Proxy "http://proxy:8080";
```

---

### Post by leivae on 2007-07-06
> **neptho said:**
> You have a proxy set.  Look for a Proxy setting in /etc/apt.conf or /etc/apt.conf.d/ - either remove the file (if not using a proxy) or set it to the full URL of your proxy.

For most of the world, it's safe to just remove it.

It'll look something like this:

```
 Acquire::http::Proxy "http://proxy:8080";
```

Hi,
could not find the proxy setting in /etc/apt/conf.d/.
Anywhere else I should look?

---

### Post by leivae on 2007-07-10
I found out. It now all works perfectly. Thanks for all help in this matter. \\:D/

---

