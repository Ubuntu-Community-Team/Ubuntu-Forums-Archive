---
title: "more problems with the ASUS A8N-VM"
date: 2006-02-05
forum: Desktop Environments
---

### Post by xraycharlie on 2006-02-05
Starting to wonder if I should have maybe gone with another board.

Got a A8N-VM with and ADM x2, 4 gigs ram.

Wondering if somebody can maybe give me some suggestions on how they got it all to work.

On installing breezy (386) The network card is not recognized. I have the latest NVIDIA drivers but can't install them because I need some of the build-essential, which of course I cannot apt-get because I have no network.

The other problem I noticed is that it is only recognizing 2 of the 4 gigs.  Is this a limitation of the 386 kernel or did I miss something during install?

Thanks

---

### Post by jhbumby on 2006-02-05
If you are running an AMD 64 on this motherboard, which I assume you would have to, why didn't you install Breezy for AMD's 64 bit architecture?  I don't know much, as I am still learning, but this could have something to do with your problems.  I am using it on my work computer, though mine is a Gigabyte motherboard, but AMD 64 works great.  No problems, and I am not even hooked up to the net.  (I did all my installs at home first.)  This could be a direction to go in if noone else gets you an answer-
JohnnyB

---

### Post by xraycharlie on 2006-02-05
Thanks for the reply.

I'm not using the ADM64 version of breezy as I intend to put on GSX server to play with.

The 64 bit version of GSX is experimental and the command line utils do not work .

I've tried putting on the latest dapper (i386) and run into the same problems so I'm guessing support for this chipset won't be included in it either.

Regards

---

### Post by jhbumby on 2006-02-05
It isn't the actual hardware that's faulty is it???  See if a different OS all together works on it.  Not to sound like a prick, but you did check to make sure everything is hooked up correctly as well??  I am just trying to think outside of the box- regards
John

---

### Post by xraycharlie on 2006-02-05
I have XP on a partition and everything is working fine.

If I could at least get the network up then I could grab the latest from nvidia but I can;t seem to.

It does see that there is an eth0. If just fails when grabbing an IP from the dhpc.  I've tried using a static IP with no luck either.

I've also included the 'auto eth0' in interfaces which wasn't there on install.

Any thoughts?

Regards

---

### Post by RAOF on 2006-02-05
What does dmesg have to say about eth0?  Specifically, run "dmesg | grep -i eth0" (from a terminal).  What about after you run ```
sudo ifconfig eth0 down
sudo ifconfig eth0 up

```?

---

### Post by xraycharlie on 2006-02-05
dmesg | grep -i eth0 gives me:

[4294678.120000] eth0: forcedeth.c: subsystem: 01043:816a bound to 0000:00:14.0

the ifconfigs don't say anything

Regards

---

