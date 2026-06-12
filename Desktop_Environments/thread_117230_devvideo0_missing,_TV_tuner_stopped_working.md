---
title: "/dev/video0 missing, TV tuner stopped working"
date: 2006-01-14
forum: Desktop Environments
---

### Post by endangst on 2006-01-14
Hi there.  I have a bt878 TV tuner and it was working just fine as card=16 tuner=28 watching TV via the composite input.

It was working fine for several days (and several reboots) in TVtime.

Now, suddenly, all I get is a blue screen in TVtime and it says there is nothing in my /dev/video0 file.

So I checked /dev/video0 and there is nothing there.

I tried sudo rmmod bttv
sudo rmmod bt878
 
then sudo modprobe -r bttv
sudo modprobe bttv card=16 tuner=28
 
It also says the bt878 is missing.
 
What went wrong?  Sorry, I'm a newbie at this stuff, but usually unloading and reloading the driver worked.  I even have it setup in /etc/modules.conf and /etc/modprobe.d/bttv (or something like that).   It is set to load bttv at boot up too.
 
I checked in Windows to see if maybe my TV card pooped out on me, but it is fine. :confused: 
 
Thanks for any help.  I really appreciate it! :(

---

