---
title: "considering reinstall, need advice"
date: 2005-12-12
forum: Desktop Environments
---

### Post by nalmeth on 2005-12-12
ey guys
my computer is an EM64T 3.4 gHz with built-in intel i915 processor, with 512 ram. I have worked hard to set-up my comp with breezy just the way I want it with amd64, but I think I want to re-do it all. 
I have been having problems with my graphics card, and maybe running in i386 will help that..
From what I hear, there is nothing lost with running i386 on an amd64 computer.. So unless anybody can dissuade me from doing this, I will.
I'm sort of :eek: considering installing XP aswell. I want to look into VMware etc. i think it would be cool to have a multi-OS system. I heard that MCN-Live can be installed onto a windows system, or maybe it was PCLinuxOS.
Anybody see any problem with installing i386 on amd64, or are there any suggestions otherwise?

thanks
peace

---

### Post by akiro.yamamoto on 2005-12-12
You can use the normal (i386)ubuntu 5.10 that's what i'm using right now.
If your using an EMT64 processor ? That's an intel processor so the normal ubuntu will work... You will also have better driver support etc in the 32bit world right now.

---

### Post by akiro.yamamoto on 2005-12-12
BTW:
If your CPU supports SSE3 I've heard reports of people installing OS X x86 on there Intel systems. I've never tried it but it sounds interesting...something else I can play with after all it's that time of year :smile:

EDIT:
Don't try the OS X x86 deamoo dvd.... this is a legal mine field.... wait for the official Apple Intel machines in Feb 2006.
Regards

---

### Post by akiro.yamamoto on 2005-12-12
If your considering a re-install remember back-up your /home directory.
I recently did a re-installl (don't ask :smile:) and when ubuntu came up the first time after the re-install........
Same background....same look and feel...flash plugin still working... WOW!
Of course I also did a back-up of my .deb files I had installed with Synaptic.
But if your switching from AMD64 to i386 (or similar)version YMMV...

---

### Post by nalmeth on 2005-12-12
I'm not sure if i'm SSE3 supported, tho it sounds like an enticing endeavor!
the wiki says:
Pentium 4 (since Prescott)
I have pentium 4, with hyper-threading. 
[http://www.dealtime.com/xPF-CPU_P4_3_0GHz_800M_LGA775_2M_RTL](http://www.dealtime.com/xPF-CPU_P4_3_0GHz_800M_LGA775_2M_RTL)
This page seems to say I am indeed supported.
I'm no hardware buff, so I don't know what boat I'm in there..
And to illustrate by lack of buff, I was actually worried about installing i386 ubuntu, my packaging says only 64-bit architecture will operate. I suppose they would say that for liability's sake.

I didn't know you could just reinstall with all your personal settings saved..
Every time I do it I just reformat everything..

---

### Post by tomwell on 2005-12-12
Akiro,

Are you saying that if i was to back my home directory up and delete Ubuntu completely(ie Reeinstall) when i restore  my Home directory it will look exactly the same have all the right multimedia plugins and Gdesklets and everything????

Just real curious...

Peace

Tom

---

### Post by nalmeth on 2005-12-12
here's a weird thought..
could I just do a dual boot with 32-bit and 64-bit, remove my current chroot, and then chroot into the new 32-bit install? I know it sounds like a waste of time, but hey, like you say its that time of year. I actually enjoy chrooting.. :p 

thanks for reply's guys

---

### Post by akiro.yamamoto on 2005-12-12
I've done this... of course YMMV :smile:
When I first installed Ubuntu I created a seperate /home partition.
After I hosed my / system (playing too much :smile:) I did a reinstall, used the same user account.... and PRESTO..... My look and feel was exactly the same....
At this point I said OMG that is SSOOOOO &*%^$%%# COOL!
And nearly wet myself :smile:
Anyway I had also followed the directions on the old UnOfficial Ubuntu Guide and created a back-up of my Synaptic cache (dial-up is a real pain) so that I would not have to re-download the files and programmed I went through all the trouble and TIME of downloading the first time...
I have come realise.... BACK-UPS ARE YOUR FRIEND :smile:

---

### Post by akiro.yamamoto on 2005-12-12
BTW:
I'm doing a little research on the Intel 64bit computing in Ubuntu...
There seems to be a ia64 bit port of Ubuntu 5.10. 
Interesting ?! 
Although it clealy states on the status page :
[https://wiki.ubuntu.com//IA64PortStatus](https://wiki.ubuntu.com//IA64PortStatus)
That this port is not Officially supported.. however you are able to get a copy of the Ubuntu 5.10 ia64 CD....
Regards...

EDIT:
It's now 6.04 dapper pre-release:
[http://cdimage.ubuntu.com/ports/daily/current/](http://cdimage.ubuntu.com/ports/daily/current/)

---

### Post by akiro.yamamoto on 2005-12-12
[QUOTE=tomwell]Akiro,

Are you saying that if i was to back my home directory up and delete Ubuntu completely(ie Reeinstall) when i restore  my Home directory it will look exactly the same have all the right multimedia plugins and Gdesklets and everything????

Just real curious...

Peace

Tom[/QUOTE]

gDesklets stores your config under the .gdesklets folder in your home directory. gDesklets will not work unless you re-install ( the program is not stored in your home folder, but under / ) it and run it the first time.. 
All you personal configuration files are stored in your /home folder. As long as your reinstall your programs, it's all good.
If like me you made some ahhh dubious software changes and that hosed your install rather than a hardware failure this step by step approach may help. Of course on my system ubuntu / only uses about 2.3 Gb of space so I could back up the entire thing to 1 dvd or use simple backup to backup and restore it.
In linux there are many different ways to accomplish a needed task...
I was just relating my own experience.. :smile:

---

### Post by akiro.yamamoto on 2005-12-12
[QUOTE=nalmeth]here's a weird thought..
could I just do a dual boot with 32-bit and 64-bit, remove my current chroot, and then chroot into the new 32-bit install? I know it sounds like a waste of time, but hey, like you say its that time of year. I actually enjoy chrooting.. :p 

thanks for reply's guys[/QUOTE]
I'm actually not sure about the whole chroot thing, but I'll look into it and post back when I have anything concrete to report..
regards.

---

### Post by tomwell on 2005-12-12
Sounds like the best way!! So if i install a shitty program i can then do a reeinstall and reinstal my docs without having to install the bad program again...

Cool!!!

Thanks Akiro

Peace

Tom

---

### Post by akiro.yamamoto on 2005-12-12
[QUOTE=nalmeth]here's a weird thought..
could I just do a dual boot with 32-bit and 64-bit, remove my current chroot, and then chroot into the new 32-bit install? I know it sounds like a waste of time, but hey, like you say its that time of year. I actually enjoy chrooting.. :p 

thanks for reply's guys[/QUOTE]

I did a little searching and found this :
[http://ubuntuforums.org/showthread.php?t=100776](http://ubuntuforums.org/showthread.php?t=100776)
Hope that gets you started in the right direction....
I'm in the same boat... I have a EMT64 CPU as well :smile:
Will pst back any developements....

---

### Post by akiro.yamamoto on 2005-12-12
[QUOTE=tomwell]Sounds like the best way!! So if i install a shitty program i can then do a reeinstall and reinstal my docs without having to install the bad program again...

Cool!!!

Thanks Akiro

Peace

Tom[/QUOTE]

No probs ;)

---

### Post by akiro.yamamoto on 2005-12-12
nalmeth:
I also found this:
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)
I think I might try this.... so I can switch from the 32bit to the 64bit....

---

