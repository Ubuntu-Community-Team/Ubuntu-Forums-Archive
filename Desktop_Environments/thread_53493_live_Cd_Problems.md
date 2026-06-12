---
title: "::live Cd Problems::"
date: 2005-08-01
forum: Desktop Environments
---

### Post by pja on 2005-08-01
Like many others (see posts on the next page) I downloaded the new Kubuntu Live CD (twice as it turned out) only to find that **IT WON'T BOOT**.  There has been a great deal of discussion of this issue over the past couple of days but Kubuntu developers seem to be totally silent.  I'm not making an issue out the software not working (we all make mistakes at some time or other) but I think we need somebody to acknowledge that the problem exists and a fix is being worked on and (ideally) should be available by...

Kubuntu is/was a great distro, but this level of support makes one wonder.

Please **just let us know whats happening**.

Regards,
Peter   ](*,)

---

### Post by news4doug on 2005-08-01
What specific version and problem are you having? Are you talking about the "repawning too fast: disabled for 5 minutes"
message repeated w/ Kubuntu 5.04.5 LiveCD?

Have you considered reverting back to a previous release and doing an online update? I might try that if I can't get any
answers soon.

Also considered trying to install under VMware 5 to see if I get the same problem and try to debug it w/o screwing up my 
system. Not sure if it runs under VMware though.

I've been searching thru the online forums and newsgroups (for Kubuntu, Ubuntu, and Debian) for answers to this specific
problem and haven't come up w/ any quick fixes yet.

When I tried the "live-expert" boot, I didn't get that message, but it still hung up. Have considered trying interactive boot
again, changing some parameters, but just don't have the technical knowledge to know what to change as well as no
patience.

Right now, I feel like I wasted my time burning this update to CD and can't understand why there hasn't been any resolutions
posted. I also can't understand why this distro is so popular when it won't boot on some of my systems while KNOPPIX boots
up on every system I have without any problems.

IS ANYONE ELSE HAVING PROBLEMS BOOTING THIS NEWEST RELEASE???

IS THERE ANYONE OUT THERE WITH AT LEAST A QUICK FIX FOR THIS???  HELLO?    Doug     ](*,)

---

### Post by news4doug on 2005-08-01
Well, my further investigations into this problem suggest booting into single-user or text mode and edit the /etc/inittab file, removing entries fo getty, then proceeding w/ regular boot (CTRL-D?) into the usual runlevel (5?).

Now what I think is crazy is that this was a problem YEARS AGO w/ older versions of Linux. Why is it a problem/nuisance now?  Doug

 :roll:

---

### Post by pja on 2005-08-02
Doug,

I will give it a go and let you know what happens.

Regards,
Peter

---

### Post by ktux on 2005-08-02
[QUOTE=pja]Doug,

I will give it a go and let you know what happens.

Regards,
Peter[/QUOTE]

i had the same problems with the lice cd . dl it twice and it didn't work on my 
laptop or the desktopmachine .and there are many others who couldn't boot it :

[http://osnews.com/comment.php?news_id=11396](http://osnews.com/comment.php?news_id=11396)

hope they will release a bootable cd soon . i admire the work they have done with
(k)ubuntu so far , and the future  seems bright . 
thx for the effort :-)

cheerz pete

---

### Post by phil91 on 2005-08-02
Source: [http://www.kubuntu.org/~amu/kubuntu-5.04.5-i386-live.iso](http://www.kubuntu.org/~amu/kubuntu-5.04.5-i386-live.iso)
I have downloaded the last Kubuntu version and i have the following messages booting on the Live CD:  :roll: 

```
"AMD Athlon Processor" is _not_ to support power_saving
```

During the "Checking battery state", i got

```

"id1" respawning too fast: disable for 5 minutes 
"id2" respawning too fast: disable for 5 minutes 
"id3" respawning too fast: disable for 5 minutes 
"id4" respawning too fast: disable for 5 minutes 
"id5" respawning too fast: disable for 5 minutes 
"id6" respawning too fast: disable for 5 minutes 
* No more processes left in this runlevel 

``` 


I have tested the Live CD on 
- my Athlon 1 Ghz (A7V133), RAM 512, HD 20 Go, HD 40 Go (IBM 60 GXP), PCI sound blaster 128, Graveur NEC 3500, DVD Plextor, screen AL707
- a laptop Athlon 64 3000+
- a Sempron 3000+

I still have the same problems. ](*,) 

I have already tested others Live CD as Kaella 2.01, Knoppix 3.2 & 3.8, Geexbox, GoblinX, and no problem occured  :-# 

Any solution for this problem?

---

### Post by 514 on 2005-08-05
I have just experienced the same problem on 2 cds. Thank you for writing about it.

I downloaded it from:

[http://www.linuxisotorrent.com/index.php?view=Kubuntu%205.04.5%20Live%20CD%20KDE%203.4.2](http://www.linuxisotorrent.com/index.php?view=Kubuntu%205.04.5%20Live%20CD%20KDE%203.4.2)

---

