---
title: "Dell Inspiron 1720 Laptop - 1935 Dell Wifi problems"
date: 2008-04-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ticat85 on 2008-04-30
Hey, I recently purchased a Dell Inspiron 1720 laptop computer and have decided to do the dual boot with Vista and Ubuntu... however the only problems I have had thus far (besides having to update my Nvidia drivers) is the wireless. In Vista, I am able to connect to any wireless network with no problem... howeverI have tried to get my wifi working in Ubuntu 8.04 with no luck whatsoever!

Yes, I have scoured the forums for my card, and I have followed the instructions for the ndiswrapper and have the proper driver for my card (bcmwl6.inf). Also, the Windows Wireless Drivers app recognizes the hardware.

Can anyone give me a clue on where I could be going wrong with this? Or is my wireless card just flat out not supported in Ubuntu 8.04?

Also, when I go into my Network Settings window, I do not have the option to even select a wireless network. I am given two options: Wired Connection and Point-to-Point Connection.

Any ideas? I'd hate to have to use vista anytime I want to venture away from my ethernet... but for now, I guess I have to. :(

Thanks!

---

### Post by mistywindow on 2008-05-12
I'm having the same vexatious problem. Set up wireless on my desktop where I don't need it, but the Dell Inspiron 1720 is a wireless brick wall.

Can someone out there *please *shed some light!

---

### Post by guerdon on 2008-05-13
I have a Dell inspiron 1720 and my wireless card isn't being recognized at all.....I am going to try to install the Windows drivers from dell with Ndiswrapper...If anyone here can help PLEASE DO!:confused:

---

### Post by oddsbodkins on 2008-05-26
Last I heard this was an issue with there not being any drivers available for the atheros wireless in the laptop... yet.

I just got myself one of these 1720s and have loved it with ubuntu, save that wireless problem. However, a $30 Linksys usb wireless works for me until the internal problem is fixed.

Wish i knew how to write drivers and i'd try and do that :P

---

### Post by mrbannerman on 2008-05-26
I have the same laptop and had tw reinstalls and an eighteen hour frustration until I discovered that in attempting to make the wifi light work I had installed an incorrect driver and accidentally pushed Fn F2 and turned the wireless radio off.
I have an Intel 2200BG wireless network card. Use lspci to check.
Good Luck

---

### Post by sam_delta on 2008-05-26
alright, first we need to know what chipset does your laptop have, post the output of the following command in the terminal (applications>accessories>terminal)
```
lspci
``` 

sam

---

### Post by dhruvraj on 2008-06-07
Hi Sam

Its the same problem on the same laptop with me. The wireless card doesnt even get recognised, and I've tried most of the tricks out there to get it work. I've even tried using ndiswrapper but to no avail. 

here is the lpsci - with no mention of my wifi whatsoever

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
d

---

### Post by sam_delta on 2008-06-07
> **dhruvraj said:**
> Hi Sam

Its the same problem on the same laptop with me. The wireless card doesnt even get recognised, and I've tried most of the tricks out there to get it work. I've even tried using ndiswrapper but to no avail. 

here is the lpsci - with no mention of my wifi whatsoever

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
d
yes it is recognized, your wifi card is 
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

ok to start now, do you have a wired connection? if so first make all updates go into system>administration>update manager, click on check and install then, with the wired connection still pligged, go into system>administration>hardware drivers, and check if there is any wireless driver listed there, if there are, enable them, if they are not there open a aplications>accesories>terminal and type the following to reinstall b43-fwcutter: (youll need a internet connection to do this, so keep your ethernet cable plugged)
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```
make sure you answer with 'yes' when promptd if you want to fetch a firmware when you type command #3
restart your computer and check if wireless now works or appear under system>administration>hardware drivers, if not ,,post back here and well proceed with ndiswrapper

if the commands of above returns any errors, post here

sam

---

### Post by mistywindow on 2008-06-07
To answer my own question above for those with a Dell 1720 and a Dell Wireless 1390 WLAN Mini-Card:

After looking here: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
I ran the following in Terminal:

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx

Then went into System Administration Hardware Drivers and enabled the broadcom wireless driver.

Didn't need to carry out the remainder of the instructions in that link, with a bit of fiddling the wireless network was available. :) Not sure whether or not any of the above commands were necessary. Certainly not the last. 

Other relevant stuff here:

[http://www.uluga.ubuntuforums.org/showthread.php?p=3762199](http://www.uluga.ubuntuforums.org/showthread.php?p=3762199)
[http://ubuntuforums.org/showthread.php?t=495056](http://ubuntuforums.org/showthread.php?t=495056)
[http://ubuntuforums.org/showthread.php?t=391961](http://ubuntuforums.org/showthread.php?t=391961)
[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)
[http://ubuntuforums.org/showthread.php?t=297092&highlight=1390+wlan](http://ubuntuforums.org/showthread.php?t=297092&highlight=1390+wlan)
[http://egypt.ubuntuforums.com/showthread.php?t=475963](http://egypt.ubuntuforums.com/showthread.php?t=475963)

---

### Post by sam_delta on 2008-06-07
alrigh im glad its working ,  good job getting it working

enjoy ubuntu :)

sam

---

### Post by mistywindow on 2008-06-07
> **sam_delta said:**
> enjoy ubuntu :)

sam

I really ***am*** enjoying it - it's a breath of fresh air. There's still a big learning curve, but it's worth it.

I've looked at Linux several times in the past but gave up because of the time commitment. The open source community have now made it easier and this time I looked at it from the point of view of "What *can* I do in Linux?" rather than "What *can't* I do?"

One big plus now is the ease of access to FAT32 & NTFS file systems. It was a mission for we newbies last time I tried.

I've been running Ubuntu 8.04 on my desktop and my laptop for about a month now as my default OS. It's great.

I will *not* be going back.

I've purchased my last Windows software. Any further payments I make for software will be donations.  I need to use Windows for a while yet, mainly for web editing, but with a bit of PHP scripting knowledge I'll soon be free.

It's great. I've already converted one grandaughter and her new husband. I feel a crusade coming on. :smile:

VirtualBox is also a boon to those of us making the switch. I'm running XP in a virtual machine to access my old data in Outlook and Info Select.

I'll miss a few Windows programs - particularly Info Select, SyncBack, Dreamweaver and Snagit, but I'll get over it.

:-({|=

Alan.

---

### Post by sam_delta on 2008-06-07
yeah, things in linux has become easier, specially in ubuntu, developers are making a really good job out there with ubuntu. The only and main problem (which is becoming less of a problem this days) is the hardware compatibility, but that has nothing to do with ubuntu developers, the problem is that manufacturers do not want to release linux drivers, some of them release chipset specs, making posible for the developers to make their own drivers, but there are companies who dont even want to release specs, so its a pain to get that hardware to work in linux.

people should realize that windows is nothing beside linux/ubuntu, much more secure, open source, free software. what else do you want!!?! xD

for your web development, i believe there are a few graphical design web developers such as dreamweaver, but ive heard they are not as good yet. so i use a software called bluefish, i like it very much for html/php development, you do not design the page with graphics such as you do in dreamweaver but has some functions and options that will help you alot, its a IDE(integrated development enviroment) its in the repos, do you can installit from add/remove, or synaptic. if you like the terminal install it by typing 'sudo apt-get install bluefish'

the best for you
sam

---

### Post by mistywindow on 2008-06-07
> **sam_delta said:**
> ..... The only and main problem (which is becoming less of a problem this days) is the hardware compatibility......
sam

Hardware compatibility is an even bigger problem with Windows upgrades IMO. I had to replace a perfectly good printer, a scanner and a modem when I switched from Win 98 to XP.

Same with software. A lot of new products which were OK in XP won't run in Vista.

> **sam_delta said:**
> ...... i use a software called bluefish, i like it very much for html/php development.....
samYeah, I'm using Bluefish - it's excellent, but I'm tied to Dreamweaver or Expression Web for dynamic content. I'm reasonably confident in hand scripting HTML and CSS but I don't know enough PHP to confidently cope with included content.

I'm working on it. 
:smile:

---

### Post by sam_delta on 2008-06-07
alright man, i cant actually say anyting about win xp/vista cuz i left windows on windows 2000 (yeah, ive used xp and vista, but not in my machines so i have no experience with drivers/etc) 
any other question, ill be around

the best for you
enjoy ubuntu
sam

---

### Post by dhruvraj on 2008-06-11
Sam

Thanks a lot for replying to my query. I did apply all the updates, and now have the new hardware driver - wl as it shows up under system-admin-hw drivers screen

And it is all working now :) -- posting frm ubuntu dell wifi - something i thought could have never happened after so many hours i had wasted already 

thx a lot

btw, since you seem to be an ubuntu expert - i have 1 more questions to ask you 

the most annoying feature of linux in general is the hw mixing of sound. this is the worst feature they could have ever concieved of. if ive opened a browser with youtube, i wont be able to use skype. i've tried using alsa but with that the limitation is that you have to configure sound driver for every application - something you cant do for browser and things like skype etc. i can open alsaplayer when skype or youtube is running but that just solves a partial issue.

---

### Post by sam_delta on 2008-06-12
hey dhruvraj, im glad your wireless is now working and i was able to help.

about your sound issues. i do not have too much experience in audio things, but few things i know that might help you.

if the problem is always with firefow, ive known of some people having this same problem with firefox flash, so ill asume that its flash issue. theres a known bug from firefox flash player to block all other audio, the solution is to install a package
```
sudo apt-get install libflashsupport
```
after installing this package,you might play changing drivers, if alsa does not work, change it to "automatic" or to "Pulse Audio" and see with which one it works best

you can change drivers by going into sys>prefere>audio

again, im not too experienced in audio, and a good long road in front of me on becoming an expert :p, i just try to help with the best of my knowledge

 here a few links that explain a liitle bit in more depth what is happning (assuming is the flash problem)
[http://tombuntu.com/index.php/2008/05/09/stop-flash-from-locking-system-audio/](http://tombuntu.com/index.php/2008/05/09/stop-flash-from-locking-system-audio/)
[http://ubuntuforums.org/showthread.php?t=824120&highlight=audio](http://ubuntuforums.org/showthread.php?t=824120&highlight=audio)

tell us how it goes with this sugested solution, ill keep doing research and see if i get something else.

if this does now work, you might also consider making a new thread under multimedia & video forum. just give me the link so i can keep track and keep helping if i can

sam

---

### Post by dhruvraj on 2008-06-21
Thanks Sam once again.

Also had one more question for you, regarding the same wl hardware driver that I got installed. 

I have to enable the hardware driver everytime I login, it comes as Not In use under the hardware driver window. I've to uncheck and check it everytime - is there a way to make it a permanent fix?

---

### Post by sam_delta on 2008-06-22
yes, ofcourse there should be a solution for that, i just have to figure it out.

can you please post the complete phrase/name of the drivers you are enabling each boot up, (the one listed under system>admin>hardware drivers)

thx,
 sam

---

### Post by dhruvraj on 2008-06-23
Yes I've only two hardware drivers that come up

1. NVIDIA accelerated graphics driver (latest cards)       -->comes in use
2. wl                                                      -->not in use

I've to uncheck and check to enable this which lightens my wi-fi led then, and starts searching for wireless networks..



> **sam_delta said:**
> yes, ofcourse there should be a solution for that, i just have to figure it out.

can you please post the complete phrase/name of the drivers you are enabling each boot up, (the one listed under system>admin>hardware drivers)

thx,
 sam

---

### Post by sam_delta on 2008-06-23
> **dhruvraj said:**
> Yes I've only two hardware drivers that come up

1. NVIDIA accelerated graphics driver (latest cards)       -->comes in use
2. wl                                                      -->not in use

I've to uncheck and check to enable this which lightens my wi-fi led then, and starts searching for wireless networks..
alright, look, i want you to make a test, can you please restart your computer and when you enter ubuntu, open a terminal and type the following command
```
sudo modprobe b43
```then, check if your wireless works.

im not sure if the module b43 is the one you using, thats why i want to make sure.
post back here if it works/do not work

if it works, we will add it to run at start up, if it doesnt, we will try something else

sam

---

### Post by dhruvraj on 2008-06-23
Thanx for the reply Sam, but sudo modprobe didnt work after I restarted.

It didnt throw any error but it didnt enable the wifi either

> **sam_delta said:**
> alright, look, i want you to make a test, can you please restart your computer and when you enter ubuntu, open a terminal and type the following command
```
sudo modprobe b43
```then, check if your wireless works.

im not sure if the module b43 is the one you using, thats why i want to make sure.
post back here if it works/do not work

if it works, we will add it to run at start up, if it doesnt, we will try something else

sam

---

### Post by sam_delta on 2008-06-24
hey dhruvraj

to be honest i currently dont know how to do that, there is of course a solution to your problem.

ill keep researching, and experimenting to see if i find the solution

id also recomend you to start a new specific thread, either under "wireless and networking" , "general help" or "absolute begginer talk" sections of the forum, there might be someone else out there who know the answer but cannot see this thread.

just copy a link to your new thread here, so i can keep a track on your new thread, and if i find something, ill go and post there.

sam

---

### Post by suyog on 2008-08-28
Sam,

I am Suyog, newly switched on to Ubuntu. Complete novice with Linux.
I have Dell Inspiron 1520 C2D, 2gb. I have done dual boot with vista.
When I go in network manager, I can see wireless networks but when i click to connect, nothing happens.
As i said i am novice with linux, please let me know solution.

Best Regards,
Suyog

---

### Post by sam_delta on 2008-08-28
whats your wireless card??, if you dont know, open a terminal (applications>accesories>terminal) and type the following command
```
lspci
```
and post the output here

ill see if i can help, but consider making a  new thread so more people can see it and post solutions.

thanks
sam

---

