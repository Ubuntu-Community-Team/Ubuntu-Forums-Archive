---
title: "New to Ubuntu"
date: 2005-12-10
forum: General Help
---

### Post by Ravendark on 2005-12-10
Hi all, 
Yesterday I downloaded Ubuntu 5.10 and tried it on my laptop (FS Amilo A1650 with amd athlon64 3400+).
I am not new to linux, I had been using slackware for quite some time since slack 7.
Some things about ubuntu.
i tried to install the x86_64 version of ubuntu and something was going wrong in the installation. Everytime i tried to install it the system halted at 67% "Installing tcpd...". So since i couldnt' install the 64bit version i tried the 32bit one successfully this time...

Now I am running ubuntu (allthough I am writing now from winblowz cause I only have a wireless internet connection, which I cannot use in linux).
Since i am used in slackware i really like compiling. Though my system now doesnt have some dev packages. For example libpng-dev...

I cant connect to the internet and use the apt-get to download the packages. So can anyone tell me grom where I can download them manually?

Thsnks in advance!

---

### Post by taurus on 2005-12-10
What kind of wireless card do you have?  It's easy to set up your wireless connection than you thought.  I have Linksys WPC54G v2 (pcmcia) and it works just fine with my HP laptop in Ubuntu 5.10!

---

### Post by Ravendark on 2005-12-10
I have a broadcom wireless card which I managed it to work under slackware with ndiswrapper (i could scan for networks etc) but I could never make xsupplicant or wpa_suplicant to work properly and finally connect.
But since i installed ubuntu only yesterday, wireless is not a priority. I just need to compile a kernel (ncurses-dev missing) and some other stuff. But I have no idea where to get the dev packages...

---

### Post by taurus on 2005-12-10
Instead of worrying about compiling a bunch of stuff, I would work on the wireless first and once it works, you can download or install anything else after.  I believe my Linksys WPC54G is a Broadcom and I used ndiswrapper to install a driver from Linksys' site...

---

### Post by ren wins on 2005-12-10
i would just like to point out how annoying i think it is that ubuntu is so reliant on the internet

---

### Post by Quartus on 2005-12-10
[QUOTE=ren wins]i would just like to point out how annoying i think it is that ubuntu is so reliant on the internet[/QUOTE]
Well, what isn't these days.

---

### Post by Ravendark on 2005-12-10
Hi, 
I compiled ndiswrapper, the card works. But....
I have no idea how to connect to the internet. Here's the story:

I am at the university accomodation where every floor has a Cisco wireless access point. The settings are the following (from winblowz "Wireless Network Connection Properties"):

In the association tab:
* Network Authentication: Open
* Data Encyption: WEP
* The key is provided for me automatically

Authentication tab:
* Enable IEEE 802.1x authentication for this network
* EAP type: Protected EAP (PEAP)

PEAP Properties:
* Validate server certificate
* There is a certification checked and
* Select Authentication method: Secured password (EAP-MSCHAP v2)

I followed the HOWTO about broadcom cards ([http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)) but it doesnt say anything about automatically received keys, mschap and so on...

Does anybody have any ideas?:confused: 

Thanks!

---

### Post by Strider420 on 2005-12-11
Or I'm pretty sure [the ones here](http://www.debian.org/distrib/packages) would work since Ubuntu is based on Debian.

---

### Post by Ravendark on 2005-12-11
Sorry Strider420, I didnt get your post...
Which ones would work?

---

