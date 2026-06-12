---
title: "VmSize Seems Really High"
date: 2008-06-30
forum: Desktop Environments
---

### Post by Brando569 on 2008-06-30
Like a lot of users now and in the past ive been experiencing memory problems where within a few hours my ram usage will go from 600mb to nearly 2gb and I cant seem to figure out why. I found out that one of the culprits is a superkaramba widget I have called logwatch which at one point was taking up 140mb when it should take up about 15-30mb.

Ive noticed now that in Ksysguard the VmSize for some of my programs is insanely high, at the top of the list is amarokapp with a size of nearly 570mb!! Firefox follows close behind with 497mb but the VmRss of these two is only 71mb and 90mb respectively.

I really need to figure out if these problems are distro based (they happen in linux mint also) or if theyre hardware based because this is really annoying.

---

### Post by hyperair on 2008-06-30
Definitely not hardware based, but not distro-based either. It's software specific. That superkaramba widget and amarok are just prone to either eating memory or leaking memory. In any case you should file a bug report.

---

### Post by Brando569 on 2008-06-30
if its neither, just program based then how do you explain it happening in both kubuntu 8.04 and mint4? im leaning towards my athlon 6400 being way too hot for a non OC'd processor and I know my dvd drive (is) was screwed up, i flashed the firmware on it and then seemed to fix it but i cant really be sure until i test out another drive and see if i get the same results.

---

### Post by hyperair on 2008-06-30
It's program based, that's why it happens on all distros which use that application.

---

### Post by Brando569 on 2008-07-01
i guess so. i still really want to know why my VmRSS (physical memory) is so high, over night i closed everything that i usually leave open (excluding my ram monitor which is a superkaramba widget that takes up about 20mb) to see if those were the culprits. when i woke up this morning i had about 90mb out of 2gb left, in the past 2 months that has happened a lot, before that it never happened. im still leaning towards a faulty processor or dvd drive, considering that my processor wouldnt even pass running orthos (dual core prime95 stress tester) for 8+ hours, it didnt flash "stop" it just completely froze and i saw that the temp was about 150F and it was at stock speed.

---

### Post by sdennie on 2008-07-01
Are you sure you are actually going up to 2G of RAM?  A better way to get proper memory information is to use:

```

free -m

```

The output should be something like this:

```

             total       used       free     shared    buffers     cached
Mem:          4049       3627        422          0        487       1397
[COLOR="Red"]-/+ buffers/cache:       1741       2308
[/COLOR]Swap:         4000          0       4000

```

The line in red contains the interesting numbers.

---

### Post by Brando569 on 2008-07-01
yea i am:

```
bran@ra:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2014       1685        329          0        466        862
-/+ buffers/cache:        355       1658
Swap:         1631          0       1631
```

after making ksysguard log my used memory,free memory and application memory ive found out that its the cached memory that is using up all of the space. it ate up 1.2gb in the course of about an hour and 20 minutes! during most of the this time (45 minutes) i was watching an episode of House MD on my computer and had nothing else running other than the normal system processes that are installed by default, except for konqueror in filemanager mode and ksysguard.

heres the first entry in the log of used memory and the last one up to this current time:

Jun 30 14:02:26 localhost mem/physical/used: 399012
Jun 30 15:48:02 localhost mem/physical/used: 1.72627e+06

this is the memory used by applications:

Jun 30 14:02:22 localhost mem/physical/application: 195192
Jun 30 15:52:55 localhost mem/physical/application: 368480

---

### Post by sdennie on 2008-07-01
> **Brando569 said:**
> yea i am:

```
bran@ra:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2014       1685        329          0        466        862
-/+ buffers/cache:        355       1658
Swap:         1631          0       1631
```

after making ksysguard log my used memory,free memory and application memory ive found out that its the cached memory that is using up all of the space. it ate up 1.2gb in the course of about an hour and 20 minutes! during most of the this time (45 minutes) i was watching a tv show and had nothing else running other than the normal system processes that are installed by default, except for konqueror in filemanager mode and ksysguard.

heres the first entry in the log of used memory and the last one up to this current time:

Jun 30 14:02:26 localhost mem/physical/used: 399012
Jun 30 15:48:02 localhost mem/physical/used: 1.72627e+06

That is normal and desirable behavior.  Cached memory is not technically "used" memory.  Look at the second line of your free -m out.  It says you are only using 355M of memory and that you have 1658M free.  Cached memory is just things that have been read off the disk.  If there is completely unused memory on the machine, it just keeps those things in memory to prevent needing to read them from disk again.  If that memory is eventually needed by an application, it will be given to the application but, otherwise, it's normal and almost always the case that the cache will eat up any unused memory.

---

### Post by Brando569 on 2008-07-01
I understand now,thanks. I was looking at that before when I posted that and was intrigued. I was curious as to why the system still performed well when I only had 75mb of ram left, this explains it. 

So I'm assuming that the freezes I've been experiencing are due to bugs in hardy itself (Ive read here that a small amount of users, someone said about 1% of the total users experience these freezes) and not necessairly with my hardware.

---

### Post by sdennie on 2008-07-01
I'm not sure why you experience freezes but, they shouldn't be related to cache memory.  Freezes are often because of driver issues (specifically, video driver issues).  If it freezes again, and it's a video driver problem, sometimes hitting Ctrl-Alt-F1 and then Ctrl-Alt-F7 can bring it back.

---

### Post by Brando569 on 2008-07-01
im experiencing both hard and soft freezes, most of the time restarting the xserver with ctrl+alt+backspace fixes it but other times nothing short of pressing the reset button will work. I just found out about the "Magic SysRq Keys" so im going to try those next time, but i think i disabled them when i compiled this kernel since i didnt know what they were and it said "if you dont know what this does, you can disable it"

also i have this annoying high pitched noise in my speakers that just started last night and its really annoying, see my thread about it [here](http://ubuntuforums.org/showthread.php?t=845813).

---

