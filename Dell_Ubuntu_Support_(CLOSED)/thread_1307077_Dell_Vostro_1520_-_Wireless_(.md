---
title: "Dell Vostro 1520 - Wireless :("
date: 2009-10-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by doshaxxer on 2009-10-30
Hello..

I have to admit that I am a windows-guy.
But I would rather use ubuntu to study. So I decided to install ubuntu 9.10 on my dell Vostro 1520. 

Unfortuanly, the wireless does not seem to work.
When I google it, I do not seem to be the only one. 

But all the guides all there, either they do not work or it is for an older version for ubuntu.. OR.. I just do not understand them :-)

I hope there is some "nerd" in here, who can help me with my wireless problem. It is not very practical having a LAN-input in the computer :-)


Have a nice day!
Ben

---

### Post by teward on 2009-10-30
It seems that this wireless problem is wide spread with many different wifi cards running 9.10, and nobody seems to be able to track the problem down.  Perhaps it's a bug in 9.10?

---

### Post by doshaxxer on 2009-10-30
Aw.. Really hoping they can find a solution!

---

### Post by coffeeaddict22 on 2009-10-31
Hi,
Can you be a little more specific?  I'm running a Studio 17 with a Broadcom 4328 card, and have had no problem with wireless.  What isn't working?
It'd be helpful if you could open a terminal (Applications/Accessories/Terminal), type in the following 2 commands, and post the output back.
```
lshw -C network
nm-tool

```

---

### Post by doshaxxer on 2009-10-31
I'm sorry :-) I'm a newbie .. :)
THe wireless wont work. The wireless icon on the computer doesn't light, and I can't find any wireless networks with Ubuntu.

On Windows I can find multiple wireless networks.
So right now, I'm hooked up with a cable. But I can't do that on the university. So I need to get the wireless to work :-)


  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:aa:9e:0c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:32 ioport:4000(size=256) memory:fe004000-fe004fff(prefetchable) memory:fe000000-fe003fff(prefetchable) memory:fe020000-fe03ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 


_____________________

  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:24:E8:AA:9E:0C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

---

### Post by doshaxxer on 2009-10-31
Anyone?
There seems to be a lot of trouble with the broadcom wireless drivers..
And as I told you before, I'm a newbie, so I don't get all those codes and so on.. 

I really need some help.. It's really annoying beeing stucked with this wire :(

---

### Post by rliegh on 2009-10-31
There's a great set of instructions here:
[http://swiss.ubuntuforums.org/showthread.php?t=1288865](http://swiss.ubuntuforums.org/showthread.php?t=1288865)
Those are what I used to get my broadcom wireless connection set up.

---

### Post by doshaxxer on 2009-10-31
Unfortuanly I don't have a CD.. :(


EDIT: I tried searching for that thing anyway.. It worked, the "Wireless" lights up !! :)

But.. But but but.. For some reason, I can't "Enable Wireless" - It's grey wich means that I can't press it.. ?

---

### Post by rliegh on 2009-10-31
> **doshaxxer said:**
> Unfortuanly I don't have a CD.. :(


EDIT: I tried searching for that thing anyway.. It worked, the "Wireless" lights up !! :)

But.. But but but.. For some reason, I can't "Enable Wireless" - It's grey wich means that I can't press it.. ?

Try clicking on the network icon and see what you get -if you click on it and you get a list of wireless servers, try connecting to yours.

---

### Post by teward on 2009-10-31
His problem is that it won't recognize the card, and thus doesn't realize a wifi card is connected to the system.

It might be the card used in the Vostro, and not related to the general Broadcom cards.

Lucky me that I use an Intel wifi card within my Dell Latitude E6500.  :)

---

### Post by coffeeaddict22 on 2009-10-31
Sorry, live on the other side of the world.  

Have you checked in System/Administration/Hardware Drivers?  There may be a driver there you need to enable.

Linux is recognising your card- that's how you're getting (quote)

description: Network controller
[B]product: BCM4312 802.11b/g
vendor: Broadcom Corporation[/B]
physical id: 0
bus info: pci@0000:0e:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:18

The problem is the driver.

---

### Post by Ulysses361 on 2010-04-29
Hi doshaxxer,

If the network manager still does not let you enable wireless, you need to get the latest BIOS from Dell. There's a bug in the old BIOS version in your Dell Vostro 1520 laptop. BIOS versions A03 and up have this issue resolved.

See the links below for more info:

[http://ajtaylor.wordpress.com/2009/10/17/dell-vostro-1520-ubuntu-9-10fedora-11/](http://ajtaylor.wordpress.com/2009/10/17/dell-vostro-1520-ubuntu-9-10fedora-11/)
[http://www.linlap.com/wiki/dell+vostro+1520](http://www.linlap.com/wiki/dell+vostro+1520)

I quote:

"And it looks to be a Dell specific bug – the wireless kill switch (rfkill) is reporting an incorrect status to NetworkManager, which assumes that therefore the wireless is disabled.

Well, that lead me to a Dell Firmware update for the Vostro 1520, to A03 – bugs fixed? “Fixed incorrect WiFi kill switch status”.

So I think you need to flash the BIOS of your Dell Vostro 1520 to the newest version (version A08).

Steps to follow:

1. Install Windows on your Dell Vostro 1520 (BIOS update tool does NOT work in Ubuntu / Linux)
2. Get the Dell Vostro 1520 A08 BIOS update here:

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R262278&SystemID=VOS_N_1520&servicetag=&os=WLH&osl=en&deviceid=19174&devlib=0&typecnt=0&vercnt=7&catid=-1&impid=-1&formatcnt=0&libid=1&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=385402](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R262278&SystemID=VOS_N_1520&servicetag=&os=WLH&osl=en&deviceid=19174&devlib=0&typecnt=0&vercnt=7&catid=-1&impid=-1&formatcnt=0&libid=1&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=385402)

3. Flash the BIOS using the Dell flash utility
4. After upgrading the BIOS using Windows, install Ubuntu 10.04
5. After installing Ubuntu 10.04, install the bcmwl-kernel-source package (by the way: coffeeaddict22 is right in stating that your wireless card should NOT use the b43 driver, but the wl driver!)
6. Then reboot and retest wireless

Hope this helps,

Ulysses

---

### Post by PhoenixZA on 2010-04-29
I had the same problem. My Bios was updated prior to the linux install.

Solved
After 3 re-installs Testing 
1. Had wireless on
2. Changed network manager 
3. removed and re0installed broadcom drivers both


[LIST=1]
[*]Install with Wireless card switched off see (switch on the side)
[*]Get Lan/Cable Connection working
[*]Update all installed packages (I am using network manager)
[*]restart and check Internet Connection
[*]Switch wireless card on
[*]Go to System/Administration/Hardware Drivers
[*]Select Broadcom driver (NOT 43xx)
[*]Restart
[*]The will work but might not have internet access
[*]Check etc/network/interfaces
auto eth1
eth1 inet dhcp
gateway 192.168.1.xxx
[*]Check etc/resolv.conf
[*]restart
[*]Check etc/resolv.conf
[*]Check Internet
[/LIST]

---

### Post by PhoenixZA on 2010-04-29
I updated ndiswrapper but did not use the tool
I am using Ultimate Edition 64bit Dual Boot with XP Pro
vmware player running xp in linux as well

---

### Post by manzdagratiano on 2010-05-04
> **doshaxxer said:**
> Hello..

I have to admit that I am a windows-guy.
But I would rather use ubuntu to study. So I decided to install ubuntu 9.10 on my dell Vostro 1520. 

Unfortuanly, the wireless does not seem to work.
When I google it, I do not seem to be the only one. 

But all the guides all there, either they do not work or it is for an older version for ubuntu.. OR.. I just do not understand them :-)

I hope there is some "nerd" in here, who can help me with my wireless problem. It is not very practical having a LAN-input in the computer :-)


I believe you have a Broadcom Wireless card, and what you need to do is to installed the Broadcom STA drivers as follows: since you are already connected to the internet via ethernet, all you need to do is this:

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```Reboot and voila! You have wireless. I did the same with my Vostro V13. For more details look at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by manzdagratiano on 2010-05-04
And well... six years ago I used to be a Windows guy too - thinking that there was no need for "all that Linux mumbo-jumbo". My opinions have since undergone a radical change, and I have realized the importance of being able to use and enjoy software freely; software should be free and open - at the very least in its ideology, which is why Windows is a gangrene that needs to go.

---

### Post by nex1982 on 2010-06-11
Here is how I made wireless work on my Dell Vostro 1520: [http://nileshtrivedi.com/ubuntu-1004-on-dell-vostro-1520.html](http://nileshtrivedi.com/ubuntu-1004-on-dell-vostro-1520.html)

---

### Post by jarviser on 2010-06-11
If Broadcom don't want to play nicely you could always get an Intel card  from ebay for not much money. My Insprion 1520 uses the  Wireless-n 4965AGN out of the box no changes.  Like Canon scanners don't work so buy an HP; stuff them if they won't co-operate.

---

### Post by DiegoBravo on 2010-07-14
Had the same problem w/ ubuntu 10.04 w/ my vostro 1520.

I installed the driver via hardware manager but didn't work.

I had to do the firmware upgrade as told by Ulysses. On the first reboot it
detected the WIFI networks.

Weird, this was not needed with 9.04.

BTW, with the upgrade, the sound glitches went away.

---

### Post by Angelo Maldito on 2010-10-30
After several hours struggling to fix my wifi on my HP MINI 210, even with broadcom sta driver enabled, wireless supposedly enabled (but with the led light off and not able to see the available networks) I have finally found the solution here:

[http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/](http://life.firelace.com/2010/10/tips-and-tricks-upgrading-to-ubuntu-10-10-wireless-fix/)   (THANK YOU VERY MUCH DARKMOON !!!) 

The solution was simple, for whatever reason that I am not able to understand, after you intall the drivers and everything else, THE BLOODY THING COMES BLOCKED !!!

So in order to unblock, the goddamn thing just open a terminal, login as root ant type the following command:

rfkill unblock all


Thats is it, now its done, working perfectly !!!

I hope it save some hours for someone !

---

