---
title: "Lirc/Myth/Ubuntu/New Kernel"
date: 2006-09-15
forum: Desktop Environments
---

### Post by dartmusic on 2006-09-15
I am running Ubuntu Dapper on my MythTV (.19) HTPC.  Everything has been working great, until the last kernel upgrade, which seemed to break lirc (I guess), as my remote no longer works.  If I reboot with the previous kernel, everything is fine.  Today's update included another kernel upgrade, which I had hoped would fix this problem, but, it did not.

Any ideas?

Thanks in advance.

---

### Post by dartmusic on 2006-09-19
Wow...42 people looked at this message since I posted it, and no one has any idea of what to do?  Today a new kernel was released in the repos, but it won't mean anything to me on my HTPC since I have to use an older kernel or my remote won't work.

Anyone?  Pleeeease??!! :D 

Thanks.

---

### Post by marplar on 2006-09-20
I had a similar problem after the kernel upgrade. To resolve I did the following:

1. Installed the kernel headers for the new kernel from synaptic (linux-headers-2.6.15-27-amd64-k8 in my case)

2. Removed the previous lirc installation (*make uninstall* as root from the lirc source directory)

3. Reconfigured, recompiled and reinstalled lirc (*./setup.sh *- Save and Configure, *make*, *make install* as root from the lirc source directory)

Now it works with the new kernel :D

---

### Post by dartmusic on 2006-09-21
Seriously?  Just 4 steps?

I'm nervous, but I'll try it when I get home tonight.

Thanks!

---

### Post by dartmusic on 2006-09-21
Argh...now I can't find the appropriate directory for the lirc source.  I'm soooo confused!

---

### Post by reclusivemonkey on 2006-09-22
> **dartmusic said:**
> Argh...now I can't find the appropriate directory for the lirc source.  I'm soooo confused!

This won't really help your problem I'm afraid, but I would suggest once you get MythTV up and working, DO NOT APPLY ANY UPDATES!!! This one certainly comes into the realm of "if it ain't broke, don't fix it". Unless you are using the web features of MythTV, you shouldn't need to worry about any updates. I run my MythTV on Slackware, so its nice and stable. With the recent "troubles" with X and Ubuntu updates, this is all the more important IMHO. MythTV 0.20 is out, so you may want to go the whole hog and update to that.

---

### Post by dartmusic on 2006-09-22
I've had Myth running for about 4 months now, always done all updates (after checking the forums for issues) and not had any problems other than this currently one with lirc.  I upgraded from .19 to .20 last week and it's great...I would just like to be able to use the newest kernel, and stop having to manually choose a different kernel from GRUB whenever I (rarely) have to reboot.

Thanks.

---

### Post by kidcharles on 2006-09-22
This is not directly related, but if you don't want to have to manually change which kernel is loaded by grub, you can alter /boot/grub/menu.lst and change the line that says 'default 0' to a different number. This will change which OS (or kernel) grub will load without any user input at boot time. Remember that separators (like "Other operating systems:") count in the 'default' numbering scheme.

---

### Post by reclusivemonkey on 2006-09-23
> **dartmusic said:**
> I've had Myth running for about 4 months now, always done all updates (after checking the forums for issues) and not had any problems other than this currently one with lirc.  I upgraded from .19 to .20 last week and it's great...

What do I have to look forward to then? :D 

I have a Nokia N80 and read on the Wiki that they had implemented UPnp so I am interested in testing that out. How is that new experimental commercial detection???

---

### Post by dartmusic on 2006-09-23
Honestly, as far as UPnP and commercial detection, I'm a little at a loss as I haven't tested out either.  I mostly use Myth to play back movies or downloaded TV shows.  I've had problems with .19 with regard to actually recording shows and I need to get a new hard drive (or clear mine out a bit) before I can record anything.  Though, UPnP does sound interesting, just not useful in my tiny apartment!

Now...if I could only figure out how to update/upgrade lirc...!

---

### Post by tlue on 2006-09-24
> **dartmusic said:**
> I am running Ubuntu Dapper on my MythTV (.19) HTPC.  Everything has been working great, until the last kernel upgrade, which seemed to break lirc (I guess), as my remote no longer works.  If I reboot with the previous kernel, everything is fine.  Today's update included another kernel upgrade, which I had hoped would fix this problem, but, it did not.

Any ideas?


Lirc usually needs a Kernel-Module corresponding to your tv-card (i.e. the module lirc_i2c for an old Hauppage-TV-Card) These modules are located in /lib/modules/2.6.15-**26**-386/misc/, where 2.6.15-26-386 was my kernel before this update. Because of the new Kernel (i.e. 2.6.15-**27**-386) you must recompile the Lirc-Kernel-Modules which then will automaticly be created in the corresponding folder. 
Because I'm just a "user", I just reinstall the whole lirc from source according to this guide:
[http://www2.truman.edu/~dat725/htpc_single.html#htpc6](http://www2.truman.edu/~dat725/htpc_single.html#htpc6)
Now it works again.

---

