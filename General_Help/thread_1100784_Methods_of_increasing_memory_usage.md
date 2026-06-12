---
title: "Methods of increasing memory usage"
date: 2009-03-19
forum: General Help
---

### Post by cros13 on 2009-03-19
I have 12GB of RAM in my system. At the moment apart from running
VMs I'm using between 300Mb and a gigabyte of RAM.
I'd like to know if there is anything else I can do to use my
memory more effectively for desktop use.
I'm running off an SSD so I'd also like to minimize writes to disk.

What I've done so far:

set vm.swappiness=0
Compiled my kernel with PAE (I use x86 for better software compatibility)
mounted /tmp as shmfs
moved the firefox cache to /tmp
installed preload

Anyone have any other ideas?

---

### Post by Locutus_of_Borg on 2009-03-19
you can load your entire firefox profile to tmpfs
speeds up FF's responsiveness quite a lot

you just need a script to periodically make a .tar of your profile so you dont lose any changes you make to it while it is in ram

here's mine
```

#!/bin/bash
if test -f /home/null/.mozilla/firefox/om6jiyxr.default/.unpacked
then
cd /home/null/.mozilla/firefox && tar -cpf packed.tmp.tar om6jiyxr.default && mv packed.tar packed.tar.old && mv packed.tmp.tar packed.tar
else
cd /home/null/.mozilla/firefox && tar -xpf packed.tar && touch om6jiyxr.default/.unpacked
fi 

```

i run that at startup, and then have a cron job to run it again every five minutes

just be sure to first run, before you start using this. (only need to do this part once)

cd .mozilla/firefox
tar cpf packed.tar om6jiyxr.default

then the above script should work
change to your profile of course

also in fstab i have

firefox /home/null/.mozilla/firefox/om6jiyxr.default tmpfs size=128M,user,exec,uid=1000,gid=10 0 0


i would think you could do the same for other directories... /var/run perhaps

or hell, write a script to load your entire file system into tmpfs

worth playing around with at least

---

### Post by philinux on 2009-03-19
> **cros13 said:**
> I have 12GB of RAM in my system. At the moment apart from running
VMs I'm using between 300Mb and a gigabyte of RAM.
I'd like to know if there is anything else I can do to use my
memory more effectively for desktop use.
I'm running off an SSD so I'd also like to minimize writes to disk.

What I've done so far:

set vm.swappiness=0
Compiled my kernel with PAE (I use x86 for better software compatibility)
mounted /tmp as shmfs
moved the firefox cache to /tmp
installed preload

Anyone have any other ideas?

You'll never use that much memory unless you do some very heavy stuff like video editing/conversion and the like. Day to day normal desktop use will probably only ever use about 1-2 gig. More like 1 gig in fact. Try running google earth as well as your vm's.

---

### Post by cros13 on 2009-03-19
> **Locutus_of_Borg said:**
> you can load your entire firefox profile to tmpfs
speeds up FF's responsiveness quite a lot

Thanks for this.

This would probably work around those firefox3 sqlite issues as well wouldn't it?

---

### Post by cros13 on 2009-03-19
> **philinux said:**
> You'll never use that much memory unless you do some very heavy stuff like video editing/conversion and the like. Day to day normal desktop use will probably only ever use about 1-2 gig. More like 1 gig in fact. Try running google earth as well as your vm's.

I do a lot of video re-encodes on this desktop for a friends documentaries.
I never hit over a 1GB of memory use doing that either.
I'm using mplayer/mencoder with vdpau so maybe that would be an explanation?

---

### Post by sdennie on 2009-03-19
> **cros13 said:**
> Thanks for this.

This would probably work around those firefox3 sqlite issues as well wouldn't it?

If you mean the fact that firefox/sqlite does an fsync after it loads every single page, yes, this that is a workaround for it.

---

### Post by cros13 on 2009-03-19
> **sdennie said:**
> If you mean the fact that firefox/sqlite does an fsync after it loads every single page, yes, this that is a workaround for it.

cool

---

### Post by linuxisevolution on 2009-03-19
Install Windows 7 and vista and Xp in virtual machines and don't use them for anything, but it will be fun running, and you'll get a kick out of using all your ram. :D

I have 4gb of ram in this system. I typically run Ubuntu as the host OS and have Mac OS 10.5, Win 7, and windows 2000 in VM's. I put each in a diff workspace fullscreen so it's like having 3 oses.


And I only have 4gb of ram. Imagine what you could do with 12gb. Make sure you run desktop effects :P

Also, my system is upgradeable to 32gb :P

---

### Post by cros13 on 2009-03-19
> **Locutus_of_Borg said:**
> 
i run that at startup, and then have a cron job to run it again every five minutes

I also will execute the script for runlevels 0 and 6 to save the profile on shutdown and reboot.
Don't want to lose that lat 5 minutes of work ;)

---

