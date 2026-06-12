---
title: "pilot-xfer wont link after dapper install"
date: 2006-06-19
forum: Desktop Environments
---

### Post by gimmee on 2006-06-19
Hi all

Generally have had not too much hassle upgrading to dapper. Some broken links and dialup modem problems but all and all pretty happy.

I have a tungsten e2 that I would sync usb under pilot-xfer and jpilot. Now that I have upgraded to dapper i can not get it to sync at all.

Before when i press hotsync it would create ttyUSB0 and ttyUSB1 and a link /dev/pilot. Running pilot-xfer -p /dev/pilot -s /home/gimmee/temp would link no worries and sync, backup install etc. Same with jpilot.

Now with dapper i already have ttyUSB0, ttyUSB1, ttyUSB2, ttyUSB3.

When i press hotsync it creates ttyUSB4 and ttyUSB5 and a link to /dev/pilot to the ttyUSB5

Running pilot-xfer -p /dev/pilot -s /home/gimmee/temp has it sitting there 'listening for incoming connection on /dev/pilot' but nothing happens.

I also tried pilot-xfer -p /dev/ttyUSB5 and pilot-xfer -p /dev/ttyUSB4 but same thing.

Look forward to any help you can give on getting me synced again.

Cheers

Gimmee

---

### Post by tristan on 2006-06-19
I've also noticed that there are some problems with the pilot-xfer etc with my USB Palm m130. Basically, you get one shot at syncing, and then it stops working until the computer is rebooted. Some kind of USB issue. I'm not in front of my linux box, so I can't post the dmesg output. 

So, you can use your Palm, but only once!

---

### Post by pito on 2006-06-20
Same problems here I had a contact with my Palm 3 times and no more. Worked fine in Breezee Ubuntu 5.10.

/piotr

---

### Post by dolphin_1 on 2006-10-24
Wondering if any of you guys have this figured out by now..  I am having similar problems, although I can safely say I have never been able to sync up, not even once.  It tries and hangs there.  Tried K-pilot and J-pilot.  Any ideas?

---

