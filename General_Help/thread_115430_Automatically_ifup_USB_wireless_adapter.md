---
title: "Automatically ifup USB wireless adapter?"
date: 2006-01-10
forum: General Help
---

### Post by fubarbundy on 2006-01-10
I have a Belkin F5D7050 working (for the moment anyway) through ndiswrapper, but I have to manually sudo ifup wlan0 whenever I unplug and replug it, and also after I boot up for the first time.

What's the best way to automate this?

Also, slightly OT, I don't have the driver CD for the adapter any more, but for anyone reading this, I found bknusb.inf and prismaxp.sys at driverpacks.net :D

---

### Post by FizDev on 2006-01-10
When you installed it, did you do this after installing it?
> ndiswrapper -m

If not do it, it will load it automatically at the startup.

When you edited the interfaces (/etc/network/interfaces) did you mark "wlan0" or "auto wlan0" to configure your wireless network interfaces?

---

### Post by lindejos on 2006-01-11
Same question but with Madwifi.  Whenever I restart my pc I have to reinstall the madwifi utility, re-create the ath0 device that the card runs on, and recconect to my router.  

It's kind of a pain in the butt because...

1. I have to go in and remove the madwifi directory.
2. I have to un-tar it again
3. I have to make it again
4. I have to make install it again
5. then I must: 
    modprobe ath-pci
6. then I must: 
    wlanconfig ath0 create wlandev wifi0 wlanmode sta
7. then I must: 
    modprobe wlan_scan_sta
8. then I must: 
    ifconfig ath0 up
9: then I have to check that it worked by scanning for available networks:
    iwlist ath0 scan
10: then I have to configure the essid and the key:
    iwconfig ath0 essid "network essid"
    iwconfig ath0 key "network WEP key"
11: then I have to run the dhclient:
    dhclient ath0
12: usually I ping bbc.co.uk after that to make sure it worked.

So as anyone might be able to see, this is kind of a pain to do whenever I restart.  The curious part is why I have to remove the madwifi directory and re-make it.

Any ideas would be appreciated.

---

### Post by fubarbundy on 2006-01-11
[QUOTE=FizDev]When you installed it, did you do this after installing it?


If not do it, it will load it automatically at the startup.

When you edited the interfaces (/etc/network/interfaces) did you mark "wlan0" or "auto wlan0" to configure your wireless network interfaces?[/QUOTE]


Did that.. I just tested, and actually the module loads and the interface comes up on boot, but not when hotplugged (unplug/replug usb adapter) . My /etc/network/interfaces is like this:

auto lo
iface lo inet loopback

mapping hotplug
               script grep
               map eth0

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid [my network's essid]
auto wlan0

---

### Post by marco51 on 2006-01-16
I am a new memeber and brand new to ubuntu  I use the same USB adapter and it is not getting discovered.  Can you suggest how I can start the system to scan and discover this USB device?
thank you

---

