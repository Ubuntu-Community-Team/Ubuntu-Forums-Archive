---
title: "Network Manager doesn't connect automatically"
date: 2009-04-25
forum: General Help
---

### Post by change_mode on 2009-04-25
Using Jaunty. I configured the network manager and checked "CONNECT AUTOMATICALLY". What kind of voodoo magic do I have to apply for it to actually do that? 
I have to click on my connection every time after startup.

I set the NM to 'managed' in the nm-system-settings.conf by the way, to prevent the red icon bug.

---

### Post by dcstar on 2009-04-25
> **change_mode said:**
> Using Jaunty. I configured the network manager and checked "CONNECT AUTOMATICALLY". What kind of voodoo magic do I have to apply for it to actually do that? 
I have to click on my connection every time after startup.

I set the NM to 'managed' in the nm-system-settings.conf by the way, to prevent the red icon bug.

What bug?, changing things from default can cause more problems than they might fix.

---

### Post by change_mode on 2009-04-25
> **dcstar said:**
> What bug?, changing things from default can cause more problems than they might fix.

The bug where the network manager shows a red cross icon and says no connection found, although it's connected. 
Letting Network Manager manage the devices in /etc/network/interfaces obviously fixes that (it's the default by the way, just not in Ubuntu).

Doesn't matter what I do, I run into one of these two bugs either way. Need to fix one of them...

---

### Post by change_mode on 2009-04-27
daily bump

---

### Post by sv1cdn on 2009-04-27
I removed Network manager and working with WiCD [http://wicd.sourceforge.net](http://wicd.sourceforge.net) so far so good!

---

### Post by change_mode on 2009-04-29
In case anyone else has this problem, I fixed it by completely removing the eth0 configuration from /etc/network/interfaces.

---

