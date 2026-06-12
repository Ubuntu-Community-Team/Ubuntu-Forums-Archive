---
title: "Lots of problems (including cd drive, sudo, and harddrive issues)"
date: 2005-12-02
forum: Desktop Environments
---

### Post by Stevio on 2005-12-02
Long story, hopefully you guys can give me some assistance.

My machine is a SN25 Shuttle, NF4 board I believe. I have a plextor dvd.

Both my harddrive and cd/dvd drive are on the ide bus.

I first started off because i wanted to format a harddrive to apple format, ready to put in a problematic mac we have.

I was advised linux could help me format the drive, great. I got recommended ubuntu live cd. I downloaded it had many issues, most of which I could solve from searching this forum luckily.

The first was the cd would not go through the install session, saying i should check the integrity of the cd.

Eventually I found out that I had to add "-d 1 /dev/hda1" or something, to parameters, For this however i had to enable "live-expert". The second problem was my ATI gpu was causing the graphics display module to fall over, again this could be fixed by manual detection as "vesa"?.

Finally I got into ubuntu, and the first problem was - no harddrives. I couldn't access the "disks" program, - it would just saying "starting disks" and disappear. I resolved this by using WMWARE to boot ubuntu through windows, I no longer had to use live-expert. And everything worked fine.

Now the problem was, I couldn't format the drive still. It said it would format it, but didn't. I guess this is something to do with vmware being interpolation layer to the actually hardware.

So I went back to booting through dos, and basicaly the two problems I get now are;

Sudo command - returns a "gethostbyname()" error < something to do with having no network setup perhaps?

No harddrives found, disks wont launch ut hardware management shows the harddrive connected in the ide sections.

I'm guessing the problem is that with expert I need to help it find the harddrive? But how would I go about this?

Hope that makes sense, and thanks in advance.

Stevo.

---

### Post by aysiu on 2005-12-02
Maybe I'm not understanding your problem exactly, but if you're trying to format the drive, just install GParted on the live CD and use it.

If you want to format in order to install Ubuntu, you don't have to. Pop the installer disc in, and you can format during installation.

---

