---
title: "Need help setting up wireless internet"
date: 2005-11-15
forum: Desktop Environments
---

### Post by xaos on 2005-11-15
Hi, I'm new to Kubuntu (and Linux) and have some trouble getting my wifi fired up. 

I have a Compaq pressario r3000 with a broadcom card. I managed to finally get my card turned on using this [HOWTO]("http://ubuntuforums.org/showthread.php?t=25683"). In short I installed ndiswrapper. Now when I give the: ```
sudo modprobe ndiswrapper
``` command the light of the wireless card lights up, but it doesn't seem to find any networks. Right now I'm working at home on the wireless network, so I know the signal is OK. At work I use a LAN, so I just need to set it up for one network only. The network I use here is key-protected (WEP).

Any help would be greatly appreciated.

---

### Post by xaos on 2005-11-17
Hmm, pehaps I should have mentioned that I also tried editing the file /etc/network/interfaces to include the network name and key like this:
```
iface wlan0 inet dhcp
wireless-essid "network name"
wireless-key xxxxxxxxxx
auto wlan0
```

---

### Post by littlepr on 2005-11-18
xaos,


I have the same model laptop wiith built-in broadcom 4306 wifi. I had to use the same HOWTO to set mine up. First I set it up  with no WEP/WPA active on my AP and it worked fine. Once I enabled WEP on the AP side I had to set WEP SSID and key through tool System --> Administration --> Networking on ubuntu. For Kubuntu with WEP enabled I have a script with my AP settings which I set up to autostart my wlan0 interface everytime I boot up the laptop. This was the only way I got it to work. I tried the default wifi manager in KDE but had no luck on getting it to save my wireless profile so that it would work on every boot without having to re-enter the WEP key over and over again.

So here is my question to you. You state that it is working at home on a wireless network? or wired? Is it open/non secure or is it set with WEP? 

At work you connect through a LAN but are you trying to connect to some wireless network that you know exist at work? If this is the case then you might want to install wifi-radar. This acts just like the Windows wireless scanner.

[http://www.bitbuilder.com/wifi_radar/](http://www.bitbuilder.com/wifi_radar/)

If you still can't get to pick up AP signals at work let me know and I will try and see what else I can do to help.

---

### Post by xaos on 2005-11-18
Thank you for your help. At home I have a wireless network, secured with WEP. I can connect to this without problems when I boot WinXP, but Kwifimanager can not find any networks, or least doesn;t connect to any. At work I have indeeed a wored network, so I can boot linux and connect to the internet, the problem is there are no woreless networks here to test my settings.

Anyway, it seems that in my attempts I have messed up all my settings and plan to do a clean install of Kubuntu, after that plan to try wifi_radar and hope it will work.

---

### Post by xaos on 2005-11-20
So I did a clean install of Kubuntu 5.10, used the same howto as above to install ndiswrapper, and then installed wifi-radar.
Now when I do
```
sudo modprobe ndiswrapper
sudo wifi-radar
```
the wifi-radar GUI comes op but I still have some problems connecting to my network. When I tried it yesterday it gave me "connected to AKMBENZ, ip none" (where AKMBENZ is my network) and I saw some error messages in the shell. Today I tried it again.

So when I startup wifi-manager I see a nice list of available networks, my neighbours' (all unsecured) and ours (secured). First I removed all the profiles I made yesterday to give it a clean start. Then I clicked on our netwerk and connect, and decided not to create a profile to see what would happen. At this point I noticed that I was connected to one of our neighbour's network and had an IP address (I don't know if this happend before or after connecting to our network). I verified that I was connected by browsing to some pages. 

So this was a good start, but I want to connect to my own network. So I pressed disconnect and this showed up in the shell:
```
Stale pid. Removing
```
Now I tried again connecting and creating a profile for our network (and entered the WEP- key). After searching for an IP address for a while it give again "connected to AKMBENZ, no IP". (and indeed browsing did not work anymore....). When I tried to disconnect again this came up in the shell:
```
File "/usr/sbin/wifi-radar", line 907, in disconnect_profile
   disconnect_interface()
File "/usr/sbin/wifi-radar", line 420, in disconnect_interface
   os.kill( int(open(DHCP_PIDFILE, mode='r').readline()), signal.TERM )
ValueError: invalid literal for int()
```
I tried connecting and disconnecting to the network (and to ome of the not-secured ones) and it gave me the same errors. At some point the program started looking for an IP address upon connecting and become non-responsive.

Now this is all getting way beyond my newby-linux skills. So if anybody can give me some advice on an easy way to connect to my wireless network. I just want to have an internet-connection so I can boot linux at home and take my time in getting to know this OS.

---

### Post by littlepr on 2005-11-21
Xaos, 

Later tonight I will try to give you some. Help. This will be around 8:00pm New Eastern Time (New York).


Update:

I came to check up on you but no show. Can I assume you got it to work?

---

### Post by xaos on 2005-11-22
Hi sorry about that, was at a thanksgiving dinner. I'm at work right now so don't have much time now either. Thanks for trying though.

edit: so, no, I didn't get it to work yet.

---

### Post by littlepr on 2005-11-22
Have you tried wlassistant? You have to install it as root and edit sudoer to get it to work for non-root. 

[http://www.kde-apps.org/content/show.php?content=21832](http://www.kde-apps.org/content/show.php?content=21832)

Description:
Wireless Assistant (wlassistant) is a small application that allows you to connect to wireless networks.

* MAIN FEATURES:
- Managed Networks Support
- WEP Encryption Support
- Not Broadcasted ("hidden") ESSIDs Support
- Per Network (AP) Configuration Profiles
- Automatic (DHCP, both dhcpcd and dhclient) and manual configuration options.
- Connection status monitoring.

* MAIN REQUIREMENTS:
- wireless-tools 27 or newer (with iwlib)
- dhcpcd or dhclient
- sudo
[B]
[COLOR="Red"]* Example sudo config: If you want to create a e.g. 'wifi' group which users should be allowed to use wlassistant, add the following line to your /etc/sudoers:
%wifi ALL=NOPASSWD: your_kde_dir/bin/wlassistant[/COLOR][/B]

NOTE: You must create this group (wifi group) with add user/group admin tool for the above example to work or just substitute wifi with a prexisting group which you are already a member of. If that doesn't work try reading the developer's suggestion on the wlassistant forum: [https://sourceforge.net/forum/forum.php?thread_id=1365920&forum_id=455252](https://sourceforge.net/forum/forum.php?thread_id=1365920&forum_id=455252)

---

