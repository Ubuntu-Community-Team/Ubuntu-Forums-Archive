---
title: "Is anyone else having this problem?"
date: 2008-11-28
forum: Desktop Environments
---

### Post by mikerobinson on 2008-11-28
I have a 2 Mb connection and everything works fine except for some reason thehungersite.com loads painfully slow (under 1Kb/sec). [This page]("http://shop.thehungersite.com/store/category.do?siteId=220&categoryId=2572&origin=34451") took 2 minutes to load completely. I've tried it in both KDE and Gnome. When I try it with a Windows computer on the same network it loads fine. I tried it in VirtualBox and Firefox with wine and it loads slowly too.  I do not have any firewalls installed on the computer and no other site has this effect. Can anyone else verify this or am I just going nuts?

---

### Post by inobe on 2008-11-28
looks like spam no matter how innocent the post

---

### Post by mikerobinson on 2008-11-28
> **inobe said:**
> looks like spam no matter how innocent the post

Sorry about that. I don't know how to word it any other way.

---

### Post by nikgare on 2008-11-29
I think you're going nuts ;-)
It loaded in under a second here!

---

### Post by lelmo85 on 2008-11-29
Mike: If you are serious and this is not spam - us wizards (ha!) need more info. What distro? When did you last update? Both FC9 and Ubuntu 8.10 have made major upgrades recently which affect download speeds.

2:50 PM Took about 15 seconds to download the page from the URL (not copying your reference)

---

### Post by Sorivenul on 2008-11-29
I, for one, tend to think this isn't spam, necessarily.  
Running Intrepid, upgraded yesterday from Hardy, and the page took roughly two minutes for me to load as well, on both hard connection and wireless.

> sorivenul@ubuntu:/proc$ cat /proc/version
Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008

Ping results:
> --- shop.thehungersite.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4014ms
> --- bbc.co.uk ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4013ms
rtt min/avg/max/mdev = 118.104/118.925/119.981/0.668 ms

---

### Post by kline on 2009-03-05
I suppose it's good to know that my configuration running very slowly isn't the only one.  I have firefox plus the flash working on my FBSD 7.1 desktop too.  Given the exact same sites--say 4 or 5 of them--here on my Ubuntu desktop all sites don't finish loading for 8 to 10 minutes...  

I've got 8.04, a barebones box with around 200G drive, 1G memory, 2.8GHz AMD uproc.  Sometimes I have miro going in the background; if I do, firefox is that much slower.  I have DSL;
1.5 downlink, 864 up.  The websites I leave up/open are Not spewing/streaming forth data.

To the wizards:  I always run xload and have noticed that every so often, the load goes to around 1.00 and hangs there for several minutes.  "top" says that firefox is eating 98% of CPU.

AH: I was logged onto my.yahoo.com.  When I killed that, my load  dived from 1.06 to 0.02.  Anybody have ideas what's going on?  Could yahoo (or others) be trying to read in an infinite loop, thinking that my desktop is DOS/Doze?? 

very strange... .

---

### Post by jnewl on 2009-03-05
The site loaded fine for me with Intrepid/Firefox. 

And you'll be delighted to know I did not buy a pair of genuine Peruvian sheepskin slippers.

---

