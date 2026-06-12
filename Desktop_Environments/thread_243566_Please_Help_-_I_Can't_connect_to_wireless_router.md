---
title: "Please Help - I Can't connect to wireless router"
date: 2006-08-25
forum: Desktop Environments
---

### Post by theLowerFre on 2006-08-25
I recently installed Ubuntu (Dapper Drake 6.06 Release) and am having trouble connecting to my wireless router.  

I have a USB WLAN adapter (Samsung SWL-2300U) which I used ndiswrapper to get Ubuntu to see and recognize.  This is working fine.  

I've followed every wireless thread, tutorial and guide so far that I've found and have been able to gather that my USB WLAN (device) adapter is being recognized as wlan0. :D 

In Network Administrator, I am able to see all the wireless networks in my immediate vicinity, I just cannot connect.  I have added the right ESSID, Hex WEP key, and have set to DHCP.  But still no connection.:-? 

From other guides, I have run other commands in Terminal and am able to gather that I cannot get wlan0 to connect to any access point/device.:-k 

There is a wireless router in my vicinity with now encryption or security set, and I try to connect to that -- but still no dice.](*,)

Any help would be greatly appreciated. Thanks. 

P.S. I'm at work, away from my desktop PC, so my replies will be delayed.  But, from the commands I've already ran I may be able to provide some insight.

---

### Post by tomduffy on 2006-08-25
Hi
I am having the same problems with same release but I have not yet used diswrapper, is it built in or do I need to download it. If built in how do I find it and use it? By the way I am a complete beginner:-k

---

### Post by theLowerFre on 2006-08-25
> **tomduffy said:**
> Hi
I am having the same problems with same release but I have not yet used diswrapper, is it built in or do I need to download it. If built in how do I find it and use it? By the way I am a complete beginner:-k

For me, ndiswrapper was not default, but it is in the repository for the Ubuntu (Dapper Drake 6.06 Release).  You need only to use the add/remove programs manager to install it.  You'll need the installation CD to do this.

What ndiswrapper does is to bind (or wrap) the Windows drivers that are used with your WLAN device so that they may work in Linux.  

I tried to used ndiswrapper via Terminal but was getting now where.  So, I installed the GUI (named ndisgtk) for ndiswrapper (also in the repository) and it worked like a charm.  You will need to reboot after you use ndiswrapper to make sure everything is working fine.

Ndiswrapper only helped my device to be recognized by Linux though.  And after that, I'm stuck trying to connect to an access point.

These are links to documents that helped me use ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page")
[http://ubuntuforums.org/showthread.php?t=85378&highlight=ndiswrapper]("http://ubuntuforums.org/showthread.php?t=85378&highlight=ndiswrapper")

The last one tells you how to find and install the GUI -- but try and install in by command line first.  Sorry that I cannot be more helpful as I'm not at my desktop PC at home.  And, if I were, I couldn't be more specific because . . . well, I can't connect to the Internet via Ubuntu because I can't connect to my router :)

---

### Post by tomduffy on 2006-08-28
Thanks for that anyway. I have now installed Ndiswrapper, I can connect with an ethernet connection but still not wireless, so I guess we are in the same position. If you get any further let me know and I will do the same.
Thanks

---

### Post by theLowerFre on 2006-08-28
So, that makes two of us.  Can anyone out there help us resolve our problem(s) with connecting to wireless routers, please?

---

### Post by Orion2014 on 2006-08-28
im having similar issues. I have a built-in wifi card in my dekstop, its an Airlink MIMO card, and it shows up as ra0. It shows all networks in my vicinity, but i cant seem to connect.

I DO use a DNS along with my DHCP router, mainly for my playstation, but i cant connect through my DNS either.

My router uses 64Bit WEP encryption, if that helps any.

---

### Post by NetworkGuy on 2006-08-29
I had the same problem when I use Network Manager.  I can get the wireless card up and running by changing my ACX firmware per instructions in this post...  [http://www.ubuntuforums.org/showthread.php?t=233565](http://www.ubuntuforums.org/showthread.php?t=233565)

however when I load Network Manager, change my /etc/network/interfaces file accordingly..  I can see several access points, but I can not connect to any of them.   I ended up scrapping Network Manager.  I'm currently looking into WifiRadar to try to control my wifi.   If that doesn't work the way I like it, I'll just go back to my method of having several interfaces files and manually copying the right one into place and then resetting my card.   

Try putting your interfaces file back to original and connecting via system --> Administration --> Networking.   Set your ESSID and WEP key in there.  If that doesn't work, let me know.  

Here is my interfaces file for reference..

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid XXXXXXXXXX

``` 

Yes there is no WEP key setup (yet) :)

---

### Post by theLowerFre on 2006-08-29
Thanks for coming.  :-D I appreciate it!

No, I set up my interfaces file as you suggested.  
And still no access point.  I used NetworkManager and that did not connect -- and I've also tried WifiRadar but it just clocks indefinitely.

I was going to try and print the output from Terminal when I issue the ifconfig and iwconfig commands - thinking it would be able to help you decipher the problem easier; however, I don't know how to write to my Windows partition.  Or how to go back into my Linux partition and grab the file.

---

### Post by NetworkGuy on 2006-08-29
Let's start at the beginning.

Post the results of ```
lspci
```
and
```
iwconfig
```
and
```
ifconfig
```

---

### Post by theLowerFre on 2006-08-29
Alright, here goes nothing:

lspci
```

chris@chris-desktop:~$ sudo lspci
Password:
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
0000:00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

```

iwconfig
```

chris@chris-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Tx-Power:0 dBm   Sensitivity=0/3
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



```

ifconfig
```

chris@chris-desktop:~$ sudo ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1504 (1.4 KiB)  TX bytes:1504 (1.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:02:78:EC:3D:19
          inet6 addr: fe80::202:78ff:feec:3d19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4724 (4.6 KiB)  TX bytes:0 (0.0 b)


```

---

### Post by NetworkGuy on 2006-08-29
OK, it appears that NDISWrapper is installed correctly 

Right now looking at iwconfig, WLAN0 is not associated with your access point.

Try this at the terminal
```
 iwconfig wlan0 essid <ESSID You Use>
```

Do another iwconfig wlan0 and you should see this:
> wlan0     IEEE 802.11b+/g+  **ESSID:"<Your ESSID>"**  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:49:B7:DA
          Bit Rate:48 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=46/100  Signal level=25/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If you see your ESSID in that area above, then do an ifconfig to see if you get an IP address.  

Let us know how that goes.

---

### Post by theLowerFre on 2006-08-29
Still, no access point is associated::-k 
```

chris@chris-desktop:~$ sudo iwconfig wlan0 essid WEST7511
Password:
chris@chris-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Tx-Power:0 dBm   Sensitivity=0/3
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



```

---

### Post by NetworkGuy on 2006-08-29
What do you get back when you do a ```
iwlist wlan0 scan
```

---

### Post by theLowerFre on 2006-08-29
All the wireless networks in my vicinity are shown.

---

### Post by tomduffy on 2006-08-30
When I run iwlist wlan0 list scan I get Interface does'nt support scanning : operation not supported. Is this significant?

---

### Post by NetworkGuy on 2006-08-30
theLowerFre:

We are getting to the end of my ability to get this card working.  But I'm not done yet.   Reply with the results of this command
```
lsusb
```

Thanks.

---

### Post by NetworkGuy on 2006-08-30
TomDuffy,

Unless you also have a Samsung SWL-2300U USB card, you may want to open a new thread. I'll be looking for it later this evening, but someone else may jump in and start to help you get the card working. :) Describe that you are having problems with wireless.  Include the make/model of your wireless card.  Include if it's USB or PCMCIA.  

Also include the results of the following commands run from a terminal:
If it's a PCMCIA or PCI card:
```
lspci
```
If it's a USB card
```
lsusb
```

Also include the output from ```
iwconfig
``` and ```
ifconfig
```

Good Luck and I hope you get the card working.

---

### Post by xtknight on 2006-08-30
Type:

sudo ifconfig wlan0 down
sudo iwconfig wlan0 ap any
sudo iwconfig wlan0 essid any
sudo ifconfig wlan0 up
sudo dhclient wlan0
sudo iwevent

Watch for the events.  If that does not work, set your access point to your router's MAC manually, e.g.:

sudo iwconfig wlan0 ap 00:60:1D:01:23:45

---

### Post by tomduffy on 2006-08-31
Thanks Networkguy
I have a thread that starts ZD1211 BlueNext wireless device and have posted details there

Cheers

---

### Post by theLowerFre on 2006-09-01
Thanks, NetworkGuy for your help . . .
Sorry for getting back to you so late but we've been really busy at work.  Here is the output from the lsusb command in Terminal:
```

[B]chris@chris-desktop:~$ sudo lsusb
Password:
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 005: ID 055d:b230 Samsung Electro-Mechanics Co.
Bus 001 Device 004: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000[/B]

```

---

### Post by theLowerFre on 2006-09-01
xtknight, here is the output from entering the commands you suggesting into Terminal . . . I don't quite think they worked out:
```

[B]chris@chris-desktop:~$ sudo ifconfig wlan0 down
chris@chris-desktop:~$ sudo iwconfig wlan0 ap any
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device wlan0 ; Invalid argument.
chris@chris-desktop:~$ sudo iwconfig wlan0 essid any
chris@chris-desktop:~$ sudo ifconfig wlan0 up
chris@chris-desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:02:78:ec:3d:19
Sending on   LPF/wlan0/00:02:78:ec:3d:19
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
chris@chris-desktop:~$ sudo iwevent
Waiting for Wireless Events from interfaces...

chris@chris-desktop:~$ sudo iwconfig wlan0 ap 00:0f:db:4f:d9:a3
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device wlan0 ; Invalid argument.[/B]

```

The iwevent command only clocked indefinitely.

---

### Post by theLowerFre on 2006-09-10
Sorry for the bump - forgive me.

---

### Post by English haze on 2006-09-11
I'm having exactly the same problem with a Belkin F5D7050 USB wireless stick.

Could it be something to do with the signal sensitivity? I'm trying to set a different sens value but the iwconfig command just complains that the value is invalid when the manual says 0 to -112 is valid.

> 
root@paul-desktop:/usr/share/drivers/F5D7050# iwconfig wlan0 sens -100
Error for wireless request "Set Sensitivity" (8B08) :
    SET failed on device wlan0 ; Invalid argument.

Any comments?

---

### Post by jmoorse on 2006-09-11
Disabling ipv6 in Network Administration and blacklisting the module helped me.  I also had to manually input my settings into the Network Administration's XML File as it has problems storing profiles.

Would walk you through those steps but, sadly, am not at my Ubuntu box...

---

### Post by theLowerFre on 2006-09-12
:D Alright cool, whenever you are able to get to your machine running Ubuntu and are able to give me step-by-step instructions I would greatly appreciate the help! :D

---

### Post by chocbar31 on 2006-09-14
> **xtknight said:**
> Type:

sudo ifconfig wlan0 down
sudo iwconfig wlan0 ap any
sudo iwconfig wlan0 essid any
sudo ifconfig wlan0 up
sudo dhclient wlan0
sudo iwevent

Watch for the events.  If that does not work, set your access point to your router's MAC manually, e.g.:

sudo iwconfig wlan0 ap 00:60:1D:01:23:45


xtknight, you is tight! Thanks for this...worked for me, as I installed Edgy and could only access the first access point seen. I could not access any other access points; open or secured.

Thanks again for your knowledge; you got me surfin from access point again! =D>

---

