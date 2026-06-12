---
title: "linksys wmp54g problem"
date: 2006-07-09
forum: Desktop Environments
---

### Post by cmw000 on 2006-07-09
I can't connect to the internet. I'm new to Linux and I'm not sure exactly what's wrong. I might be connected to the network but unable to get the internet or maybe I'm not on the network at all. How do I check?

Also, I've read about a lot of different linksys wmp54g problems and I am unsure of how to fix my problem. I checked my drivers folder on the linksys cd that came with my adapter and it had this file in it: bcmwl5.sys

Any help would be appreciated.

---

### Post by cmw000 on 2006-07-09
^

---

### Post by Camino on 2006-07-09
having the same wlan card and it´s working fine. Can you give the version of wmp54g you are using ?

Mine is V4.1 with Ralink Chipset RT61. This one is supported fine on dapper.

do a lspci in terminal and you should get following output:

0000:00:0b.0 Network controller: RaLink: Unknown device 0301

if you do now a 
> 
lsmod |grep rt61

you should get something like this:
rt61                  223616  1

If this is the case your nearly done.

Now you have to follow the steps in this thread here (copy firmware to folder /etc/Wireless/RT61STA and create the file rt61sta.dat with your specific configuration). You don´t need the compile part here. If you don´t know how to setup the rt61sta.dat you can download the source driver from Ralink and follow the readme included.

[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

To get the Chipset you can have a look here:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

If you are using a older version my guess would be to use ndiswrapper and use the windows drivers wrapped with ndiswrapper

---

### Post by bigken on 2006-07-10
take a look at this it worked for me [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

### Post by AZzKikR on 2006-07-10
The Linksys WMP54G has the RT2500 chipset. I have one installed on my desktop PC and it works like a charm. This howto on the Wiki worked perfectly for me. I had WPA/PSK TKIP authentication so I couldn't configure my network using the Gnome Network Configurator

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

---

### Post by cmw000 on 2006-07-10
Thanks everyone for the links.

I'm trying to use ndiswrapper with the factory driver but I can't install ndiswrapper because I can't run make. (??) I thought make came with the C compiler but I guess not. How can I install make? I don't have a wired internet connection from the computer that needs it. I'm typing this from a friend's computer.

edit: I just remembered about the path. 2 things: how do I discover if make is present on my computer and if it is, how do I add it to my path?

---

