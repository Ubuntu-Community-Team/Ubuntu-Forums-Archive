---
title: "Strange Wifi problem"
date: 2005-06-21
forum: Desktop Environments
---

### Post by tristian on 2005-06-21
My card is detected and it detects my access point and no IP adress is given to me.

I don't know how to solve this problem thats why I am posting this message. I never had this problem with previous versions of Ubuntu but I decided that I wanted to use Kubuntu. Other than that I like it better than Ubuntu!

---

### Post by aamir on 2005-06-21
post the output of ```
sudo ifconfig
```

---

### Post by tristian on 2005-06-21
Actually I cannot get the machine online. I tried that to see if there was any IP adress assigned to ath0 but no luck.

Do you think I might have to mess around with:
/etc/hosts
/etc/hosts.conf
/etc/hosts.allow
/etc/hosts.deny

If I cannot get it to work I may buy myself a long 20m ethnet cable and get the drill out  :twisted:

---

### Post by aamir on 2005-06-22
okay so your card is recognized, are the lights on? did you use ndiswrapper to get this going or did it get picked up during the install?

---

### Post by tristian on 2005-06-22
OK at the install it asked for the ESSID and I entered it as it would be, no WEP (until I can get it working) and the installer would not detect it. I do not have a ethnet socket enabled on the machine.

Also the lights are on and the accesspoint is detected if I use KDE's Wifi Manager.

I am really stumped on this one. I don't want the computer running Windows if you know what I mean?

I dont have a computer in this building running Windows since its a pain to maintain and I need to use GUI to update, secure and configure it.

Also I have not posed my hardware (links included):
Access Point = Belkin 54g
([http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=201576&pcount=&Product_Id=141071&Section.Section_Path=%2FRoot%2FNetworking%2FWirelessNetworking%2F80211gWi%2E%2E%2Etworking%2F](http://catalog.belkin.com/IWCatProductPage.process?Merchant_Id=&Section_Id=201576&pcount=&Product_Id=141071&Section.Section_Path=%2FRoot%2FNetworking%2FWirelessNetworking%2F80211gWi%2E%2E%2Etworking%2F))
PCI Wifi card = D-Link DWL G510 High Speed card
([http://www.dlink.com/products/?pid=308](http://www.dlink.com/products/?pid=308))

---

### Post by usererror on 2005-06-22
i have not been able to get my wifi card to connect via kwifi manager.  i have now switched entirely to setting it all via command line...

---

### Post by tristian on 2005-06-22
If that worked could you post a workaround?

Thanks in advanced

---

### Post by tristian on 2005-06-22
Well I have decided I cannot be bothed with this problem and I am going to purchase a very long ethnet cable 10m+ that way I will have no bad reception or problems just endless supply of packets.

---

