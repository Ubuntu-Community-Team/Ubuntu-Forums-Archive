---
title: "intel 3945abg driver update"
date: 2008-02-28
forum: Dell  Ubuntu Support
---

### Post by thibz21 on 2008-02-28
Hi,

i'm new to linux. i am using ubuntu 7 in my dell inspiron 1420 with wireless card 3945abg. but my wireless driver is 2200 by default. i want to change it to 3945abg as that's wat mine is and the driver is available for linux.

i downloaded the driver, read the readme and found that ieee80211 have to be installed. so i download ieee80211 1.2.18 which is the latest. when installing it there is one part where the command like is this:

DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p" \/etc/hotplug/firmware.agent)

but the thing is there is not such file firmware.agent. so i keep searching and i see forums ppl talking about the linux kernel. so i even download the latest kernel 2.6.24.3. but there was a problem. i don't know how to install it. even when i type "make" it giving so much error. i have been cracking my head for 3 days. i have been to all the forum and now i'm here at last resort. plz help.

thanks,
thibz

---

### Post by natehall on 2008-02-28
[Dell has a Ubuntu version made for the 1420]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10"). It has the 3945 driver built in.  Just save what data you want and go with a fresh install.

---

### Post by pormogo on 2008-02-28
The 1420n uses the same chip as my m1330n and I haven't had any luck getting the ipw3945 or iwl3945 modules to work after coming back from a suspend. Coming out of hibernate the ipw3945 module works about 60% of the time or so (or else I have to unload and reload the module and then bring it into suspend and out of suspend :() So if your module is working i might actually recommend leaving it as is. Just my personal experiance.

---

### Post by thibz21 on 2008-02-28
because my intention is to learn to crack WEP... so if i'm going to do that... i need to make my 3945 to monitor mode at least... it might not need to inject... just monitor the IVs i will be able to crack.. i want to try that... i tried using wifislax v3, backtrack v2 and v3... all not working.. only ubuntu at least can detect the wireless... other don't have drivers also.. looking forward for some help... thank for the replies guys...

---

### Post by thibz21 on 2008-02-28
> **natehall said:**
> [Dell has a Ubuntu version made for the 1420]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10"). It has the 3945 driver built in.  Just save what data you want and go with a fresh install.

thanks for the idea dude... hope it works... but again.. it just mentioned that it solve the graphic card problem... would it solve the wireless problem?

---

### Post by fragos on 2008-02-28
My 1420n works great.  I've used both the pwl and iwl WiFi drivers.  The iwl might be better but it's hard to judge.  iwl doesn't support the WiFi led but I don't consider it much of a detriment.  When signals are ocassionaly dropped or difficult to connect to they are always lower powered and I can't be sure if other factors such as router bandwidth come into play.  With my home wireless i've high signal strength and connections are allways there.

---

