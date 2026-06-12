---
title: "Vmware Server - Wireless Networking"
date: 2006-08-01
forum: Desktop Environments
---

### Post by IAmNotPhillip on 2006-08-01
So I currently have Ubuntu 6.06 running on my HP Pavilion ze2000 laptop (alone -- no windo$e) and am loving it. But there are a few progies that I can't get to work via wine that I am hopelessly addicted to...namely Flash.

I have successfully installed vmware server and have a full (and legal) copy of Win XP Home running through it. It works great except for the fact that I can't get my wireless working at all (eth1 802.11g). I have added an ethernet device in the settings menu and have tried every different type of connection (Bridged, Nat, Host-only, etc) but they all give the same error:

"Could not open /dev/vmnet8: No such file or directory. Virtual device Ethernet0 will start disconnected."

Now I can understand the error itself fairly easily seeing that it simply states that the file doesn't exist, but in every howto and manual I've read, I have yet to see anything stating that I need to create something extra.

So I guess my question comes down to this:

Is there a vmware-noob-friendly manual or guide or something similar that could help me get wireless working through my vmXP?

---

### Post by tim- on 2006-08-01
i've just installed vmware and got windows 2003 server up and running.  i noticed when vmware was installing that it attached my eth0 to vmnet0 and my wlan0 to vmnet2 (vmnet1 is reserved for host only networking) so my guess is it try and switch the network to vmnet2 and see if that helps!

---

### Post by IAmNotPhillip on 2006-08-01
I'm afraid all that did was change the "Could not open /dev/vmnet8" message to "Could not open /dev/vmnet2"

I'm considering reinstalling vmware and paying more attention to all the feedback. Maybe I'll get a message similar to what you did.

EDIT: Upon quick inspection of my /dev folder, I don't appear to have any vmnet-anythings. Could it be possible that vmware can't detect my hardware for some reason?

EDIT2: Reinstalling did the trick. Apparently during my first install I said not allow my vm any access to the internet. :P

---

### Post by tim- on 2006-08-06
lol glad you got it sorted!

---

