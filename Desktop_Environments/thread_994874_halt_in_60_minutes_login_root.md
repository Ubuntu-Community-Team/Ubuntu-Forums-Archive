---
title: "halt in 60 minutes login root???"
date: 2008-11-27
forum: Desktop Environments
---

### Post by ramaswamyps on 2008-11-27
my system was halted when i had put in the synaptic to update last week and when i came back i saw ir was shut down.
this happened 2 3 times again if i work or it idles.
today i saw screen flashing warning for a second or so. root login will be halted in 60 minutes.
i tried to get the message again with no luck.

any idea which file is controlling this time limit.?
i know root login is not good for regular use of system. i need to do this to write in other partitions in X file browser.

any pointer to the file to edit it to 3hrs will help me.

i use kde-4.1.2 normally.
usually gnome only gives a warning root login is not adviced and to be careful.

i hope gnome only must have this time control?

any idea?

---

### Post by Ric_ on 2008-11-27
I had this but on gnome. I was running intrepid.

It seems to have cleared up after I installed the proprietary ATI graphics driver. Not sure what graphics card you have but that might be a good pointer.

To install you can go to system > administration > device drivers

---

### Post by ramaswamyps on 2008-11-27
i have intel driver installed.
nope this cannot be video problem.
it happens in my desktop which is 845 intel mother board with intel video driver
and in my laptop toshiba tecra 9000 which uses savage S3 driver.
there must be a timer keeping track of this root login.
though i have no such problem in gentoo gnome or kde
this can be some limitation by ubuntu init scripts.

right now i am running ubuntu-8.10 distro upgraded from 8.04

please say if you had the same problem and it went away by updating driver?

---

### Post by Ric_ on 2008-11-27
The problem only happened in a fresh install of 8.10 and didn't happen in 8.04. The upgrade fromt he standard drivers to the ATI ones fixed the problem.

---

