---
title: "Cardbus wireless in Kubuntu Breezy - so close but not quite there!"
date: 2005-12-20
forum: Desktop Environments
---

### Post by Switch625 on 2005-12-20
Hi all,

I'm trying to get a Cardbus wireless PCMCIA card working and connected to my home network on the girlfriend's (HP) laptop. The PCMCIA is an RTL8180 model.
I'm using Kubuntu Breezy with kernel 2.6.12-10-i386 and I've installed the deb driver package from [here]("http://ubuntuforums.org/showthread.php?t=95879"). 
I've made sure to add the two lines specified to /etc/network/interfaces, but contrary to the post, the driver doesn't load on bootup &#8211; I have to type 
```
sudo insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/ieee80211_crypt-r8180.ko
sudo insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/ieee80211_crypt_wep-r8180.ko
sudo insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/ieee80211-r8180.ko
sudo insmod /lib/modules/2.6.12-10-386/kernel/net/rtl8180/r8180.ko
```
 manually after each boot.

From the KDE system settings application, I have then configured Internet & Network -> Connections -> Wireless Network with my network details (SSID, WEP key etc) and Internet & Network -> Network Settings with the SSID, WEP Key and default gateway (my router IP) also.

Having done all this the PCMCIA card's TX/RX light starts to flash and the LINK light goes a steady green &#8211; all very  promising, however I can't ping the router (&#8220;Network Is Unreachable&#8221;) and looking at the Router's &#8220;Attached Devices&#8221; list from another PC shows that the laptop has not connected.

There are two major things that stick out as wrong:

[LIST]
[*]on boot-up, when the &#8220;bringing up network interfaces&#8221; phase occurs, the PCMCIA card's lights are not on &#8211; if I could somehow cause the insmod commands to be run before this point I would be happier as I eventually want the thing to connect on boot anyway, and I can't shake the hope that if the card were available at this time all might go smoothly.
[*]once the insmod commands have been issued, despite the PCMCIA card flashing happily away, in Internet & Network -> Network Settings the wlan0 interface is shown as &#8220;Disabled&#8221;. Clicking &#8220;Enable Interface&#8221; causes it to change very briefly to &#8220;Enabled&#8221; before flicking back to &#8220;Disabled&#8221;. No clue is given as to the problem.[/LIST]

Can anybody help me out with this? I've got a feeling I'm pretty close - the flashing lights seem to indicate the drivers are ok and it's now just a configuration issue. 
I'm reasonably new to Linux and especially Ubuntu but any suggestions at all would be appreciated - I can always Google the stuff I don't understand! ;)

edit: dammit, just realised I've posted this in the Hoary forum. Sorry! Should I cross post or will an admin move it for me?

---

### Post by edwardog on 2005-12-20
Instead of inserting the modules manually (which you many also see being done via ```
modprobe
```), you can have them load on boot by putting them in ```
/etc/modules
```

What happens when you type
```

ifconfig wlan0 up
iwlist wlan0 scan

```

---

### Post by Switch625 on 2005-12-21
Thanks for the reply.

I added the modules to my /etc/modules file, it now looks like:
```
lp
mousedev
psmouse
ieee80211_crypt-r8180
ieee80211_crypt_wep
ieee80211-r8180
r8180
```

However the card doesn't start on boot and I still have to use the insmod commands (which I've made into a script - I haven't tried the modprobe method yet, I shall do). Have I put the modules into the file correctly?
I've also noticed that even after running my startwireless script, the lights on the card don't come on until I go into "Connections" and click "Activate". (if I click Activate having just booted with the above in the modules file, I get "interface not found" or somesuch)

Running the commands you suggested yields:
```
ESSID: "FIELDGATE"
Mode: Master
Frequency:2.462 GHz (Channel 11)
Bit Rate: 1 Mb/s
Bit Rate: 2 Mb/s
Bit Rate: 5.5 Mb/s
Bit Rate: 11 Mb/s
Quality=89/100   Signal Level=-57 dBm Noise Level=-256 dBm
Encryption key: on
```

FIELDGATE is, indeed, the SSID of my network - but I don't know whether this has come from what I've typed in to try and get the thing connected.

Any ideas?

---

### Post by Switch625 on 2005-12-21
Just to follow up, running 
```
modprobe r8180
```
results in ```
FATAL: Module r8180 not found.
```
:???:

---

### Post by edwardog on 2005-12-21
After you do the insmod stuff, you can see the modules you're currently using with ```
lsmod
```

The names of the wireless modules that lsmod provide are the names you should be feeding to modprobe.

Is r8180 included in lsmod?  You can check this quickly by doing ```
lsmod | grep r8180
```

Once the modules are loaded (one way or another), it looks like you're connected to your wireless station.

Set your base station to not use encryption (as a test), and post the results of the following:
```

ifconfig wlan0 up
iwlist wlan0 scan
iwconfig essid FIELDGATE
dhclient wlan0 (this might time out if we're unlucky)
ifconfig wlan0

```

You should be root to do all of this (and the modprobe stuff), so you can avoid typing in ```
sudo
``` every time by typing ```
sudo su
``` once, doing stuff as root, and switching back by ```
ctrl-d
```

---

