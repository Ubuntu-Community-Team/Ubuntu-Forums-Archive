---
title: "can connect to irc,ftp but can't browse!!"
date: 2006-08-29
forum: Desktop Environments
---

### Post by grizzly on 2006-08-29
**The problem**
Irc, ncftp, ftp-uploading all just work absolutely fine. However browsing (http) doesn't work!! Actually it works very randomaly, sometimes suddenly some page will open or sometimes a page will load a after a whole 2 minutes.
Again I doubt if its speed problem, coz irc/ftp work dead fine.
Problem common with all browsers including lynx.


**[The config**

Cable or lan based internet, static ip addrees, I can ping the gateway, dns servers all right. No personal router/firewall installed, using kubuntu.
Windows is working so no problem  with hardware

**How it began**

I had to change the ip address a few times.
The steps I took for this :
Edited /etc/network/interfaces
ifconfig eth0 down
ifconfig eth0 up
/etc/..networking restart
This would switch the ipaddress successfully

Also I played a bit under network settings/profiles in kcontrol


Help please, me is very confused here

**Question**

Is it possible to delete/uninstall clear all settigns related to my network card? MAyet that will solve the problem

THanks

---

### Post by sidd-tx on 2006-09-19
I have a similar problem with my Kubuntu 6.06 laptop. Networking was fine for a while, but after updating a couple of rounds ago (I don't recall the updates, or even the exact timing for that matter, but it SEEMS to be around that time) my network is intermittent. 

Any applications that utilizes the network more often spits out error messages pointing to connection problems. If I try a few more times or refresh my browser a couple of times, I eventually get the connection. 

Anyone else seen this after updating Kubuntu Dapper around 2 to 3 weeks ago?

Thanks in advance.
Sidd

---

### Post by grizzly on 2006-09-29
well my problem got solved.. I just removed the network card and put it another PCI slot and it worked. 

However I haveever got still more network problems with kubuntu :( , dns keeps reseting/can't download from IRC, other downloads keep getting stuck, I have to keep hitting stop and resume to complete any download

---

