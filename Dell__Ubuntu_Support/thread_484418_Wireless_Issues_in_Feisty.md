---
title: "Wireless Issues in Feisty"
date: 2007-06-25
forum: Dell  Ubuntu Support
---

### Post by skysong on 2007-06-25
I have a Dell Inspiron 600m, with an Intel PRO/Wireless card. I just recently upgraded to Feisty. I want to connect to my home wireless network.

I have run into several problems:
1. I did not set up the network. The person responsible knows almost nothing about the details of our network.
2. Although network manager can "see" the correct network, I can't connect to it. I have the correct key -- it worked in my Windows boot. 

My question is this: how do I begin to troubleshoot this problem? How can I find out what kind of key I have, how do I figure out how to configure everything? If I need an upgrade for something or another program, is there anyway to get a download and install it via windows that isn't tedious? I have no other way to connect to the internet than through my windows boot.

Any help or ideas appreciated!

Thanks!

---

### Post by ampted on 2007-06-25
can you connect without the cryptation in the wireless router off?

---

### Post by skysong on 2007-06-25
I'm not sure. How do I do that, exactly?

---

### Post by clikc on 2007-06-25
If your looking for you key, you need to log into your Router, and you should be able to see the encrip or disable it.

---

### Post by skysong on 2007-06-25
I have the key. I just need clarification on the following:

> **ampted said:**
> can you connect without the cryptation in the wireless router off?

---

### Post by RedRover1 on 2007-06-25
You need to figure out what brand of router and how to logon it.  If the password was never changed then you can usually find it via google by searching for "router name and password".  For example I have a Westell Router and to log on it I type http:\\dslrouter.  Once you are in you can disable encryption or reset a new password to find out what the problem might be.

---

### Post by ironyCurtain on 2007-06-26
What ampted is asking is if you can connect to the router without any sort of encryption enabled on it.

What kind of encryption does the router use?  If its WEP then the wireless should work without any configuration other than entering the key into Network Manager (in the upper right hand corner).  

If you need to use WPA (either 1 or 2) then you need to do a couple of things.  In a terminal enter this:

```
sudo apt-get install wpasupplicant && sudo echo ENABLED=0 > /etc/default/wpa_supplicant && sudo /etc/init.d/dbus restart
```

Essentially this just enables WPA encryption and restarts some services including Network Manager.  Then click on Network Manager, select your network and enter the wireless password and encryption type.

---

### Post by raptor95368 on 2007-06-26
while i have no issue with fiesty on my xps, i was not able to get it to run on my inspiron.  I did, however, put in a DLink card, with the atheros chipset, and have absolutely no problem connecting to any of several networks, with WEP or WPA encryption.  In fact, that is how I am responding here, so that might also be an option for you as well...

Cheers

---

