---
title: "World of Warcraft and Cedega - Hard drive access stutter"
date: 2005-10-14
forum: Gaming &amp; Leisure
---

### Post by kidcharles on 2005-10-14
I had WoW running smooth in Mandrake 10.1 and yesterday I took the plunge and replaced Mandrake with Ubuntu 5.10. I installed the semi-latest nvidia drivers (7667) which was an upgrade from what I was using before (7174) and the latest cedega (4.4.3), and used the same config file I used before. It seemed to run fine but now I'm getting incessant hard drive access causing frequent stuttering. The fps is fine, but ths constant HD thrashing makes the game borderline unplayable. Any thoughts on this? I tried the version of cedega I used before (4.3.2) and have the same problem.

---

### Post by GIBson3 on 2005-10-14
I'd be willing to bet you it isn't your Ubuntu... I have the same issue on one of my 2 Windows based Gaming boxes...

2.4c P4
512Megs Corsair XMS 2-3-3-6 pc3200
GeForce 4 TI-4600.

The only thing I've been able to figure the cause of this problem is that it's Primary Drive is an old 5400rpm 13 gig that's about 6-7 years old.  I'll try swapping the primary to a new 7200 80gig and hope that does it.

heh and who knows maybe I'll take the plunge and move my Gaming systems over to linux, Since my work box is just so Happy ;)

~GIBson3 :D

---

### Post by AsteriskNix on 2005-10-15
try sudo hdparm -d1 /dev/hda ( or /dev/hdwhatveryourdriveletteris )

then rerun it.

DMA isn't always on by default

---

### Post by kidcharles on 2005-10-15
I went ahead and did "hdparm -d1" on both my drives and I played a bit, I don't think the problem improved much if at all.  Good suggestion though.

Last night I put Mandrake 10.1 back on a different partition, and the stuttering was just as bad, so maybe it was in my imagination that it was worse in Ubuntu, as embarrasing as that is to admit.

Still, I wonder if there aren't some tweaks to minimize the problem...

---

### Post by OcirgamPT on 2005-10-15
Well I also play WoW, and I have been doing it in windows, I get losts of "stutters" too, Wow really needs ram, 1GB should be ok, but iff you go to pvp areas like BGs you will always have that "lag" "stutter", at least with my PC.

I got a 2.4GHz AMD (Overclocked) 1GB ram, 120 SATA, 9600pro, and wow runs in pve ok, but pvp omg Im always whining :(

---

### Post by kidcharles on 2005-10-16
I have 1GB of RAM, anything less is unplayable on any OS.

After yet further examination, I think I've determined that it the stuttering is not hard drive related, but may be due to slow rendering, which makes me suspect the drivers.  The reason I think this is that the stuttering occurs when I face in a new direction, particularly outside.  If I've recently looked in that direction, there is no stuttering, but if I haven't, there is a pause.  It is much reduced inside caves, but is still present.  I'll continue testing and report back.

---

### Post by GIBson3 on 2005-10-17
[QUOTE=kidcharles]I have 1GB of RAM, anything less is unplayable on any OS.

After yet further examination, I think I've determined that it the stuttering is not hard drive related, but may be due to slow rendering, which makes me suspect the drivers.  The reason I think this is that the stuttering occurs when I face in a new direction, particularly outside.  If I've recently looked in that direction, there is no stuttering, but if I haven't, there is a pause.  It is much reduced inside caves, but is still present.  I'll continue testing and report back.[/QUOTE]

I spent most of my free time this weekend doing a bunch of testing. I turned Graphics down to the Bare minimum (well as far as wow goes). and played around with the Studder.  While it is Definately Ram related, the studder happens when I hit the Pagefile in Win. >.< I'll be Ordering more Ram once I get Paid this week.

Being that you are running a ATI-R9600 the drivers are probably beating on you (as has been my experiance with the Radeons under any flavor of Linux). 1 Gig of Ram is plenty I've seen no difference between 1 Gig and 1.5Gigs on my other box.

~GIBson3 :D

---

### Post by kidcharles on 2005-10-17
Actually I'm using an nvidia card (Geforce 6600 GT). About a year ago I tried for many, many an hour to get my Radeon 9500 Pro working under linux with no success.  I finally was able to get it working in Ubuntu 5.04, but the performance was horrible.  I bought the Geforce specifically because of this problem and have been pretty happy overall.

---

### Post by GIBson3 on 2005-10-18
[QUOTE=kidcharles]Actually I'm using an nvidia card (Geforce 6600 GT). About a year ago I tried for many, many an hour to get my Radeon 9500 Pro working under linux with no success.  I finally was able to get it working in Ubuntu 5.04, but the performance was horrible.  I bought the Geforce specifically because of this problem and have been pretty happy overall.[/QUOTE]

oops
the sceond "chunk" of my last post was suppose to have 
[quote=OcirgamPT]I got a 2.4GHz AMD (Overclocked) 1GB ram, 120 SATA, 9600pro, and wow runs in pve ok, but pvp omg Im always whining [/quote]
Before it [COLOR="Sienna"]d[COLOR="Blue"]o[/COLOR].[COLOR="Blue"]0[/COLOR]b[/COLOR]

sorry about that.

~GIBson3 :D

---

