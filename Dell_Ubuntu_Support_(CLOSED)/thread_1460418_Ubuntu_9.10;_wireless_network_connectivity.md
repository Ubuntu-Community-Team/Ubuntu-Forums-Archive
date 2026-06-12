---
title: "Ubuntu 9.10; wireless network connectivity"
date: 2010-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by anandnz on 2010-04-22
Hi Experts, 

I have finally successfully installed Ubuntu 9.10 on my DELL D610 
**Specs:**  1.73Ghz Pentium-M 
 1280MB RAM (1024 +  256, shared with video)
 
 Intel Graphics (915GM)
 SigmaTel  Audio
 
 Intel Gigabit Ethernet
 Dual band (a/b/g) Wireless
 Conexant modem

I am not able to connect to the wireless internet and without which i cannot do any thing, no updates, nothing. However when i boot from winxp, i have my wi fi enabled and connect to internet. Any help is much appreciated.

Cheers
-- Anand

---

### Post by epoh on 2010-04-22
I *just* went through this to get the wireless access working on my D620. You need ndiswrapper. 

Start here - [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)

There are a couple of steps - the first of which is properly identifying your device (which is easy since you've got it working under windows.) Secondly you need the .ini and .sys files from your windows load. The ndiswrapper then does a little magic to make those windows drivers work in Ubuntu. 

These - [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) - are the directions I followed. 

One thing to note, mine wouldn't work until I went into the Hardware Drivers gui and enabled the driver in there.

---

### Post by anandnz on 2010-04-22
Thank you very much Epoh,

As a freshman in ubuntu installation, please could you let me know how to identify the device ( you mean from My computer/hardware details).

2.  .ini and .sys files from your windows load, please could you explain which one's and where to find them. 

After this help, (push) i may follow the links you have kindly mentioned.
I will try this week end

Thanks a ton in advance. 
- Anand

---

### Post by anandnz on 2010-04-25
Hi epoh and other experts,

I have hit a wall following the links ..

lspci in my DELL D610 shows up this
03:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

lspci -n : 14e4:4319(rev 02)

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) lspci -n: 8086:266d (rev 03)


I need a few clarifications, please can someone help me.

1. Not sure how to get the relevant drivers for ubuntu for the above configurations to use ndiswrapper, i tried to get the same from windows xp, which is my primary boot
but unfortunately i can find only .sys file and search in entire window directory did not fetch me .ini and .bin files.  Any help please.

2. Once i have them, how to use the ndis wrapper any help there please.

3. Since i use BCM4311 driver, do i still have to black list them to have ndiswrapper see it? 

4. Lot of links say, we need to disable some drivers any list of them would be appreciated.

Thanks in advance
- Anand

---

### Post by Ralph L on 2010-04-26
I have a Dell Latitude D610.  All I had to do to get the wireless to work was plug the laptop into Ethernet on my router (using an Ethernet cable), go to Main menu>System>Administration>Hardware drivers, and click the box to install the B43 drivers.  I believe my computer uses the Broadcom 4318 chip for wireless.

Ralph

---

### Post by epoh on 2010-04-26
Your laptop uses the same wireless adapter as mine. Here are the inf and sys files I used.

ETA: I did do the blacklist, not sure if it was necessary.

---

### Post by anandnz on 2010-04-27
Thank you Epoh,

I got my Wireless working, thank to your drivers and instructions.
I wouldn't have done without it.

My exp: When every thing is configured, the hardware GUI says, cannot find the hardware even after i used Fn F2 to enable wireless, but nothing seems to work.. but after a while magically i saw the list of wireless, disappeared and could get again.  Not really sure what was happening. So for every one else doing same ... patience ..

Now that i have wireless, please can some one suggest what packages and software is important to update.

Thank you Ralph for responding and others.

---

### Post by Ralph L on 2010-05-03
I am still a newbie, although I have been using Ubuntu for a couple of years.  I put together a web site to try to explain to others what I did to make it a useful system for me.  You may have other interests, you might find it helpful.  [http://ubuntulinuxnoviceguide.webs.com/](http://ubuntulinuxnoviceguide.webs.com/)

Ralph

---

