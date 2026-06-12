---
title: "mdadm RAID. *** glibc detected ***"
date: 2006-07-27
forum: Desktop Environments
---

### Post by Xenolard on 2006-07-27
Hey guys.

Firstly, sorry if i've posted this in the wrong place. Please move it if it is the case, mods.

I've just bought a new machine to setup as a server machine. It's been running perfectly on old hardware for ages. Anyway, currently the specs are:

3100+
1GB DDR RAM
4x320GB WD HDD SATA
1x40GB System Drive
1x300GB OLD store drive

One of the 320's was not running right so I had a new one delivered today, I popped the new one in and decided that i'd reinstall the os as I'd let someone else on the box and they'd installed a load of crap (x, gnome, vnc, arrgh).

So I waited for the system to boot so that I could get my ppp configs and what-have-you off, no dice. 

```
*** glibc detected *** double free or corruption (!prev) 0x0000000000539830 ***
```

Is what it displayed. Huh, odd, I think. So I pop in a 5.10 live disc and watch it boot up, same. Whaa?

So I flatten the system disk and install a fresh install, nope, same again.

So by now I'm getting a little annoyed, so I set the BIOS to fail-safe setting. Nope. Rats.

So I disabled the onboard SATA controller (It's worth mentioning at this point that there's 2 of the 4 320's on a SATA controller card and 2 being fed from the onboard controller). DING up it comes, only half the drives, obviously.

So I get the net running and apt-get update/upgrade and it updates a few things. Reboot after turning the stuff back on in the bios and the same messages comes up.

I'm stuck, what can I try? I just want my RAID to work :(.

I've also tried wiping all the drives so they're just blank partitions, no dice.

Yelp!

---

### Post by Xenolard on 2006-07-28
Bump! :(

---

### Post by HAARP on 2006-07-28
If you're using onboard SATA, I'm absolutely sure it's a Software RAID which shows as a Hardware-RAID because of Windows drivers. Use dmraid to get it to work on Linux, there should be tutorials around this forums/the wiki/google

---

### Post by hotani on 2006-07-28
I set up my RAID (2x250GB SATA) using the 'alternate' install disk which provided a clunky unintuitive gui interface for the process. I'm not ragging on the install disk itself, it's mostly straight-forward, but setting up RAID is a delicate and finicky process in there.

I used [this tutorial](http://users.piuha.net/martti/comp/ubuntu/raid.html) to get me through it.

It may be worth mentioning that during my install process and trying to get RAID up and running one of my PATA 120s failed causing all kinds of error messages, although not the one you described. As soon as i removed that drive, everything came up fine. That is when I decided to go with the 250GB SATA RAID setup rather than the older 120s.

---

### Post by denali443 on 2006-08-08
I had something similar with software raid with the server version of dapper drake, on a known to be solid dual p2 450, w/ 3 36 scsi disks...

If one of the raid filesystems was hosed, then the box would hang on boot with a double free detected message, if I however hit ctrl-s to pause the boot, while the raid stuff tried to bring the funky raid partition back up.  I could then boot normally after the raid was done doing it's thing (giving up on the partition in this case)....

Looks like the server kernel needs some work...

---

