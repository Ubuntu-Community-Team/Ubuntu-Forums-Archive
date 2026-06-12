---
title: "Inspiron N4010 wireless disbaled"
date: 2010-08-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by solace.discord on 2010-08-22
this is my first time using Ubuntu.

I have a Dell Inspiron N4010 i14r-2265 with the i5 and Windows 7 Pro dual-boot to Ubuntu 10.04 through wubi installer on a separate partition. the dual-boot works flawlessly.

I followed the instructions in this post to get the Ethernet card working. but I mainly use my laptop wirelessly.
[http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697)

I have the Intel WiMax/WiFi Link 6050 Series rev57 according to the output from a terminal command. I have downloaded the drivers, but have no clue how to install. I tried to move the files into the drivers folder, but I'm told I don't have access.
[http://www.intellinuxwireless.org/?n=Downloads](http://www.intellinuxwireless.org/?n=Downloads)

I have searched for a few days now, and cannot find a solution to this issue. I have tried to toggle the wireless on/off through Windows a few times, I have changed the Power Settings to keep the device from shutting off. and through another terminal command, I can see that the device is on, it is recognized, but it is consistently disabled. terminal says the driver is iwlagn

Can someone please help me enable my wireless card?

---

### Post by Nerotique on 2010-08-23
I have this same laptop.  I noticed that if you use the live CD before installing, and then enable the broadcom driver from the restricted packages, everything works just fine.  If you go straight to the install, the wireless card doesn't seem to work.

---

### Post by mörgæs on 2010-08-23
In general it is best to have wired internet access while installing. It prevents a lot of problems.

---

### Post by solace.discord on 2010-08-23
as I described, I used wubi to install on a separate partition- I have a live cd, but did not use to install, and I cannot find the drivers I need on it. I had to enable the wired ethernet connection while in ubuntu using instructions from another thread. and even after that was fixed, using the live cd, I still could not get wireless to work.

I do not have a BroadCom card- I have an Intel card, I have downloaded the drivers from the link above, but I can't for the life of me figure out how to install them. where the hell is the hardware manager in this thing? the proprietary drivers box is empty.

and its not like I need drivers either.. it's there, its installed.. but it is consistently disabled and I can't find how to enable it.

this will stop me from using ubuntu, and that is very unfortunate! someone please help.

---

### Post by mörgæs on 2010-08-24
According to this
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451)

you need to have lucid-proposed enabled to get the updates. Is it?

Else trying 10.10 could be an option, if you don't mind working with a release which is still a work in progress.

---

### Post by solace.discord on 2010-08-24
> **mörgæs said:**
> According to this
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451)

you need to have lucid-proposed enabled to get the updates. Is it?

Else trying 10.10 could be an option, if you don't mind working with a release which is still a work in progress.

I don't know what the lucid-proposed enabled is.. where do I find it?

I followed several threads. I downloaded the drivers from the link in my first post. how do you install drivers? why are there no drivers listed in the Proprietary Drivers box? where is this Hardware Manager I've heard of? why is my wireless card *disabled*- it exists, it is installed, recognized, etc.. it needs to be enabled and I don't know how.

my eyes are crossing with all these codes to run or registry edits to do- I don't understand what any of it means, and I don't know what I'm doing to want to make potential mistakes. I want to learn, but getting my wireless working is top priority.

---

### Post by mörgæs on 2010-08-24
> **solace.discord said:**
> I don't know what the lucid-proposed enabled is.. where do I find it?

It is in 'software sources' in the 'system'-menu.

---

### Post by saiki4116 on 2010-09-15
me too facing the same problem..can anyone help me to fix this..

---

### Post by xsandman.32 on 2010-09-15
Depending on the filetype for the driver you may have to do a lot of work in terminal. My suggestion (which has worked pretty well for me) is start googling and reading the basics of installing stuff in Ubuntu. It starts out pretty tricky and I'll say I didn't understand what I was doing but it made things work, after that everything will start to click. I would suggest looking in to ./configure ./install make and make install

---

### Post by cybetech on 2010-09-15
I'm slowly going insane. I had a Acer netbook that I put Ubuntu netbook edition on it and it worked immediately connecting to the Internet via a wireless router. 

Yesterday, I purchased an HP all in one desktop and installed Ubuntu desktop 10.04, but I am unable to see any wireless connections let alone my own. I am new to linux, so forgive my ignorance, but I saw some other postings on commands to get info from terminal and I did that, but mine says it is disconnected. My problem is, I have wireless set up through my cable company so I cannot get online at all on the computer to even make updates. I can manally download them from my netbook to my USB and load them on the desktop, but I have no idea what to do with them once I drag them to the desktop from the USB. 

Ok - I connected my desktop directly to my LAN 

Any help would be greatly appreciated. 
and it connected immediately, so it is just the wireless that I cannot connect to. 
Teri

---

### Post by mörgæs on 2010-09-15
Cybetech, please open a new thread in stead of hijacking this. If you do that and describe exactly which net card you have, then I am sure you will get help.

---

