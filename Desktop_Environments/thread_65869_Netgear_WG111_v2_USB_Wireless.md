---
title: "Netgear WG111 v2 USB Wireless"
date: 2005-09-15
forum: Desktop Environments
---

### Post by ticklu2deth on 2005-09-15
Has anyone had any success setting this device up in Kubuntu? I have searched here and found a handful of topics and some on the web (denoting mixed results). All references I could find were vague and lacked enough detail for me (I'm a total noob and need extreme detail). If someone knows how to set this up, could you provide step by step, hand holding instructions? I know nothing about networking or wireless in Kubuntu/Linux.  

Any help would be appreciated. I think this is the first question I've had to ask on the forum; Kubuntu works so well "out of the box", I haven't had to really do anything since my install.  

Thanks in advance.

---

### Post by ticklu2deth on 2005-09-20
"bump" Anyone?

---

### Post by snowjunkie on 2005-09-20
Simply set the netgear router up as per netgear's instructions.  Browse to your router using 192.168.0.1 and enter your username and password.  The default will be admin/password I believe.  You should change this as soon as you can.

Enter your adsl connection details etc.  At the minute, kubuntu only supports WEP encryption for wireless.  So, configure the WEP details on your router and make a note of the encryption key (Key 1 HEX value).

Then using the wifi manager in kubuntu and scan for your network.  Use the key you generated in your router settings.  That should be all there is to it, providing kubuntu has recognised your wireless card, etc.

---

### Post by ticklu2deth on 2005-09-22
[QUOTE=snowjunkie]Simply set the netgear router up as per netgear's instructions.  Browse to your router using 192.168.0.1 and enter your username and password.  The default will be admin/password I believe.  You should change this as soon as you can.

Enter your adsl connection details etc.  At the minute, kubuntu only supports WEP encryption for wireless.  So, configure the WEP details on your router and make a note of the encryption key (Key 1 HEX value).

Then using the wifi manager in kubuntu and scan for your network.  Use the key you generated in your router settings.  That should be all there is to it, providing kubuntu has recognised your wireless card, etc.[/QUOTE]
 Hi, thanks for the reply! The WG111 is not a router (I have a Linksys router and it was setup long ago). The WG111 is a USB Wireless Adapter ( should have specified). I have worked on this all week and for the most part I have managed to get it to work thru ndiswrapper. The only problem I have now is that it will not come up on reboot. Each time, I have to issue the commands:

ndiswrapper wlan0 essid (name)
dhclient wlan0

I think this is right, I am at work now and don't have the info handy. Anyway when I do this it works perfectly. I created a script to run these commads so it's not a big deal; just a minor inconvienience. I have tried to setup thru the control center with no success. If anyone knows how I can get the script to run on startup, I could certainly live with that (actually it's ok as it is, but for e easier is always better). Well, I'm still learning, but making progress.

---

### Post by bigdaddydsp on 2005-09-22
I also set this adapter up w/ ndiswrapper although I think we can use the drivers from the ralink website.

Either way, make sure you have an entry in **/etc/modules** for **ndiswrapper**.  I think you might can do 'ndiswrapper -m' to load at boot, but the former will definitely load at boot.

As far as specifying the essid and such, you can have that setup in **/etc/network/interfaces**.  I have a line as '**iface wlan0 inet dhcp**' and put wlan0 in the auto line ('auto lo wlan0' + whatever other ifaces to load).

---

