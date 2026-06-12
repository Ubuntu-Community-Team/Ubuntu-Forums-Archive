---
title: "Wireless Problem with Dell E1705 Wireless N"
date: 2009-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dfinf2 on 2009-05-02
Hey I have been trying to get my Wireless Working for the past two days on my Dell Inspiron E1705 it uses the Dell mini 1500 Wireless N card. I tried both NDIS Wrapper and The Broadcom STA wireless Driver. When I use the NDIS Wrapper it says it cannot detect the hardware the dirver is for but it is the correct .inf file i'm 98% sure. When I use the Broadcom STA Wireless driver is tries to connect to the Wireless but just won't. If you need anymore information or somehow when I used search I missed an article let me know.

Thanks alot!

---

### Post by coffeeaddict22 on 2009-05-03
Hi,
There's an excellent wiki article on wireless [**here**]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")
If that isn't enough/ is too much, open a terminal, type in```
lshw -C network
```and then ```
iwconfig
```Those commands should give you/ us enough to figure out where the problem lies.  Post the output from both back here if you want more assistance.

---

### Post by dfinf2 on 2009-05-03
Thanks for the information, I have found something that doesn't make sense to me. when using ndiswrapper it says the device is installed and present. Looks like this:

```


where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
dfinf2@dfinf2-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
[B]bcmwl5 : driver installed
        device (14E4:4328) present (alternate driver: ssb)[/B]

```

But Ubuntu still sees no wireless. I am still running through that tutorial that you recommended to see if it can be fixed, but in the mean time here is the information you requested.

```
  [B]*-network                                 
       description: Network controller      
       product: BCM4328 802.11a/b/g/n       
       vendor: Broadcom Corporation         
       physical id: 0                       
       bus info: pci@0000:0c:00.0           
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb[/B]
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:4b:63:0d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.254.3 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 52:51:b9:a1:8c:a3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```


Hopefully this can help if that tutorial doesn't help. Thanks alot I hope I can get this working as I spend a lot of time on the wireless at school and am trying to keep myself from using Windows XP as much as possible.

---

### Post by coffeeaddict22 on 2009-05-03
You haven't got ndiswrapper running, even if it is installed, and it looks like your wireless driver is not running either.  Look in System/Admin/Hardware drivers, and turn on the Broadcom STA driver.  Once you do that post back the results of the lshw command again.

Just be a bit careful messing around if you're using google.  Linux wireless has changed quite a bit in the last couple of years; especially in the last 6 months, and you'll find some commands (pccardtl for one) have been "deprecated".  Most cards now "just work", but following an old howto is a good way of changing that.

---

### Post by dfinf2 on 2009-05-03
Hey Sorry for being such a noob, just a little hard going from Windows since being born to linux lol. But after enabling the Broadcom STA driver here is was lshw spits back at me:

  ```
[B]*-network                                                                                                                                                                                                          
       description: Wireless interface                                                                                                                                                                               
       product: BCM4328 802.11a/b/g/n                                                                                                                                                                                
       vendor: Broadcom Corporation                                                                                                                                                                                  
       physical id: 0                                                                                                                                                                                                
       bus info: pci@0000:0c:00.0                                                                                                                                                                                    
       logical name: eth1
       version: 01
       serial: 00:16:cf:28:05:1e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11[/B]
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:4b:63:0d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.254.3 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:4a:7c:29:e5:31
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

Thanks again for putting up with my lack of knowledge
UPDATE: When enabling the STA driver after a reboot I cannot connect via ethernet or wireless. I have to disable the STA driver and reboot to connect to wired internet.

---

### Post by coffeeaddict22 on 2009-05-04
Don't bother apologising for being willing to learn- we all did / are still doing it...
OK.  It looks like you've got a working driver with the wireless on.  The ethernet should work; it looks like it was unplugged, but it could be a conflict.  Terminal is a bit easier to explain than a GUI, but network manager should be going.  Have you got the icon with 4 bars in the upper right?  If so, Left click to set up your network and you should be away.  Right click gives you a few more options.
Terminal commands if you still want help- now that you've got a working driver, you can start playing finding and connecting to the network.
```
iwconfig
```, for your wireless connection details; if you're trying to figure out if it can see your router, ```
sudo iwlist scan
``` essentially looks around the neighbourhood.
```
ifconfig
``` will tell you a bit about the wired network.  Post what you get from them back if you like.

there's a nice page in the wiki: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") is both up to date and fairly logical.

---

### Post by dfinf2 on 2009-05-04
Got the same problem when I installed the STA driver the ethernet wouldn't work and it tries to connect to my wireless, it shows two orbs and the arced blue lines but only the bottom orb lights up not the top one. Here is the outputs from the terminal.

```
~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:130 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```
```

~$ sudo iwlist scan         
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:CB:9F:F3:6E
                    ESSID:"WAR"               
                    Protocol:IEEE 802.11g     
                    Mode:Managed              
                    Frequency:2.437 GHz (Channel 6)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on                                        
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s      
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s     
                              48 Mb/s; 54 Mb/s                               
                    Extra:bcn_int=100                                        
                    Extra:atim=0                                             
          Cell 02 - Address: 00:1D:7E:58:7E:CC                               
                    ESSID:"lauren"                                           
                    Protocol:IEEE 802.11g                                    
                    Mode:Managed                                             
                    Frequency:2.437 GHz (Channel 6)                          
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on                                        
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s     
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s      
                              12 Mb/s; 48 Mb/s                               
                    Extra:bcn_int=100                                        
                    Extra:atim=0                                             
                    IE: WPA Version 1                                        
                        Group Cipher : TKIP                                  
                        Pairwise Ciphers (1) : TKIP                          
                        Authentication Suites (1) : PSK                      
          Cell 03 - Address: 00:0F:3D:51:9E:FC
                    ESSID:"Claire"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:0F:B5:A8:4D:A0
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

pan0      Interface doesn't support scanning.
```

```
ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:55214 (55.2 KB)  TX bytes:55214 (55.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:28:05:1e
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:2862 (2.8 KB)
          Interrupt:17 Memory:dcffc000-dd000000
```

To me this says both the wireless and ethernet should be working and that I should be able to connect to my Wireless (My wireless is hidden), but neither is happening lol.. Ill look at that wiki after some finals today. 

Thanks again

---

### Post by coffeeaddict22 on 2009-05-04
Yes, you should be able to connect.  All four wireless networks you can see are encrypted, though, so you're going to have to find/ remember the key; I'm willing to bet that's why you aren't connecting.  With the hardware setup you were using there's nothing showing up that looks like a wired network driver.
I suspect you've forgotten that wired networks aren't encrypted; when plugged in, you connect automatically.  When trying with wireless you need a key.  Easiest way to enter it is by clicking on the network manager icon.

---

### Post by dfinf2 on 2009-05-05
My network wasn't showing up because someone unplugged it when I was posting that reply lol. But even when it is plugged in I still cannot connect or use the wired. Maybe I will try to juyst reinstall Ubuntu and see what happens. Thanks for your help!

---

### Post by moster on 2009-05-13
I have too similar problem with broadcom 4311 rev2. It not work in 8.4 then working in 8.10 and now again do not work in ubuntu 9.4.

With STA driver it seems everything working, but I cannot connect to my network and with b43 driver I can connect but connection is 1kb/s and after some time it just snap.

I am very, very, very dissapointed.

---

### Post by dfinf2 on 2009-05-13
Sadly, I had to switch back to Winblows XP as my default OS, still have ubuntu installed, but without wireless it's not as practical to use everyday for me.:sad: Maybe I could use Feisty or Gusty instead, but I am one of those people who needs to use the most up to date software.

---

### Post by l-x-l on 2009-05-13
> **dfinf2 said:**
> Sadly, I had to switch back to Winblows XP as my default OS, still have ubuntu installed, but without wireless it's not as practical to use everyday for me.:sad: Maybe I could use Feisty or Gusty instead, but I am one of those people who needs to use the most up to date software.

Sorry to hear about your troubles. I have the same laptop (Dell E1705). But I have a different wireless N card (Intel PRO/Wireless 4965). Wireless worked out the box for me. But I do suffer irregular & random connection drops. Hope you figure out your issue.

---

### Post by dfinf2 on 2009-05-13
Maybe I will just buy a new laptop and turn this one into a firewall or something lol

---

### Post by dfinf2 on 2009-05-13
@ l-x-l:

So your wireless does work? I just remembered that the wireless card in the e1705 is a mini pci-e can can be replaced. If your wireless works fairly well I could just buy the card you have off ebay for roughly 30 bucks. Please let me know how often is just randomly disconnects. THANKS!

---

### Post by l-x-l on 2009-05-14
> **dfinf2 said:**
> @ l-x-l:

So your wireless does work? I just remembered that the wireless card in the e1705 is a mini pci-e can can be replaced. If your wireless works fairly well I could just buy the card you have off ebay for roughly 30 bucks. Please let me know how often is just randomly disconnects. THANKS!

Yes my card does work. Random disconnects means what it implies. Sometimes the disconnect doesn't happen for a day after loging on & sometimes it happens 30 minutes after logging on. Sometimes it happens when dl'ing large files & sometimes not. There's no real rhyme or reason. Whenever it does happen I have to disconnect my connection from Network Manager/WICD & reconnect. Then all is well. The longest I have gone without a disconnect problem is a day.

Please also note that the card is a wireless draft N. As far as I know Ubuntu does not yet support Wireless N. So don't expect Wireless N speed/range. I made my router a dedicated G instead of dual N & G hoping it would fix the disconnects but it still happens.

---

### Post by dfinf2 on 2009-05-14
Maybe I will experiment with the "Intel PRO Wireless 4965 AGN Mini-PCI-Express 802.11AGN" card that you have and also the older "Intel Pro Wireless LAN 3945ABG Mini PCI-E" card they make. I would think I would have better luck with the older 3945ABG card. That is how much I want Ubuntu to work.

---

