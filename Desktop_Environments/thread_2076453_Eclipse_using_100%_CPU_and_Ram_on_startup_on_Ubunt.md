---
title: "Eclipse using 100% CPU and Ram on startup on Ubuntu 12.10 x64"
date: 2012-10-26
forum: Desktop Environments
---

### Post by bond17_007 on 2012-10-26
Hi, 
  I use Eclipse IDE for development on my ubuntu 12.10 laptop. It is
Dell Studio 1558
Processor: i3
128 GB SSD HDD
8GB RAM

When i start my eclipse, i notice that all 4 core's go up 100% usage, fan kicks in. Looking at process monitor, it shows as "java".. using up over 1 gb of ram. I went and configured my eclipse.ini file also increasing xms and xmx values. But no luck
at times eclipse freezes and CPU and memory usages go very high. 
Can someone help? 

TY

---

### Post by tomns on 2012-10-27
I was having a similar problem in 12.04 before upgrading to 12.10 and haven't seen it since, so maybe it is a different problem.  But I found a post suggesting this and it worked for me:

sudo mv /usr/lib/x86_64-linux-gnu/libgailutil.so.18.0.1 /usr/lib/x86_64-linux-gnu/libgailutil.so.18.0.1.OFF

The library is used by the shutter application.  When I needed to run shutter I renamed the library back.

---

### Post by bond17_007 on 2012-10-30
@tomns,
  Thanks for your reply. that didnt seem to help :(.
Not sure why its eating up CPU like that even on a pretty good system config. When i had windows on this machine it didn't eat up this much cpu while loading Eclipse.
[ATTACH]226379[/ATTACH]

---

