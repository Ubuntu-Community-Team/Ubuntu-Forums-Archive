---
title: "gDesklets: FTB gauges not working"
date: 2005-10-18
forum: Desktop Environments
---

### Post by matthias_k on 2005-10-18
Hi,

I was using the FTB desklets in Hoary. In Breezy however, the gauges don't seem to work. The textual information seems to be ok (e.g. free disk space in megabytes), but the bars are always at 100%.

Does anyone else have these problems?

---

### Post by chajuram on 2005-10-18
Hi,

I have exactly the same problem. i was wondering if re installing will fix the problem. Even iWeather has some problem, with numbers overlapping.

Chajuram.

---

### Post by Tanjerine on 2005-10-24
Hi, i tried re-installing. It didn't help. :( Still searching the net for possible solutions. Will post back if I find anything.

---

### Post by matthias_k on 2005-10-25
*bump*

Still not fixed. Shall I file a bug report? I didn't get an answer on gnome-net IRC either.

---

### Post by Duncan_Idaho on 2005-11-01
same problem here, :confused: 
but not only FTB, but EVERY gauge-based Desklet shows a 100% or an offscale gauge :shock: :shock: :shock: :shock: :shock: 
my brother have the same problem on his laptop :( 
any clue how to fix that? :confused:

---

### Post by RanDinCarolina on 2005-11-02
Same problem here. None of the gauges work correctly, but the info displayed is correct.

---

### Post by arnieboy on 2005-11-02
I am wondering if an older version of gdesklets would solve this problem. am not sure though.. worth a try.

---

### Post by Duncan_Idaho on 2005-11-04
so, anybody has managed to get desklet's gauges to work properly??? :confused:

---

### Post by RanDinCarolina on 2005-11-09
i'm actually using the side candy desklets. Has anyone screwed around with the code?

---

### Post by Canuckelhead on 2005-11-12
Wow... I'm Glad to see that I am not the only one with this problem... its driving me nutty....  I have tried everything I can think of...

---

### Post by NicP on 2005-11-20
also having this problem, any suggestions?

---

### Post by chajuram on 2005-11-20
Still no solution I am guessing.

---

### Post by Sutekh on 2005-11-22
I also noticed that the percentage of space used on my ext3 partitions is always exactly 5% greater than what the System Monitor says.  The used and free space amounts are incorrect aswell but it always makes a 5% difference.  My FAT32 and NTFS partitions are correct though.

---

### Post by matthias_k on 2005-11-22
Okay, let's rephrase the question:

Is there **anyone**, who is using gDesklets with Breezy and does **not** have these problems?

---

### Post by tomwell on 2005-11-22
I have the same prob... 

Also does anyone else get the info on the side candy overlapping when it is minimized to the side... attached screen shot....

Its not so bad since i rarely minimize them, but kind of stops me from minimising if i want to...
I like the desktop to be perfect... LMAO!!!

Tom

---

### Post by Efwis on 2005-11-22
[QUOTE=matthias_k]Okay, let's rephrase the question:

Is there **anyone**, who is using gDesklets with Breezy and does **not** have these problems?[/QUOTE]
I had that problem too, so I didnt' use those desktlets, I downloaded some other guages from the site, they work fine.

---

### Post by skirkpatrick on 2005-11-22
So what other gauges do work correctly?

---

### Post by NicP on 2005-11-23
[QUOTE=skirkpatrick]So what other gauges do work correctly?[/QUOTE]

yeah ive been downloading some, and none of them seam to work correctly either

---

### Post by Efwis on 2005-11-23
let me retract that, I'm not using guages, I'm using the plotters. I've been messing around with the guages files to see if I can get them to work properly. Its something in the script somewhere. Once I find it I will post here to let you know. Hopefully I will have an answer today.

---

### Post by Sutekh on 2005-11-23
[gdesklets Dev Book]("http://dev.gentoo.org/~nixphoeni/gdesklets/develbook/book.html")

Check out section 4.12 on gauges, maybe that will be helpful

---

### Post by Efwis on 2005-11-23
Thanks,
i will be gone until monday, so that will be the earliest I can work on it.

---

### Post by Canuckelhead on 2005-11-23
Yeah I have also switched to the plotters... but they are nowhere near as nice...

---

### Post by skirkpatrick on 2005-11-25
I'm not sure it's in the FTB scripts as desklets that I had that worked in Hoary don't work in Breezy and I haven't updated them.

---

### Post by griefman on 2005-12-01
i just wanted to mention, that the problem, seems to me, is in the gDesklets programm itself, because i checked the sources of the Sidestripes disk gauge, there are actually two files that are used with this applet (theme.py, disk.py), and because i'm not "very good" in python i just set constant values for the bar to see if it would eventually show something different for a change.... and... guess what... nothing... i could only get its height to change but not its width. And that's why i think that the problem should be in the daemon, couse the numeric value for free space is ok... and the graphic is not...pfuii... and i was hoping that a little touch in the source... and everything will be ok.... but... it look somehow silly to think that when none of the applets isnt working the problem is in the applets not in the daemon.... but the hope dies last:)

good luck to those who are digging deeper... but my knowledge in the case is somehow not enough to help further.

---

### Post by NicP on 2005-12-01
I removed the gdesklets packages in synaptic and compiled version .34.3. I still get the same problems (broken gauges) when i download desklets and try to use them.

---

### Post by matthias_k on 2005-12-06
Since noone could come up with a solution so far and something obviously is broken, I have filed a bug for the gdesklets package:
[https://launchpad.net/distros/ubuntu/+source/gdesklets/+bug/5433](https://launchpad.net/distros/ubuntu/+source/gdesklets/+bug/5433)

It doesn't look as if the developers care much about this package though; another 12 weeks old bug hasn't even beed assigned yet... That's what happens when you have extremely short release cycles, probably everyone is working on Dapper Drake already... *sigh*

---

### Post by Efwis on 2005-12-06
[QUOTE=matthias_k]Since noone could come up with a solution so far and something obviously is broken, I have filed a bug for the gdesklets package:
[https://launchpad.net/distros/ubuntu/+source/gdesklets/+bug/5433](https://launchpad.net/distros/ubuntu/+source/gdesklets/+bug/5433)

It doesn't look as if the developers care much about this package though; another 12 weeks old bug hasn't even beed assigned yet... That's what happens when you have extremely short release cycles, probably everyone is working on Dapper Drake already... *sigh*[/QUOTE]
I became a member at the gdesklets site and filed the bug there a few weeks ago. Hopefully this will help get this resolved.

---

### Post by arnieboy on 2006-03-21
This GTK 2.8 related bug has been resolved in version 0.35.3. I have compiled this version of gdesklets from source and the gauges work just fine.

alternatively the instructions outlined in the following post might work as well:
[http://ubuntuforums.org/showpost.php?p=784353&postcount=5](http://ubuntuforums.org/showpost.php?p=784353&postcount=5)

---

### Post by arnieboy on 2006-03-21
ignore this post.

---

### Post by dpm on 2006-04-29
arnieboy: thanks for pointing out that there is a new version of gDesklets that solves this issue.

After compiling and installing the new version on my Breezy system the problem was gone. 

This version seems to also work for Dapper. After upgrading to Dapper, I just had to recompile gDesklets and now the FTB gauges are also working on my Dapper system.

BTW, in case anyone is interested, here's a bug report in malone regarding this issue:

[https://launchpad.net/distros/ubuntu/+source/gdesklets/+bug/5433/+index]("https://launchpad.net/distros/ubuntu/+source/gdesklets/+bug/5433/+index")

---

