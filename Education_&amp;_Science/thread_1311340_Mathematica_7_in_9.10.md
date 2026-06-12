---
title: "Mathematica 7 in 9.10"
date: 2009-11-02
forum: Education &amp; Science
---

### Post by gmcauley on 2009-11-02
I was wondering if anyone has tried Mathematica 7 (MM7) in Ubuntu 9.10?

There were some problems and a [fix]("http://ubuntuforums.org/showthread.php?t=1136142&page=6#56") for MM7 issues in 9.04, and a report of [problems with a beta version of 9.10]("http://ubuntuforums.org/showthread.php?t=1136142&page=7#63").

---

### Post by ZankerH on 2009-11-02
I've been using Mathematica on ubuntu since 8.04 and I've never encountered any trouble with it. This hasn't changed with 9.10.

---

### Post by gmcauley on 2009-11-02
Thanks ZankerH for your reply.

It is interesting that you did not see trouble with 9.04.  With the kernel update from 8.10 excessive cpu usage was an issue for, I thought, everybody (see [here]("http://ubuntuforums.org/showthread.php?t=1136142&page=4") and [here]("http://ubuntuforums.org/showthread.php?t=1136142&page=5")).

So you don't see excessive cpu usage with MM7 and 9.10?

---

### Post by ZankerH on 2009-11-03
I don't normally check my CPU usage all the time, but I didn't see any noticeable slowdowns, no.

---

### Post by rofman on 2009-11-08
Same as 9.04. Java at ~ 15% CPU  for no reason.

---

### Post by kaspar_silas on 2009-12-04
> **gmcauley said:**
> Thanks ZankerH for your reply.

It is interesting that you did not see trouble with 9.04.  With the kernel update from 8.10 excessive cpu usage was an issue for, I thought, everybody (see [here]("http://ubuntuforums.org/showthread.php?t=1136142&page=4") and [here]("http://ubuntuforums.org/showthread.php?t=1136142&page=5")).

So you don't see excessive cpu usage with MM7 and 9.10?

I checked and I also do not see excessive CPU problems (~7%).

---

### Post by DipanjanRay on 2009-12-09
I have the CPU excessive load issue running Mathematica 7.0.0 on karmic.

Renaming the JLink directory  (see [http://ubuntuforums.org/archive/index.php/t-1136142.html](http://ubuntuforums.org/archive/index.php/t-1136142.html)) solves the problem completely, at the cost of disabling Documentation Center, etc.

---

### Post by mikelito on 2010-02-03
See
[http://ubuntuforums.org/showpost.php?p=8769399&postcount=71](http://ubuntuforums.org/showpost.php?p=8769399&postcount=71)
for a workaround to the java problem.

---

### Post by andres.ordonez on 2010-03-24
I'm using 9.10, had the same problems with the cpu usage but the fix worked for me too! Thanks for that.

I also had the Plot3D problem and fixed by changing the accel method to uxa (while using 9.04).

---

### Post by GIdervish on 2010-04-12
Just a quick update - Mathematica 7.0.1 has the same problems - they've included the 64 bit file updates, but not the 32 bit one (adding this reduced the usage on my computer (not including java) from ~40% to 1-2%.

The java problem seems to still be around - but blocking access to the folder works well.

---

