---
title: "Broadcomm STA driver stopped working properly after upgrade in Ubuntu 10.04"
date: 2010-05-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wizard_karan on 2010-05-13
Hi all,

I have been using Ubuntu 10.04 beta for 1 month and everything was fine.

two days back i upgraded 10.04 from 2.6.32-21 to 2.6.32.22 and the following things happened:-
1) The network manager was gone:(, so i installed it again.
2) I use a wifi connection at home and have a belkin wifi wireless-g router, the wifi used to work perfectly before the upgrade.

BUT NOW, the the wifi connection connects and disconnects every 10 or 20 seconds and so on this pattern continues :mad:.

I am almost sure that this is a driver issue, i was previously using Broadcomm STA driver that came with ubuntu. I know that this is not a network manager problem, because i am getting the same problem with WICD network manager too.

But strangely this problem vanishes if i am using a wired ethernet connection. SO this is a wireless only problem(probably).

BTW the wifi connection works perfectly on the Windows 7 installation on the same laptop. My laptop is DELL Inspiron 1564, which i bought 2 months back.

Please help me out as i am not able to access the net on my ubuntu installation.:confused:

from
Karan Pratap Singh
Chandigarh,India

---

### Post by binary10 on 2010-05-13
That driver is working for sure with 2.6.32-22-generic kernel. That's the same version that I'm running now.  Can you not boot the previous kernel from your grub menu ? 

My only saving is that I had pre-built this O/S disk on a another system to 2.6.32-22-generic and then transferred it to the 1564-i3 330m and then installed the STA driver.

Have you looked at the output of 'iwlist scan' and such like ?

What sort of security is on the wireless ?

---

### Post by wizard_karan on 2010-05-15
Hi Binary10

thanks for helping me out!:)

1) Yeah i am able to boot to the previous generic version but in that version too the STA driver is not working:confused:


2) iwlist scan is not able to find my wifi card?:mad:

3) My wireless connection security is WPA2-PSK:guitar:

I really need wifi up and running, do you have any experience with ndiswrapper ?

from
Karan Pratap Singh
Chandigarh,India

---

### Post by binary10 on 2010-05-15
I've been looking around at a few threads on this issue and doing my own investigations, because I guess this is could hit me also at the next kernel upgrade. There's a few things that you might want to check or go over again if you already have.

```

xxx@drone:/var/lib/dkms/bcmwl$ lspci | grep BCM
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
xxx@drone:/var/lib/dkms/bcmwl$ 

xxx@drone:/etc$ dpkg -l | grep bcmwl
ii  bcmwl-kernel-source                  5.60.48.36+bdcom-0ubuntu3                       Broadcom 802.11 Linux STA wireless driver so
ii  bcmwl-modaliases                     5.60.48.36+bdcom-0ubuntu3                       Modaliases for the Broadcom 802.11 Linux STA
xxx@drone:/etc$ lsmod | grep wl
wl                   1964968  0 
lib80211                6119  2 lib80211_crypt_tkip,wl

xxx@drone:/etc$ sudo find / -name wl\.ko
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/2.6.32-22-generic/x86_64/module/wl.ko
/lib/modules/2.6.32-22-generic/updates/dkms/wl.ko
xxx@drone:/etc$ 


```

Also check the dkms areas and see if you have a link for the kernel version. Mine has the build area and source.
```

cd /var/lib/dkms/bcmwl

```

The links I found were :

[http://www.backports.ubuntuforums.org/showthread.php?t=1378830](http://www.backports.ubuntuforums.org/showthread.php?t=1378830)
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

They might be of some interest, I might try a manual build myself under /var/lib/dkms/bcmwl on a backup drive of mine.

Last time I did ndis wrapping, I think it was on OS2 back in the 90's :s - so I think I'll pass

---

### Post by wizard_karan on 2010-05-17
Thanks Binary10,

Thanks i am going to try your links and suggestions and post back if the problem is solved, or not solved!:P

Thanks Again.

Long Live Dell Laptops:)!

from
Karan Pratap Singh
Chandigarh, India

---

### Post by wizard_karan on 2010-05-22
[SOLVED][Broadcomm STA  driver stopped working properly after upgrade in Ubuntu 10.04]("http://ubuntuforums.org/showthread.php?t=1482400")

Hi binary10

I finally solved the problem that i was facing.:guitar:

I was guided a lot by acicula on #ubuntu at irc.freenode.net

Thanks acicula , a lot!:)

it worked after i toggled wifi on and off a few times after disconnecting the ethernet cable from my laptop.

and here is the definite guide to Broadcomm drivers in ubuntu

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)


Enjoy! and thanks to you too binary10:P for helping me out! he he!

from
Karan Pratap Singh
Chandigarh, India

---

### Post by wizard_karan on 2010-06-27
Over time i have come to realize that the problem was not because of the STA drivers, it was actually WICD and the ubuntu network manager that were conflicting with each other.

Note it also seems from my experience that WICD can't work properly without the default network manager!

thought i dont use WICD now, i stick to the default network manager provided by Ubuntu 10.04.

Hope this helps other people affected by this problem!!
from
Karan Pratap Singh
Chandigarh,India

---

### Post by pirx42 on 2010-06-27
Hello!

I have the same problem with a Dell Vostro 3500. I have installed the "bcmwl-kernel-source" pkg, and i can connect to the wifi-network... for a while. Then it disconnects, re-connects, disconnects and so on. Driving me nuts:)

# lspci | grep Broadcom
12:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)

In syslog i see that for some reason the system decides to start roaming:

Jun 27 02:25:32 laptop NetworkManager: <info>  Policy set 'Auto PlommonNet' (eth1) as default for routing and DNS.
Jun 27 02:25:32 laptop NetworkManager: <info>  Activation (eth1) successful, device activated.
...
Jun 27 02:25:36 laptop NetworkManager: <debug> [1277598336.005783] periodic_update(): Roamed from BSSID 00:1F:9F:50:27:61 (PlommonNet) to (none) ((none))
Jun 27 02:25:42 laptop NetworkManager: <debug> [1277598342.006279] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1F:9F:50:27:61 (PlommonNet)
Jun 27 02:25:48 laptop NetworkManager: <debug> [1277598348.001549] periodic_update(): Roamed from BSSID 00:1F:9F:50:27:61 (PlommonNet) to (none) ((none))

And it keeps printing this even during the periods when the wifi is working. One line every few seconds.

I have tried deleting all other wifi-connections except the one i want to use (PlommonNet) in the network-manager, and as far as i know i am not using any "wicd".

So how exactly was the "roaming"-problem solved for you? Previously you used 2 network managers and those conflicted, and it was solved when you quit using wicd?

And is it possible to skip any network-manager alltogether? How do i just manually set a ssid/encryptiontype/password manually? Then perhaps it wont disconnect&roam?
I have tried a few "iwconfig" commands, but i just got "Operation not supported" or something like that.

  wbr / pirx


> **wizard_karan said:**
> Over time i have come to realize that the problem was not because of the STA drivers, it was actually WICD and the ubuntu network manager that were conflicting with each other.

Note it also seems from my experience that WICD can't work properly without the default network manager!

thought i dont use WICD now, i stick to the default network manager provided by Ubuntu 10.04.

Hope this helps other people affected by this problem!!
from
Karan Pratap Singh
Chandigarh,India

---

### Post by wizard_karan on 2010-06-27
Hi pirx42

1) Yeah my problem was mainly caused due to conflicts between WICD network manager and the default Network Manager provided by ubuntu, so i removed WICD and it solved my problem.:D

2) I see from your post that you have a Broadcomm 4353 wireless card in your Vostro laptop.
You should try installing the Broadcomm STA Wireless driver by going into System -> Administration -> Hardware Drivers and see if that works properly for you? otherwise you should use the bmw-cutter package available for Broadcomm.

3) Also which company Router are you using? sometimes faulty settings in the router can also cause frequent disconnects.

4) Does your wifi connection work perfectly in Windows or any other OS ? is it only Ubuntu that is causing problems for you ?

5) Is the firmware of your router updated to its latest version  ?
if not then go to your router's manufacturer's website and follow the procedures there to update your routers firmware. 

Updating your routers firmware can help because the router company might have fixed some crucial patches and security loopholes in your router's inbuilt software.

6) Another important point to consider is are you using WEP or WAP/WPA2. If you are using WEP then your router could have been hacked by your neighbour and he might be messing with it, try switching to WPA/WPA2 for better protection.(though it is very unlikely that your connection was hacked)(:KSFACT:KS: WEP can be cracked in under 5 hours using Aircrack)

7) Please do the following:
type in the terminal:
ifconfig
and then show me its output.
 
8) Also
type in the terminal:
iwconfig
and then show me its output.

9) This is an obvious one, but are you within range of your router's coverage area ? i mean to ask are you within the advertised wifi range of the router or outside that range ? Keep the router antenna in a vertical position with respect to the room floor, which will help max its range.

10) As a last resort you can also use Ndiswrapper to install the windows version of your wireless card driver inside ubuntu. I am no expert in that area but you should see the following link: 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Though going the Ndiswrapper way will be a bit challenging!!

11) Yeah you can setup a wifi connection by using the terminal by editing the /etc/network/interfaces file, though i am not sure whether you can setup security using the terminal only.

12) Lastly , check in the following official link whether your wirless card is supported by ubuntu or not ?

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)


Provide me with the information i asked above and then i will help you

from
Karan Pratap Singh
Chandigarh, India
P.S. Dell laptops Rock :guitar:, Belkin routers suck:mad:

---

### Post by prubyholl on 2010-07-08
Hello all, this is my first time posting to this forum though i sometimes face some issues.. i completely stopped using windows as mainstream OS a couple of yrs ago sticking and enjoying ubuntu.

Well i purchased a yet another Dell Vostro 3500 (i5) only to have problems wit the broadcom card...

i have tried alotta the theories here on ubuntuforums but no success

well i guess the techies out here can help me solve this ..

I successfully activated the restricted drivers and am using them.
My wifi card detects the networks and tries connecting to them but usually fails with error 

'Association request to driver failed' 

 Pls...has it got something to do with the blacklist File..?

I currently use  ZYDAS usb wireless stick perfectly on my 10.04 box.
but i really want my in-built card to work.

sorry for the long text but pls contact me on skype:   prubyholl or yahoo:  prubyholl.
i can also paste any command output here.

Pls help me out..thanx all

---

### Post by wizard_karan on 2010-07-08
> **prubyholl said:**
> Hello all, this is my first time posting to this forum though i sometimes face some issues.. i completely stopped using windows as mainstream OS a couple of yrs ago sticking and enjoying ubuntu.

Well i purchased a yet another Dell Vostro 3500 (i5) only to have problems wit the broadcom card...

i have tried alotta the theories here on ubuntuforums but no success

well i guess the techies out here can help me solve this ..

I successfully activated the restricted drivers and am using them.
My wifi card detects the networks and tries connecting to them but usually fails with error 

'Association request to driver failed' 

 Pls...has it got something to do with the blacklist File..?

I currently use  ZYDAS usb wireless stick perfectly on my 10.04 box.
but i really want my in-built card to work.

sorry for the long text but pls contact me on skype:   prubyholl or yahoo:  prubyholl.
i can also paste any command output here.

Pls help me out..thanx all

Hi prubyholl:p

please see my reply tp pirx42 above your post and try following all the steps mentioned there!:D

post the output of /etc/network/interfaces file
as well as outputs of the commands, ifconfig and iwconfig

i will be glad to help you out as much as i can!:)

from
Karan Pratap Singh
Chandigarh, India

---

### Post by prubyholl on 2010-07-08
1. I donot have wicd installed on this installation 
2.yes i think am using broadcom 4353 also
3. the wifi works perfect on windows 7 to the same Netgear router
4. AP Network is open ..No passwords
5. AM able to connect using the same laptop but with an addon usb ZYDAS wireless stick
6.

$$$ifconfig
eth0      Link encap:Ethernet  HWaddr a4:ba:db:b1:57:bf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:32 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr f0:7b:cb:20:d5:63  
          inet6 addr: fe80::f27b:cbff:fe20:d563/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:261
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:695067 (695.0 KB)  TX bytes:695067 (695.0 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.62.1  Bcast:192.168.62.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.27.1  Bcast:172.16.27.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:40:a8:3a  
          inet addr:172.16.0.5  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe40:a83a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5010017 (5.0 MB)  TX bytes:2952029 (2.9 MB)



$$$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"ASHAWO"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:2A:10:5D:38   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=16/100  Signal level=16/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:159
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.


Yes i am within range of the routers coverage because it works with the wireless stick and also with the same inbuilt broadcom on win7
and well the signal is not really high as i take this command but will move closer in any other steps u whelp me with, though cos of a few walls but i am very mobile around here and still doesnt work




I have tried NDISWrapper with teh win7 drivers both 32bit and 64 bit versions....

had no success

only thing is that i feel am close to the solution cos it detects the network and connects but gives error associating to the driver or so

$$$$ System Log
nager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jul  8 20:09:45 phatkin-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto ASHAWO' requires no security.  No secrets needed.
Jul  8 20:09:45 phatkin-laptop NetworkManager: <info>  Config: added 'ssid' value 'ASHAWO'
Jul  8 20:09:45 phatkin-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jul  8 20:09:45 phatkin-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jul  8 20:09:45 phatkin-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul  8 20:09:45 phatkin-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jul  8 20:09:45 phatkin-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jul  8 20:09:46 phatkin-laptop wpa_supplicant[912]: WPS-AP-AVAILABLE 
Jul  8 20:09:46 phatkin-laptop wpa_supplicant[912]: Trying to associate with 00:1e:2a:10:5d:38 (SSID='ASHAWO' freq=2412 MHz)
Jul  8 20:09:46 phatkin-laptop wpa_supplicant[912]: Association request to the driver failed
Jul  8 20:09:46 phatkin-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jul  8 20:09:46 phatkin-laptop wpa_supplicant[912]: WPS-AP-AVAILABLE 

$$  /etc/network/interfaces:
auto lo
iface lo inet loopback


I hope am not filling up the servers here

thanx in advance

---

### Post by n5wy on 2010-07-08
FYI, I have had the same problem with the logfiles filling up with connect/disconnect lines when I have the wifi adapter in use. It does not seem to matter which Cisco AP is in use while connected. All of the APs I use have WPA/WPA2 encryption and DHCP enabled. My Broadcom drivers (STA) are installed and working and I can use the networking without any apparent problems other than the annoying messages filling the log files. 

This has occurred consistently in Karmic and now Lucid 64bit editions on my Dell M6400 with the BCM4322 card. I have tried to troubleshoot this problem off and on, but have not met with any success yet. So far my investigations have led me to conclude that this may be a driver issue since this hardware works fine with no similar problems in Win 7 x64.

---

### Post by prubyholl on 2010-07-09
Well mine seems to be Broadcom 4353 on vostro 3500 using Ubuntu 10.04 x64, i guess not real much difference anyway

well I understand in this thread, someone managed to get it working 
I pray it works for me as well, though i have followed several theories here using clean installs but still not managed to fix it.

so does it mean Broadcom drivers now are not updated for their newer hardware devices?

Wizard_kharan, pls continue helping me out when free.


Any hope? Thx all for the information, prompt response and all..
am grateful sop far.

---

### Post by wizard_karan on 2010-07-11
> **prubyholl said:**
> Well mine seems to be Broadcom 4353 on vostro 3500 using Ubuntu 10.04 x64, i guess not real much difference anyway

well I understand in this thread, someone managed to get it working 
I pray it works for me as well, though i have followed several theories here using clean installs but still not managed to fix it.

so does it mean Broadcom drivers now are not updated for their newer hardware devices?

Wizard_kharan, pls continue helping me out when free.


Any hope? Thx all for the information, prompt response and all..
am grateful sop far.

Dear prubyholl,(my name is wizard_karan not wizard_kharan :D)

Thanks for posting all the details i asked for.:D

1) You should not use an insecure wireless connection, as it may very well be used by a neighbour and he may use up all your bandwidth or hack into your home wirless network.(try setting up WPA/PSK or WPA2/PSK if it is supported by your router guy.)

2) You should better use the default gnome-network-manager to setup your connection and unistall any other network configuring clients.

3) I see the phatkin-network-manager in your error logs...
what is this phatkin-network-manager that you are using ?

4) This zydas wireless stick that you are using, does it need drivers inside Ubuntu ? I wonder whether the zydas drivers are conflicting with your Broadcomm STA drivers.

5) Try unistalling zydas drivers or any softwares that came with the zydas stick completely and then reinstalling the Broadcomm STA wireless drivers. After that try connecting to your network via gnome-network-manager.

6) Also note that whatever changes you make in the /etc/network/interfaces file will be automatically overwritten by the gnome-network-manager at each startup!(yeah i know GUI network managers are a piece of ****)

7) Are you able to ping your router's address when you connect to your wireless connection ?
(Generally the router's address is 192.168.2.1(may wary from router to router))

8) I suspect that you configured your Netgear router yourself straight out of the box? If yes, then do call the Netgear Tech. Support for the correct settings for your router, including the security settings as well, Sometimes we shrug off small things like these, but talking to the Netgear Tech. Support Guy might actually help you out.
post the answers to these questions and then i may be able to help you further. 8-)


from
Karan Pratap Singh
Chandigarh, India

---

### Post by prubyholl on 2010-07-11
Alright, well I added a few packages just today and it works but i have another problem with the roaming every say 5 seconds...I dont know what.

#log
 11 20:41:34 phatkin NetworkManager: <debug> [1278880894.001427] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:41:40 phatkin NetworkManager: <debug> [1278880900.002623] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:42:46 phatkin NetworkManager: <debug> [1278880966.003091] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:42:52 phatkin NetworkManager: <debug> [1278880972.002904] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:43:10 phatkin NetworkManager: <debug> [1278880990.003145] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:43:16 phatkin NetworkManager: <debug> [1278880996.005615] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:43:22 phatkin NetworkManager: <debug> [1278881002.003173] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:43:28 phatkin NetworkManager: <debug> [1278881008.000369] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:43:34 phatkin NetworkManager: <debug> [1278881014.001360] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:43:52 phatkin NetworkManager: <debug> [1278881032.001516] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:44:04 phatkin NetworkManager: <debug> [1278881044.005070] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:44:10 phatkin NetworkManager: <debug> [1278881050.001330] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:44:28 phatkin NetworkManager: <debug> [1278881068.004720] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:44:34 phatkin NetworkManager: <debug> [1278881074.002897] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:45:04 phatkin NetworkManager: <debug> [1278881104.001541] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:45:10 phatkin NetworkManager: <debug> [1278881110.001317] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:45:40 phatkin NetworkManager: <debug> [1278881140.001897] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:45:58 phatkin NetworkManager: <debug> [1278881158.002456] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:46:46 phatkin NetworkManager: <debug> [1278881206.000632] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:46:52 phatkin NetworkManager: <debug> [1278881212.001678] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:47:16 phatkin NetworkManager: <debug> [1278881236.001425] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:47:22 phatkin NetworkManager: <debug> [1278881242.002315] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))

thanks and and correction well noted

---

### Post by wizard_karan on 2010-07-12
> **prubyholl said:**
> Alright, well I added a few packages just today and it works but i have another problem with the roaming every say 5 seconds...I dont know what.

#log
 11 20:41:34 phatkin NetworkManager: <debug> [1278880894.001427] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:41:40 phatkin NetworkManager: <debug> [1278880900.002623] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:42:46 phatkin NetworkManager: <debug> [1278880966.003091] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:42:52 phatkin NetworkManager: <debug> [1278880972.002904] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:43:10 phatkin NetworkManager: <debug> [1278880990.003145] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:43:16 phatkin NetworkManager: <debug> [1278880996.005615] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:43:22 phatkin NetworkManager: <debug> [1278881002.003173] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:43:28 phatkin NetworkManager: <debug> [1278881008.000369] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:43:34 phatkin NetworkManager: <debug> [1278881014.001360] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:43:52 phatkin NetworkManager: <debug> [1278881032.001516] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:44:04 phatkin NetworkManager: <debug> [1278881044.005070] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:44:10 phatkin NetworkManager: <debug> [1278881050.001330] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:44:28 phatkin NetworkManager: <debug> [1278881068.004720] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:44:34 phatkin NetworkManager: <debug> [1278881074.002897] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:45:04 phatkin NetworkManager: <debug> [1278881104.001541] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:45:10 phatkin NetworkManager: <debug> [1278881110.001317] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:45:40 phatkin NetworkManager: <debug> [1278881140.001897] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:45:58 phatkin NetworkManager: <debug> [1278881158.002456] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:46:46 phatkin NetworkManager: <debug> [1278881206.000632] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:46:52 phatkin NetworkManager: <debug> [1278881212.001678] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))
Jul 11 20:47:16 phatkin NetworkManager: <debug> [1278881236.001425] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:2A:10:5D:38 (ASHAWO)
Jul 11 20:47:22 phatkin NetworkManager: <debug> [1278881242.002315] periodic_update(): Roamed from BSSID 00:1E:2A:10:5D:38 (ASHAWO) to (none) ((none))

thanks and and correction well noted

hey prubyholl,

i know this might seem a bit basic... but have you set your router SSID name ?

i am guessing that you have not named your router ssid name, and that your PC MAC address is 00:1E:2A:10:5D:38?

i mean if you dont give an SSID to your Netgear router then it might cause problems like you mentioned above.

from
Karan Pratap Singh
Chandigarh, India

---

