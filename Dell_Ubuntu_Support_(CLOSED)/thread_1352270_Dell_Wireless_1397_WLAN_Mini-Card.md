---
title: "Dell Wireless 1397 WLAN Mini-Card"
date: 2009-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by junebhryan on 2009-12-11
Hi, Newbie here!

I installed Ubuntu 9.10 in my Dell Inspiron 1440 using Wubi to have a dual OS boot (VISTA SP2). Everytime I boot using Vista I can connect wireless and hardwired but if I boot using Ubuntu my hardwired connection works however my wireless connection doesn't work. It can't identify the any wireless network. I already tried to configure the SSID, MAC and WPA encryption in the wireless network and still won't connect.

I tried to search online to resolve my issues but most of the things are too ambiguous for me to understand so far these are the things I was able to find..

WLAN Card Data

Dell Wireless 1397 WLAN Mini-Card 
driver provider broadcom 
driver date 10/22/2008 
driver version 5.10.38.26 
digital signer microsoft windows hardware compatibility published 


using sudo lshw -C network

  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:25:64:5b:9a:66
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:de00(size=256) memory:f0010000-f0010fff(prefetchable) memory:f0000000-f000ffff(prefetchable) memory:f0020000-f003ffff(prefetchable)

Please help me out how to get the wireless connection working!

Thanks!

---

### Post by mikewhatever on 2009-12-12
Dell uses a lot of Broadcom products with closed source drivers, which aren't installed by default. In fact Dell Wireless 1397 WLAN Mini-Card is a camouflage for BCM4312. It pretty easy to install the driver however. There is a utility under System->Admin->Hardware Drivers that can download and install it. Note, it needs an internet connection to work.

Many Karmic users reported the Harware Drivers program didn't work for them. In that case, install bcmwl-kernel-source package from Synaptic package manager, or from Terminal.

```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by ublintu on 2009-12-12
OR if you don`t have Internet connection, the answer is on the CD... You can try this (the first post) : 
[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by junebhryan on 2009-12-12
thanks guys I will try it!

---

### Post by junebhryan on 2009-12-14
Hey!!!

I was able to make my wireless connection work... This I how I did it. I activated the Broadcom b43 wireless driver from Hardware Drivers. Then opened Synaptic Package Manager and installed bcmwl-kernel-source making sure that in the Repository, CDrom with Ubuntu 9.10 'karmic koala' is not checked because I have hardwired internet connection . Reloaded then applied the settings. Restarted the computer. Configured my wireless connection. Able to browse. Issue resolved.

Thanks for the help!

---

### Post by solomonhomicz on 2009-12-15
I have a Dell Inspirion 1545 64-bit, with the Broadcom BCM4312 wireless.
The wireless has worked beautifully through two upgrades, from 8.04 to 8.10 and again to 9.04.
However, the latest upgrade to 9.10 was not so nice.
See: [http://ubuntuforums.org/showthread.php?t=1355310&goto=newpost](http://ubuntuforums.org/showthread.php?t=1355310&goto=newpost)
It did not work at all at first, after just screwing with every little thing relentlessly it began to work.
Then it didn't work, now it's working again...,I'm beginning to feel bipolar!

Anyway I've followed a few threads, followed two different wireless tutorials from Ubuntu community documentation, everything seems to check out most of the time...,sometimes there's no wireless device at all then I'll check again and there is.
I'm not sure but I think the problem is related to the wireless button(actually the f2 key).
In previous versions this button did nothing, I could accomplish anything I needed by clicking on the network manager icon.
Now it seems the button works...,sort of...,

If I start up, log in hit the button, and just wait it connects.
If I hit the button to disconnect then try reconnect later the network manager will show the available network but say "disconnected" it is impossible to connect at this point without reboot.
If I open the network manager icon (this is while the swirly things are going around) to check network status it shows the network and signal strength but will not actually connect.
It will swirl for awhile then stop, then start again, when it starts again it throws up a popup that says network disconnected, this sequence goes on and on no matter what you do, button also does nothing.
It seems that if I just hit the button once and don't dare even think about touching the network manager icon, then it will connect, but God forbid you touch that icon or that button again.
All the right drivers are installed and everything works perfect when it works.
When it doesn't work, everything checks out fine just no actual connection.
If I use <ifup> it says the interface doesn't exist, then I check <iwconfig> and it says it is there...,???
Anyway, anybody else with anything similar?

---

### Post by Theophrastus On Character on 2009-12-20
Hi, I have a similar problem with the wireless connection. Followed the direction below, and I was able to install both of the drivers below but the wireless isn't picking up any signals. Suggestions please. As for configuring the connection, I'm unsure what that means. Thanks 

"I was able to make my wireless connection work... This I how I did it. I activated the Broadcom b43 wireless driver from Hardware Drivers. Then opened Synaptic Package Manager and installed bcmwl-kernel-source making sure that in the Repository, CDrom with Ubuntu 9.10 'karmic koala' is not checked because I have hardwired internet connection . Reloaded then applied the settings. Restarted the computer. Configured my wireless connection. Able to browse. Issue resolved."

---

### Post by chenxiaolong on 2009-12-21
Please check my post (post #7,page1) in this thread: [http://ubuntuforums.org/newreply.php?do=newreply&p=8539988](http://ubuntuforums.org/newreply.php?do=newreply&p=8539988)

---

### Post by maraja on 2010-01-01
Hallo,

I have recently switched to Ubuntu 9.10 64bit to see if I can get my system perform a bit faster and get full use of the installed 4Gb RAM.

My system is a Dell XPS M1330

Since the new installation the wireless started acting weird. When I turn on the system the wireless sometimes is recognized sometimes not.

Then the wireless was never recognized every time I started the system and I had to reboot few times before being able to use the wifi connection. 

As the wireless worked pretty well on this system with 8.04, 8.10 and 9.04 (all 32 bit versions) I tough about a possible hardware issue and ran the Dell diagnostics which reported the system is ok.

After some google searches I landed on this page and installed the Broadcom drivers ```
sudo apt-get install bcmwl-kernel-source
```

Then rebooted a couple of times and now it looks like the problem is gone.

My question is that I am not sure the wireless card is a Broadcom, looking at the output of *sudo lshw -C network*:

```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:81:d8:af
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.102 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f1ffe000-f1ffffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:9b:f2:a5:7d
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:31 memory:f1bf0000-f1bfffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

it seems that the wireless board is an Intel and the ethernet interface is a Broadcom so I cannot understand how the new driver fixed the issue.

Is there anyone able to give me a clue?

thank you and have a great 2010!

---

### Post by solomonhomicz on 2010-01-01
I'm not sure if this is a driver issue, I'm beginning to think it is the network manager or something deeper.
I have had bcmwl-kernel-source installed all along (since installing 8.04 from livecd) and am getting the same kinds of problems.
I'm an engineering student and I use a wi-fi connection while at school. 
However, I live in a rural area so I'm confined to a dial-up modem at home.
I am having similar problems at home, with a Zoom usb modem.
The gnome ppp dialer never worked right so I used wvdial and made a launcher icon with a simple <sudo wvdial>.
I ran wvdialconf one time way back, it found the modem on 'ttyACM0'.
The configuration has worked flawlessly until now.
Now, I have to run wvdialconf everytime before I can execute wvdial successfully.
The modem port randomly wanders from ACM0 to ACM4, if at all.
If I type 'lsusb' it finds the modem everytime, but wvdialconf only finds it about half the time.
So, I rerun wvdialconf until it finally finds the modem.
Then I run wvdial, it works about a third of the time.
When it doesn't work the reply from my isp is missing letters and the modem won't respond to the login prompt.
Sometimes it will say it doesn't know what to do and it will start the pppd and hope for the best.
When it starts the pppd blind it works every time.
Otherwise, it will finally either time out or it will say no modem is present.

Now here is where the two problems get very similar:
     1. If I start up and _immediately_ after pressing enter after login, I press and hold the wifi button for about three seconds. When my desktop finishes loading the wifi is already connected _everytime_. If I don't do this..., I might, maybe get a connection by pressing the button, but it will probably just endlessly connect and disconnect once I do. Also, you can hit the button while it is connected to disconnect. It will dissconnect but will NOT connect again until a reboot. May as well just reboot every time you need to try again.
     2. I noticed that upon plugging in the modem a few seconds later the 'data' light will flash for about five seconds. So I make sure I'm already in sudo mode. Type in sudo wvdial aand wait. Plug in the modem and hit enter _while_ the 'data' light is flashing. Wvdialconf runs perfectly, the modem passes with 'OK' at all baud rates and wvdial performs perfecly. This works _everytime_, but wvdialconf has to run at the same time the modem is recognized.

Everything is up to snuff all tests check out fine, have all the required drivers, but network connections are screwy as hell unless I do the things described above. It seems that if you use your network at exactly the same time the device is being recognized (upon startup or plugin) everything works beautifully. This leads me to beleive that there is something goofy going on with the way the system recognizes and allocates resources, or the way the network manager recognizes resources. But those subjects are way over my head, hopefully somebody will track down the root of this problem.
     I am and will remain a Ubuntu fan, but 9.10 is severly hobbled by these network difficulties. I use the internet extensively at school. I also do alot of programming in fortran and regularly backup my files on the school server using sftp. I used to use ssh quite a bit becuase the schools compiler was ifort and I was using gfortran. I would compile my work over ssh because there were some quarellsome compiler differences and my programs had to be able to be compiled  by the teacher at school. Anyway, I think we all get the picture, no network connection - severly hampered ubuntu.

     I'm thanful to have found some little tricks to make everything work. However, newer users could be seriously shut down by this problem (I fell I've just gotten lucky). This is like the old beater car you have to pump five times, hold the pedal down for ten seconds, hold the shifter in neutral (otherwise it'll pop into reverse), turn the key and pray, otherwise it'll flood out and you'll have to drink ten beers before it will start again.
Good luck!

---

### Post by maraja on 2010-01-03
update: after 2 days the wireless is not working again.
After I reboot for 3 times it start working again.

I made additional searches and found out this post:
[http://www.uluga.ubuntuforums.org/showpost.php?p=8424682&postcount=20](http://www.uluga.ubuntuforums.org/showpost.php?p=8424682&postcount=20)

after having installed the backports, turned off the system and started up again the wifi seems to work.

Will keep you updated in the coming days...

---

### Post by solomonhomicz on 2010-01-03
Excellent,
Thank you for the link maraja.
Installed backports and modem is working normally again, after two restarts no problems.
Haven't gotten to a wifi connection yet, will post when I do.
Thanks again
:guitar:

---

### Post by jdp2681 on 2010-01-11
I just upgraded my parents dell laptop to 9.10 and the wireless stopped working.  It was working just fine in 9.4.  I did find some information on how to get it working but now I have an interesting issue that has started and it is very similar to other post.  When I turn the computer on I have to Press the wifi button (F2) because the card is disabled.  at this point every thing works fin until I shut down the computer.  When I turn it back on and press the wifi key it will try to connect then report that wifi is disconnected.  After a lot of trial and error I started to notice that I was getting a connection every other reboot.  This is when I tried pressing the wifi key before I turned the computer off.  Once I restarted the computer I still had to press the wifi key and it was able to connected every time as long as I disable the wifi before shutting down.  I repeated this process 6 time to insure that it was a valid work around and it was successful every time.  I am looking for a way to not have to have my parents follow this work around as they are fine using Ubuntu and really like it but they are just computer users (I tell them to do something some way and they do it.)  I can see that they may forget to follow this workaround the I will be getting a call that they can not get on line and I have to walk them through 2 to 3 reboots to get the pattern back in line.  Can anyone help? ](*,)

---

### Post by chenxiaolong on 2010-01-11
This seems like it's more of a BIOS issue than a Ubuntu issue. I've actually had this problem in Windows before. You could try resetting the BIOS by pressing on boot up: F2 > Left Arrow > Reset Settings. If that doesn't work you might need to upgrade your BIOS ([http://support.dell.com](http://support.dell.com)). The current version for the Dell Studio 1555 (my laptop) is A09.

Good Luck

---

### Post by solomonhomicz on 2010-01-11
jdp2681, did you notice if the wifi(f2) button worked in 9.04?
My wifi button didn't do anything in 8.04 or 8.10 and I honestly never checked it in 9.04.
Everything worked from the network manager icon and the button didn't do anything.
Now the button behaves very similarly to your situation.:???:
I tried the backports but my modem problem returned after two days and I haven't checked the wifi yet.
Is yours still working maraja?
Does anybody know a way to temporarily disable the f2 button?
It would be interesting to see how the wifi behaves with the button disabled.:-k

---

### Post by maraja on 2010-01-23
after a couple of weeks my xps did not like to use the above solution anymore...

I found this one and, at the moment, it works:
[http://ubuntuforums.org/showpost.php...3&postcount=30](http://ubuntuforums.org/showpost.php...3&postcount=30)

hope this is the final solution ):P

edited, sorry the link was wrong:
[http://ubuntuforums.org/showpost.php?p=8710493&postcount=30](http://ubuntuforums.org/showpost.php?p=8710493&postcount=30)

---

### Post by cygnl7 on 2010-01-23
> **maraja said:**
> after a couple of weeks my xps did not like to use the above solution anymore...

I found this one and, at the moment, it works:
[http://ubuntuforums.org/showpost.php...3&postcount=30](http://ubuntuforums.org/showpost.php...3&postcount=30)

hope this is the final solution ):P

It looks like that link might have been copied and pasted from the displayed text because there are '...' instead of the middle of the link.  Can you repost?

---

### Post by jlane01 on 2010-07-25
I have a dell 1545 64 bit system with a broadcom wireless 1397 card.  I love ubuntu 10, but could not get my wireless card to be recognized.  I had to go back to ubuntu 9.04 to get my wireless card recognized.  Once I started updating after installing 9.04 my wireless card was immediately recognized.  Any idea when 10.04 will be updated to recognize it??

---

