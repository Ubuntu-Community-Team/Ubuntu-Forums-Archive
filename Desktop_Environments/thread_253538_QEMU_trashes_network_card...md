---
title: "QEMU trashes network card..?"
date: 2006-09-08
forum: Desktop Environments
---

### Post by Onos on 2006-09-08
So I get this idea in my thick skull to try running Windows XP on QEMU per this blogger's post:

[http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html](http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html)

I mean, I am no fan of Bill... but when it comes to games - he is pretty much the only game in town in terms of how well supported most video games are (and that game developers cater to M$'s market saturation).

Long story short, I install QEMU without any major mishaps, and start the "virtual install" of Win XP.

About three hours later and not much change in the countdown of The QEMU window showed that "Setup will complete in approximately: 39 Minutes". along with all the M$ marketing hype, I decide to go to bed.

(at this point, I still have working internet access)


....zZzZzZzZ....

I wake up to find my poor Ubuntu computer frozen - locked up - non-responsive: a doorknob could not have possibly been more inanimate than this box.

The QEMU window showed that "Setup will complete in approximately: 7 Minutes".



I shrug it off as a bit of wierdness or whatever: all this stuff was getting sent to a folder on my hdb drive so I could dink around with Kuma\War or Empire at War; if it got hosed up along the way, no biggie.


Things never are that easy though.

I did a cold, hard reboot:
(CRTL ALT F2)  

```
sudo reboot
```

... and found myself back in all that chocolately goodness that is Ubuntu 6.06 LTs... without a functioning internet connection.


:-k 


Acting upon the assumption that I am a reasonably intelligent cat, I started up my laptop which could see the internet (ruling out a router or modem problem) and came to these forums in search of HOWTOs and other goodies to fix this issue.

First, I ruled out the easier stuff (modem? all lites flashing as they should. Router? The wife's Mac, my Win XP craptop and the Vonage phone all workie. I even swapped lines around the various router ports, and they all work.

I swapped the cable from the vonage phone with the Ubuntu box - phone still worked. Chocolately Ubuntu goodness however, continued to elude me. 


The next step was to delve into the somewhat scary guts of tools like the networking GUI (Systems > Administration > Networking) which was quite useless (according to it, the LINKSYS Etherfast 10/100 LAN card, model LNE100TX was active).

Resorting to the CLI... I dug up what tools should work:

netstat -nr
(turned up exactly nothing. Blank line.)

sudo ifup
eth0 is already configured.

ifconfig
(returned something I was not able to copy her, but looked normal)

ping localhost and ping 127.0.0.1
(worked normally)

arp -a 
(did nothing)



... many hours of frustration.

I reinstalled Ubuntu twice, then even reformatted the whole mess and installed XP (with SP2) ... still no joy.

Now normally things work "out of the box" in WIndows; but not surprisingly, the network card/PCI bus/mobo ...??? issue repeated itself here.

It is quite the gremlin: Device Manager turns up no flags or anything to indicate that there is something fundamentally wrong with my network configuration.

Short of any solution to this I am probably looking at this computer as an addition to my garbage can collection. 

I might be able to load a few single player games on it... but it is now fairly useless for much of anything.

Lesson learned: Stick with dual-booting and don't screw with emulators?

](*,)

---

### Post by Onos on 2006-09-08
QEMU Drama, Part the Second.


Turns out that as I was planning to haul the old Compaq Presario out around back to vent my rage in a hail of 9mm projectiles upon it...

my dear wife alerts me to a (surprisingly simple) fix documented here:

[http://www.annoyances.org/exec/forum/winxp/1130146387?s](http://www.annoyances.org/exec/forum/winxp/1130146387?s)

The gist of it is connecting directly to the cable modem and then back to the router;

Resetting the network (not sure how to do this in Ubuntu, but in Windows it involved cycling through ipconfig -all and ipconfigc -release and -renew until I finally picked up a DHCP IP issued from the router.

I think I shall now contemplate the weighty issue of installing the dual boot love once again... although this time I will probably to lazy to go about making it look like a MacBuntu.

After all, we Linux users enjoy nothing more than a good OS to tinker with. :rolleyes:

---

