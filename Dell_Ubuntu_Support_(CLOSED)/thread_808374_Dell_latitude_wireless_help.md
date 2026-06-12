---
title: "Dell latitude wireless help"
date: 2008-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Corvair on 2008-05-26
Hello every one.
I just installed 6.06 LTS, it would not take 7.04, on a Dell Latitude c510/c610 model PP01l for a friend. It replaces a windows installation.
It works very well with all the 306 updates, on a wired lan internet.
The problem is that he has wireless access only and I can,t seem to get it working on wireless.

The adaptor is a Nova Tech 54 Mbps Unwire Notebook adaptor.

When I check on network settings,  it says the interface ra0 is active
and also the interface etho is active but it won"t work on wireless.

Here is what I get on a terminal

dave@dave-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:1B:2F:FF:E6:12
                    Mode:Managed
                    ESSID:"ordinausore"
                    Encryption key:on
                    Channel:6
                    Quality:0/100  Signal level:-27 dBm  Noise level:-195 dBm

sit0      Interface doesn't support scanning.

dave@dave-laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ra0/00:d0:41:a3:0f:15
Sending on   LPF/ra0/00:d0:41:a3:0f:15
Listening on LPF/eth0/00:06:5b:e6:cb:03
Sending on   LPF/eth0/00:06:5b:e6:cb:03
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
ip length 318 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 10.0.0.1
bound to 10.0.0.3 -- renewal in 34717 seconds.

I hope this can be of some help to find the problem

---

### Post by sam_delta on 2008-05-26
why dont you try ubuntu 8.04 LTS?

sam

---

### Post by majickmann on 2008-05-27
There are a number of posts that address wlan installs especially with dells, in the forums.

I am curious why 7.04 would "not take"???  I've installed 7.04 and now 8.04 on Dell Lat C600 laptops.

Hint: kevdog is one of many contributors to forums with wlan solutions.

HTH...
:-)

--majickmann

---

### Post by Corvair on 2008-05-30
Hello,

Problem solved

After trying to install 7.04 again I cleaned up the hard drive by doing manual portioning and was able to install it.
But then I could not get wireless to function.
So I downloaded Ubuntu i386.iso version 8.04 and ventured into instaling it.

After 2 tries I had to do a manual install and portion the hard disk again and this time the installation went OK.
This time wireless was easy to install.

After upgrading my own Gateway MX6453 from 7.04 to 8.04 on the internet I had problems and problems. So I decided to reinstall 8.04 from the iso cd and the installation went OK. And wireless is working also.
Upgrading on the internet often goes wrong because of corrupted packets.

Thanks for your support.

---

### Post by sam_delta on 2008-05-30
no  problem, glad everyhtin is ok now

yeah, when you upgrade distro, some wireless fixes you applied on th previous version do not work on the new one, or perhaps needs some fix in order to make them work again. although upgrades work very good, theres nothing better than a fresh install


enjoy ubuntu
sam

---

### Post by rlacroix8 on 2008-06-06
Sam, I just installed 8.04 on my Dell Latitude D810 running XP; can't get the wireless to work [wired works fine]. Here is what terminal shows:
richard@richard-laptop:~$ sudo lshw -C network
[sudo] password for richard: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:e2:54:28
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5751-v3.29a ip=192.168.1.104 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a4:79:7c:65
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
richard@richard-laptop:~$ 

To my newbie eye this looks like my wireless interface is disabled, under Ubuntu [no problem under XP] If that is so, how can I enable this interface?

Incidentally, Fn+F2 only switches the Bluetooth connection on and off, NOT the WAN, as it does under XP.

Thanks in Anticipation

Richard

---

### Post by sam_delta on 2008-06-06
fisrst, before trying anything, with the wired connection plugged in, do all updates availabe, go into system>admin>update manager, click on check and install.

after all updates are availabe, go into system>administration>hardware drivers, ,,, check if there is a wireless driver listed right there, if it is, enable it and restart your computer and check if it works

if it does not work or there is no wireless drivers listed, post back here

sam

---

### Post by rlacroix8 on 2008-06-07
Sam, Sorry did not work. The hardware drivers shown are only:

ATI accelerated grahics driver .... not in use
Broadcom B43 Wireless Driver .... not enabled .... in use

I did "enable" the thing and restarted, twice. No success. 

PS Wanted to include a screenshot here but do not know how to get it here from the desktop; only get a location pointer.

Richard

---

### Post by sam_delta on 2008-06-07
alright, try reinstalling those drivers, youll need an internet connection, so plug your internet cable. but before, itll help if you do all sytem updates, go into system>admin>update manager and click on check then install
if your system is up to date we proceed reinstalling the drivers
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```
make sure you answer with 'yes' when promptd if you want to fetch a firmware on command #3.
restart your computer and check if it works or if you can enable the driver now undedr system>admin>hardware drivers
if any of the commands return any error, post back here
if it doesnt work, post back here and well proceed with ndiswrapper

sam

---

### Post by rlacroix8 on 2008-06-08
Sam, Just trying if this quick reply works again. Just send you a "private" message.

Richard

---

### Post by rlacroix8 on 2008-06-08
Sam, the quick reply works again for me, so I use this instead of teh private message.

Here is the response of iwconfig:

richard@richard-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:9E:D6:0A 


          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=63/100  Signal level=-45 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

richard@richard-laptop:~$ 

So, it appears that the name is indeed wlan0. However, it lists the bit rate as 48 MB/s. If that is correct I will not bother to change it, but still do not understand why right clicking on the "bars" gives me, at connection information: "Speed ....1MB/s". Also, above shows "link quality 63%, which is what the little window shows when I simply point at the bars. How can that be when my router is next to my computer?

Thanks 

Richard

Edit: I did NOT put in these emoticons.

---

### Post by sam_delta on 2008-06-08
ight, yeah that seems as a driver compability problem (the driver might not fit your wireless card that good), is your system up to date? have you made al updates? you can check by going into system>admin>update manager, and click on 'check' if indeed, your system is up to date, we should move to ndiswrapper, so, make sure you have all updates, if you do, and you wish to install ndiswrapper drivers, post here, and ill give you instructions

sam

---

### Post by sam_delta on 2008-06-08
also, just to make sure its not a network manager problem ( that the network manager is giving wrong information) try downloading some file from a 'known-to-be-fast' website, lets say, start downloading ubuntu,, from ubuntu.com and check whats your download speed, if the speed is not what you usually get, that means well have to move into ndiswrapper, but if your speed is normal, that might be a newtwork-manager giving wrong info and we just install another network manager

i really debt that the network-manger is returning wrong ingo , but  just to make sure

sam

---

### Post by rlacroix8 on 2008-06-09
Sam, First I upgraded, another 13 of them, although I did the same yesterday [that Ubuntu community is active!] Then, after rebooting,  I tried "internetfrog" first. This gave me in the first try: 3.74 Mbps down and 209 kbps up; in the second try, 10 seconds later: 2.20 Mbps down and 114 kbps up. This is an RCN cable connection, configured I believe as a LAN [for the neighborhood?] and I am thus not surprised by the fluctuating speeds. I then started downloading Handy Harry from Ubuntu and noticed that the download speed stayed just under 1Mbps with exception of two instances when it went momentarily to 1.1 Mbps. I all cases, Internetfrog and Ubuntu, the "connection information" box showed "Speed...1Mbps". Regards

---

### Post by sam_delta on 2008-06-09
alright time to give ndiswrapper a try.

for the next steps, it is very important for you to plug an ethernet cable since the wireless will not work when we remove b43-fwcutter.

first we need to make sure that very old drivers bcm43xx are disabled, and then install ndiswrapper by typing ```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
``` 

with the following 2 commands, we just make a new folder change our working directory (change to that new folder located inside your home folder) ```
mkdir ~/bcm43xx
cd ~/bcm43xx
```

now, we need to download and extract windows XP drivers we are going to be using, to do this, type the following commands ```
sudo apt-get install cabextract
ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
```

then we install the driver with the following commands
```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
```
here, the second command 'ndiswrapper -l' should return something like "drivers xxxxx installed: device present" that means we have the right drivers correclty installed, and we can move on to set ndiswrapper up
if you dont get that output, stop here and post your output

then, we set up ndiswrapper by typing ```
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

we remove b43-fwcutter we were using
```
sudo aptitude remove b43-fwcutter
```

now we need to make a simple script to fix some driver conflicts (this is a hardy problem) its easy to fix , just follow the following steps
```
sudo gedit /etc/init.d/wirelessfix.sh
``` this command will open a empty text file, when it opens, copy and paste the following: > #!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44 save the file and close it

finally we make this script executable and tell the system to run it each time you turn your pc on by typing ```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
sudo update-rc.d wirelessfix.sh defaults 
```

RESTART your computer and you should have wireless at its full power :P

based on [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

if you get any error message, post it here, any debts, post it here, any problems, post them here, anything post it here

sam

---

### Post by rlacroix8 on 2008-06-09
Sam, I am up the creek! the 8.04 CD I have does not boot. When asking for help, an option of the "umenu.exe" in XP, it does reboot, gives a choice of Ubuntu/XP and I choose Ubuntu. An MSDOS type screen stops scrolling with a message that I should go to the Ubuntu web site, something to do with the bc43. Had to disconnect power to get out of this mess. Fortunately, I have still a CD with the previous version 7.something, which I know will boot. I intend to do that and then ask to install that version, with the intention to upgrade it to 8.04. Will do all that to-morrow, Tuesday, but frankly I had not expected Ubuntu to be that involved. Cheers Richard

---

### Post by sam_delta on 2008-06-10
hey rlacroix, sorry to hear that, few things i would consider
 
first, make sure you uninstall ubuntu from windows, (ubuntu within windows)

upgrade from 7.10 to 8.04 is good, but not as good as a 8.04 fresh install, so id recomend you to give 8.04 another try.

this is the steps you need to follow
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

but again, just take care at the partitioner, so you keep your windows partition (you may resize it but not delte it)

BUT, before you try 8.04 again. forget about an umenu.exe, and anything related with windows. the only thing you have to do is insert ubuntu CD, and restart your computer, you should get into the CD menu where you can click on install/start ubuntu, you will get into a actuall ubuntu enviroment, this is called the 'ubuntu live CD' in which you will have an icon on the desktop which says 'install', you click on that icon and you follow the steps to install

if you insert the ubuntu CD and restart your pc, and it goes straight to windows, then, you need to change the boot order to boot off the cd, this is usually made by clicking some key while turning your computer on, it might vary from computer to computer for example in my computer is pressing F8 while turning on. you need to change the boot order to make it boot form the cd before the hard drive.

Also, when you make it to the 'live CD menu' theres an option which reads something like 'Check CD for errors' click on that option before proceeding , just to make sure your CD is well burned and does not have errrors before installing

you need to make it to the 'live session' if you cant, then theres an 'alternate install cd' which installs in text mode, either way, you have to boot off the cd, i have never used the umenu.exe tool, withing windows so i duno how it works, but id recomend to stay away of it

lets try to work this out 
dont worry, keep posting if unsure/have debts

sam

---

### Post by rlacroix8 on 2008-06-10
Sam, it has been a long day. The 8.04 version I downloaded was an ISO file. I thought that an "undisker" I downloaded would extract all files, which I did and then burned them on a CD. That was the CD that did not boot. I booted with the 7.10 disk I ordered some time ago. However when trying to load Ubuntu from that disk, before having read your message above, I ran into partitioning problems, with questions I did not dare to answer. I then followed more religiously the instructions on the Ubuntu web site to create a bootable Cd from my ISO file, using now "InfraRecorder". The resulting CD booted and I opted for "Install". All went well until the partitioning. I have a 40Gig HD, which the partitioner told me should be 67% XP and 33% Ubuntu. I agreed, but the partitioning failed, possibly because my HD is too small. I am now again in the Ubuntu version that runs within XP, but without all the goodies installed earlier, and no wireless. O yes, prior to the partitioning failure I had already uninstalled a lot of programs I never use, hoping to free up disk space. In addition I could now delete all my documents, pictures etc., about 9Gig, because I copied it all on an external USB 110Gig HD, usable on both XP and Ubuntu. What do you think? It is all getting a bit tedious, though.

Cheers

R

---

### Post by sam_delta on 2008-06-10
hey sorry to hear that, id recomend you defrag your windows partition before you try to go to the installer. go into windows and defrag your disk. and try again.

id bet that after you defragment your disk, the partitioner will work

if still does not work theres another thing you can do is this:
while in the 'live ubuntu' (before clicking install on the desktop) press alt-f12, then type "gksudo gparted",, a program called gparted will open, this program help you partition your disk. now

DO no create a new partition, all you have to do in gparted is select your windows partition and select Srink/move partition. and then shrink it to the desired size. AND LEAVE the the rest as 'free space' so you will only have 1 windows partition the size you want, and the rest as free space,,, again, do not create a new partition, leave it as free space.  

when done, close gparted and proceed with the installation. BUT when asked about the partition, theres a option that reads like this: "Use longest continuos free space" or something very similar (this option will appear in the window were you select how much % you want for ubuntu/windows, but your going to select the "Use longest continuos free space" option so the installer will leave win xp partition, and it will use the free space we left with gparted.

dont worry, ur doing fine
also, with a wired connection, you can come into the forums while in the "live ubuntu", so without having to reboot, you can come into the forums to ask for help while in the installation process.

any more questions, ill be here, dont hesitate to ask

sam

---

### Post by rlacroix8 on 2008-06-11
Dave, I have had it. I backed up my entire C drive onto an external HD and defragmented my disk using the windows program, which took a couple of hours. I then got into "gparted" but have no way to decide what to do after the resize/shrink operation request, hence I aborted that. I then went back to, and ran, "install", which gave me the same message as yesterday after an apparent attempt at partitioning, something in the spirit of "errors occurred..." I quit. I am now back in the live Ubuntu and am going to close and exit. When doing that yesterday and subsequently trying to run XP I got the scary "blue window" and an automatic CHKDSK operation which took about an hour. Fortunately I apparently passed, because XP loaded after that. I hope to be equally lucky to-day. Ubuntu is not for me; many thanks, though, for your assistance. Best Personal Regards - R

---

### Post by sam_delta on 2008-06-12
alrigh rlaxroix, thats fine, if you ever decine on comming back, ill be here to help, also, you can try to install in an old computer (if you have one available), that might get you to lern before you do on your primary, anyways, good luck bro, ill be here if you need anything

sam

---

### Post by rlacroix8 on 2008-06-27
Sam, just to let you know I am back. I put a new 120 Gig HD in my laptop, reinstalled XP etc., booted with the 8.04 CD, partitioned as you showed me earlier from within Ubuntu, splitting the HD in half for XP and half for Ubuntu and installed Ubuntu. I had not realized that Ubuntu can straddle the partition and let me read and write within my old document structure with XP - Great!

So, I am back now where I was before, but with an installed Ubuntu. I also reinstalled that b43 driver for my wireless with the "fwcutter" as you showed me. I thus do have wireless, but as you may recall, running at a low speed. As you suggested I may want to consider Ndiswrapper at some point.

Things seem to run fine, except that I can not get the microphone to record anything with "Applications > Sound & Video > Sound Recorder" on any settings. I have a Logitech USB Webcam with built-in mike, as well as another mike on the mike-in port. However, Skype works fine, when telling it to use the "USB device". Incidentally, the "Sound Recorder" does not have a setting to choose USB as input device. Any idea what's up?

Best, Richard

---

### Post by sam_delta on 2008-06-27
alright bro, im glad your back :)

to fix your mic, this is how i fixed mine, and should work for you. if you have any problems, ask again 

right click on the little speaker on the top right of your screen (in the notification area) and click on "open volume control", then click on "edit">"preferences" , and checkbox the "capture" and "input source" option. then close the preference pop-up, now in the volume control window, 2 new tabs will apear, the "recording" tab and the "input source" tab.
select the recording tab, and make sure the volume is all the way up, then select the "input source" tab and select the mic you want to use, in your case, it should appear the usb mic, mic jack, or internal mic.

then, in the sound recording application, just select as input "capture"

if any debt, or it does not work, post here

sam

---

### Post by rlacroix8 on 2008-06-28
Sam, I did all that, but the problem is that I do NOT have an "input source" tab. Also, when right clicking the little speaker I can click on "preferences". At present the "select the device and track to control" and  is set to "Intel ICH6 (ALSA mixer)". I changed that to "USB device" and then the only "track to control" is "microphone". Still, no sound recording.

A completely different problem. I look frequently at a foreign currency graph, produced by a company called OANDA. The graph should be at: [http://www.oanda.com/products/fxgraph/fxgraph.shtml](http://www.oanda.com/products/fxgraph/fxgraph.shtml) , but does not show in Ubuntu, although I have Java turned on in Firefox and I installed the JRE 6xxxx in Ubuntu. Any idea what can be the problem. I have also asked the bank through whom I see that graph for an explanation and will post here any reply [my bank has apparently subscribed to this OANDA graph as a service for its clients.

Cheers

R

---

### Post by rlacroix8 on 2008-06-28
Sam, do you know about this, [http://jak-linux.org/projects/ndisgtk/](http://jak-linux.org/projects/ndisgtk/) , purportedly a GUI for Ndiswrapper. If so, what do you think?

RL

---

### Post by Diggs808 on 2008-06-28
> **rlacroix8 said:**
> 

A completely different problem. I look frequently at a foreign currency graph, produced by a company called OANDA. The graph should be at: [http://www.oanda.com/products/fxgraph/fxgraph.shtml](http://www.oanda.com/products/fxgraph/fxgraph.shtml) , but does not show in Ubuntu, although I have Java turned on in Firefox and I installed the JRE 6xxxx in Ubuntu. Any idea what can be the problem. I have also asked the bank through whom I see that graph for an explanation and will post here any reply [my bank has apparently subscribed to this OANDA graph as a service for its clients.

Cheers

R

I am jumping in here.  I am able to get the graph to display.  Dell Latitude D820.  It is a java app so you might want to check to see if the Java add in for FF is installed.  

Diggs

---

### Post by Diggs808 on 2008-06-28
> **rlacroix8 said:**
> Sam, do you know about this, [http://jak-linux.org/projects/ndisgtk/](http://jak-linux.org/projects/ndisgtk/) , purportedly a GUI for Ndiswrapper. If so, what do you think?

RL

I have seen a GUI for Ndiswrapper in the add remove program.  Change the Show dropdown box to "all applications" and search for wireless.  It is listed as "Windows Wireless Drivers" and it is from the project you linked here.  I have used this on another laptop to get wireless working.  It worked really well and seemed pretty easy to use.

---

### Post by rlacroix8 on 2008-06-28
Thanks for jumping in. As far as I can see the Java app is enabled in FF. I have also looked at the "Sun Java 6.0 Plug In Control Panel" and believe to have done everything asked for; still no Java. The Sun site with instructions, [http://www.java.com/en/download/help/5000010500.xml#100](http://www.java.com/en/download/help/5000010500.xml#100) etc. does indeed indicate that the JRE is not operating on my system.

---

### Post by rlacroix8 on 2008-06-28
That's where I saw the reference. I could simply download it and use it but wanted some assurance that it works as promised. You seem to do that. Thanks

---

### Post by sam_delta on 2008-06-28
hey, yes, ive heard about the ndisgtk, but havnt used it myself,  you might want to find a good tutorial out there and give it a try. if you find any problem, ask here.

about your mic, i know you do not have a input source tab, you need to do the following to get it, follow the steps, 1 by 1

1. click on the little speaker and select, "open volume control"
2. once in the open volume control, select "edit>preferences" 
3. checkbox the "input source", and "captude" options
4. close the preference pop-up to get back to the volume control.
5. now in the volume control, you will have 2 more tabs, "input source" and "recording", select the "input source" tab, and select the device you want to input from.
6. now , go to the recording tab, and turn the volumes all the way up. 
7. close the volume control, and go to the recording application, select capture as the source.

any questions, please ask

sam

---

### Post by rlacroix8 on 2008-06-28
Sam, that is the problem, I do NOT have an "Input Source" box to check in "edit>preferences".

---

### Post by sam_delta on 2008-06-29
humm, strange, do you have "capture" and "capture 1" options??

sam

---

