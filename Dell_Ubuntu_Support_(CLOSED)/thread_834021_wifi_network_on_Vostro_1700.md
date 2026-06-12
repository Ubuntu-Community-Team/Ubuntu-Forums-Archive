---
title: "wifi network on Vostro 1700"
date: 2008-06-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by catonano on 2008-06-19
Hello people,

I installed Hardy Heron fresh on a Vostro 1700.

The wireless network does not go. I'm new at this, please help me. Is there anything I should know ? I see many threads about wireless network on Vostros, but no one about the 1700.

Shall I post any output of any command, such as lspci or anyone else ?

Shall I post any log ?

Please, help me

Thanks
Adriano

---

### Post by StefAndrew on 2008-06-19
Do you know what kind of wireless adapter is in your laptop?  My 1500 has the dell branded adapter which is a broadcom 1390 I believe, maybe a 1490.  What you probably need to try is to plug direcly into the network with a cable.  Then go to System menu, then Administration, then Hardware Drivers.  There should be a selection to enable restricted drivers for your wireless card.  This will start the installation for you, then you will need to check the box to fetch the firmware and install automatically.  Once that is complete, you may need to restart, but then you should be able to use the Network Manager icon in the top right near the clock to either see the networks around you or to setup your connection manually.

Let me know if that works for you.

---

### Post by catonano on 2008-06-20
> **StefAndrew said:**
> What you probably need to try is to plug direcly into the network with a cable.  Then go to System menu, then Administration, then Hardware Drivers.  There should be a selection to enable restricted drivers for your wireless card.  This will start the installation for you, then you will need to check the box to fetch the firmware and install automatically.  Once that is complete, you may need to restart, but then you should be able to use the Network Manager icon in the top right near the clock to either see the networks around you or to setup your connection manually.

Let me know if that works for you.

Yes, that worked. Thanks !

---

### Post by StefAndrew on 2008-06-20
Awesome.  Let me know if you notice that the wifi times out or disconnects.  I'm going to be trying out the older driver for broadcom because this one seems to have issues staying connected while I'm installing/downloading packages and times out.  So I'm working on that and will let you know how it works out.

Hopefully this driver works fine for you though.  Glad to hear it worked.

---

### Post by catonano on 2008-06-21
stef,

> **StefAndrew said:**
> Awesome.  Let me know if you notice that the wifi times out or disconnects.  I'm going to be trying out the older driver for broadcom because this one seems to have issues staying connected while I'm installing/downloading packages and times out.  So I'm working on that and will let you know how it works out.

Hopefully this driver works fine for you though.  Glad to hear it worked.


Yes, you're very kind. But luckily I'm experiencing no disconnections or timeouts, so far.

Wish you the best with your driver, though !

Thanks for your help !
Bye
Adriano

---

