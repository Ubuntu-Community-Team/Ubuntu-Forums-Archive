---
title: "wireless problems"
date: 2006-01-03
forum: General Help
---

### Post by humanchimp on 2006-01-03
Hi everyone.
First of all i'm very new to this whole linux thing, so bear with me please. I finally got to install kubuntu on an old hard drive i found gathering dust, and it seems to work great. The only problem is that it hasn't (as far as i know) detected the netgear wg311t adaptor. I read somewhere on these forums that it should have done, is this the case?

This adaptor ran fine under windows which i have on my other harddrive - so i don't think its a problem with the adaptor. It connects to a netgear router, and the network has WEP.

To make matters worse, When i go to system settings -> network settings, all i get is a "Please wait while detecting your current platform" message.

Anyway, i've been reading there are two solutions. First of all, theres madwifi, and then theres ndiswrapper. I tried downloading madwifi for kubuntu on this computer (win xp) then copying it onto a cd and loading it up on kubuntu, but when i click on it on kubuntu, ark loads up and gives me the error:

"The utility ar is not a PATH.

Please install it or contact your system administrator"

Where am i going wrong?

---

### Post by xtacocorex on 2006-01-03
According to the Ubuntu Document Storage Facility, the card is natively supported in Breezy: [http://doc.gwos.org/index.php/NetgearWireless](http://doc.gwos.org/index.php/NetgearWireless)

I think madwifi is already installed by default.

Here is more info: [http://www.ubuntuforums.org/showthread.php?t=110106](http://www.ubuntuforums.org/showthread.php?t=110106)

---

### Post by humanchimp on 2006-01-03
thanks for the reply

I have a problem though, when i get to step 2, and it says type: "sudo apt-get install sharutils" in the console, - nothing happens :( it just goes onto the next line.

---

### Post by humanchimp on 2006-01-03
ok, i have just restarted my computer, and now when i follow the instructions i get the following:

ME: sudo apt-get install sharutils
###################################
Reading package lists... Done
Building Dependency Tree... Done
Package sharutils is not available, but is referred to by another package
This may mean that the package is missing, has been obsoleted, or is only available from another source

E: package sharutils has no installation candidate
###################################

ME: sudo dpkg -i madwifi-source_20041023-1_all.deb
###################################
(Reading database ... 57915 files and directories currently installed.)
Preparing to replace madwifi-source  1:20041023-1 using (madwifi-source_20041023-1_all.deb) ...
Unpacking replacement madwifi-source ...
dpkg: dependency problems prevent confguration of madwifi-source:
 madwifi-source depends on make; however:
 Package make is not installed

 madwifi-source depends on debhelper (>> 3.0.0) however:
 Package debhelper is not installed

 madwifi-source depends on gcc l c-compiler; however:
 Package gcc is not installed
 Package c-compiler is not installed

 madwifi-source depends on sharutils; however:
 Package sharutils is not installed

error processing madwifi-source (--install):
 dependency problems - leaving unconfigured
Errors were encountered when processing:
 madwifi-source
#####################################

does anyone know whats going on?

---

### Post by xtacocorex on 2006-01-03
I'm assuming this is a fresh install, the sources.list for apt need to be updated.

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by humanchimp on 2006-01-03
im assuming that i need to be connected to the internet to do that, but thats the whole point, because im not connected to the wireless, im not connected to the internet either

---

### Post by xtacocorex on 2006-01-03
I downloaded sharutils for you: [http://www.public.iastate.edu/~bobw/sharutils_1:4.2.1-13_i386.deb](http://www.public.iastate.edu/~bobw/sharutils_1:4.2.1-13_i386.deb)

Hope that works for you.

---

### Post by taseal on 2006-01-03
[QUOTE=humanchimp]im assuming that i need to be connected to the internet to do that, but thats the whole point, because im not connected to the wireless, im not connected to the internet either[/QUOTE]

no plugin ethernet port?

---

### Post by humanchimp on 2006-01-03
xtacocorex, thanks ill try that now

taseal, no - its a very old computer :(

---

### Post by humanchimp on 2006-01-03
well after messing around with it i think ive got it installed, theres only a few problems.

Firstly when typing: modprobe wlan_scan_sta
i get: Module wlan_scan_sta not found

I also get:
wlanconfig: command not found

Any help greatly appreciated

---

