---
title: "No Internet after short unplugging"
date: 2005-09-06
forum: Desktop Environments
---

### Post by dqsis on 2005-09-06
Hello Ubuntu friends!

This is my question:

Whenever I want to move my laptop (let's say between offices), I have to shortly unplug my internet cable.

But (there is always a but) when I replug it, I get no internet and I have to restart my computer  ](*,) 

Do you know how I can overcome this problem?

In addition, whenever I start my computer without the internet cable (but plug it in later) I get no internet...

I think these 2 problems are related. 

Any ideas?
  
Thank you all in advance!

---

### Post by cwaldbieser on 2005-09-06
[QUOTE=dqsis]Hello Ubuntu friends!

This is my question:

Whenever I want to move my laptop (let's say between offices), I have to shortly unplug my internet cable.

But (there is always a but) when I replug it, I get no internet and I have to restart my computer  ](*,) 

Do you know how I can overcome this problem?

In addition, whenever I start my computer without the internet cable (but plug it in later) I get no internet...

I think these 2 problems are related. 

Any ideas?
  
Thank you all in advance![/QUOTE]

Do you connect to your network with DHCP or do you have a static IP address?  You should be able to go into the network GUI and turn off the interface and turn it back on.  If that doesn't work, just run an "ifconfig eth0 ip-address" from the terminal for a static IP address, or "dhclient" for a dynamic one.

Also, it might be useful to turn the interface off before unplugging so it gives up the lease on a dynamic IP address.

---

