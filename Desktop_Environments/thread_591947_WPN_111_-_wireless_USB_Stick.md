---
title: "WPN 111 - wireless USB Stick"
date: 2007-10-25
forum: Desktop Environments
---

### Post by UweD on 2007-10-25
Hi,

I am using Ubuntu 7.1 and was wondering if anyone knew what the best way is to bring my WPN 111 USB wireless lan stick from Netgear into action? I already played with ndiswrapper and got it working but not very reliably. It sometimes doesn't start up at all when I boot up my computer. When it starts up all is good and it functions nicely. What about 'madwifi' driver. A) Is that the better choice, and B) what do I need to do to install it?

Thanks for your help,
Uwe

---

### Post by Arno123 on 2007-10-28
Hi Uwe,

i'm also running Ubuntu 7.1 with a WPN111 but i didn't get to work yet.
Please tell me wich driver you use, I always get the message "invalid driver".

---

### Post by dented59 on 2007-10-28
Hey,

I've gotten it to work pretty reliably using ndiswrapper, the ndis-drivers from the CD and wpa_supplicant.

I had to disable network manager though. It would cause my entire system to compltete hang, or when it worked, it only worked for a little while and then I lost my connection and had to reboot.

My current solution is to launch everything by hand. First ndiswrapper, then wpa_supplicant and then dhclient.

Let me know if you need a more detailed description of how I got it going.

/Mike

---

### Post by ECPCLINUX on 2008-03-16
Hello, I'm fairly new at this and I got my Netgear WG111v. 1 to work with Ubuntu 7.10. I'm doing this by memory, not a very good one,lol.  Hence it might not be perfect but hopefully it will give you guys further clues. First,  I installed ndiswrapper. I found it in synaptic (system, administration, synaptic package manager). Then I downloaded the correct drivers from Netgear (remember the version of your adapter matter, v1, v2 etc). You'll find the drivers here: [http://kbserver.netgear.com/products/WG111.asp](http://kbserver.netgear.com/products/WG111.asp)

   NOTE: there is a way to tell your adapter in a Terminal, I just can't remember it. Nevertheless,  if you look up the serial number as per Netgear's site you should be able to figure it out. 

Again note your model number by serial number. Mine was the wg111 v.1, none Tivo.  After I downloaded the drivers from Netgear I just unzipped them (note the location you unzip it to). 

Next I opened  ndiswrapper, as follows: (System, administration, Windows wireless drivers) once opened you can choose install new drivers, and find your .inf file and add it. After thIs all I had to do was to choose the network device from the drop down menu, mine was  (loopback interface Lo). The rest was a matter of setting the my network  password. I did this a while ago, so please forgive me if somehow I forgot  a small detail. Nevertheless, it should at least guide you.  The following link is a person describing (how to) using a terminal and uninstalling previous attempts, which if you have , maybe this would be useful.  [http://www.linuxquestions.org/questions/linux-wireless-networking-41/netgear-wg111v2-ndiswrapper-installation-problems-460124/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/netgear-wg111v2-ndiswrapper-installation-problems-460124/)

Please note that I have not used the above site, did not have to.  Hope this helps at least a little.

---

