---
title: "using xrandr to set up multiple displays at startup"
date: 2012-01-18
forum: Desktop Environments
---

### Post by nezhac on 2012-01-18
Hey all,

Been a long time lurker of the forums, using them to solve any ubuntu problems I've ever had until now. Had a bit of a search the past few days and can't seem to find a solution.

Anyways I have a Radeon HD 5450 using the fglrx drivers, the proprietary ones just wouldn't enabling dual monitor support. Now to set up the dual monitors I run
```
xrandr --auto --output DVI-0 --mode 1680x1050 --left-of VGA-0
```If I don't specify the resolution (--mode) it puts both monitors at the same resolution, which they're not.

Now this works fine, but I added the same command at startup and it sets the same resolution for both monitors, even with --mode specified. If I run the same command again (ie. from terminal) , it fixes itself. 

I think I'm either missing something big or this may actually be a bug.

I'm on Ubuntu 11.10 using xfce after installing xubuntu-desktop.
The only other 'tweak' I have is redshift, and it doesn't make a difference wether running or not. Also, under unity this works as it should.

Any help/discussion etc. appreciated

Thanks

EDIT: It seems to have just fixed itself. Don't need to specify this command at startup anymore, it just assigns the right resolution. I'm a bit perplexed, but hey it's solved

---

