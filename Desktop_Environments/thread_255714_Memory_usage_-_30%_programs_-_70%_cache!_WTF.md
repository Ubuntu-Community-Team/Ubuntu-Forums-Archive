---
title: "Memory usage - 30% programs - 70% cache! WTF?"
date: 2006-09-11
forum: Desktop Environments
---

### Post by mobilehavoc on 2006-09-11
Hi, 

I'm loving Ubuntu but somethings are bothering me like randomly (just now) after only being up for about 10 mins the memory monitor is showing 30% of my memory being used by programs and the other 70% in use by cache! WTF?

I have 2G of RAM...so that means about 500mb or so is in use by programs (perfectly possible since XGL/Compiz takes a lot but I don't care since I have plenty) but then cache takes up 1.5G!! What the hell is that about? I have a 4G swap partition and it never uses it...

Some days it'll run for days with 30% programs/30% cache but then all of a sudden this time it does this.

It's very odd because it doesn't seem to cause any problems..no crashes, no freezes or other errors but it's a little odd and I want to know if this is normal Linux/Ubuntu fashion or something is off.

Any ideas?

---

### Post by dickohead on 2006-09-11
the cache you refer to is your swap partition. so 70% of your swap is being used and 30% of your physical memory, a screenshot would be useful.

---

### Post by elvis on 2006-09-11
> **dickohead said:**
> the cache you refer to is your swap partition.

No it isn't.  Swap is held on disk.  Cache is a buffer held in memory.

[http://www.faqs.org/docs/linux_admin/buffer-cache.html](http://www.faqs.org/docs/linux_admin/buffer-cache.html)

The Linux kernel likes to cache agressively in order to speed up day-to-day performance.  This is perfectly normal, and not anything to worry about.  Cache is always given a lower priority than active memory pages used by running programs.

For example, say you have 500MB of RAM.  Say you are using 300MB in active use by programs, and 150MB of cache, leaving you with 50MB free.  If a program starts that requires 100MB, the cache will be told to pull back and allow for the active running program to reclaim the memory space.

The cache allows the system to respond much faster when you open programs, files, or link to dynamic libraries on a regular basis.  The overhead required for it to run is minimal, and does not affect the performance of your machine negatively.  In fact, without it life would be rather sluggish!

---

### Post by mobilehavoc on 2006-09-11
I can't take a screenshot because compiz screenshot is not working and the 70% in use by cache only shows up in the tooltip when I hover over the memory monitor but nowehere else. Everywhere else it shows only the amount being used by programs.

What's odd is that when it does this it uses my swap partition (~18mb) but the times when it doesn't load up cache it doesn't even touch my partition.

I just wish I could turn the cache overload feature on/off...I want to know what causes it to act differently.

---

### Post by elvis on 2006-09-11
> **mobilehavoc said:**
> I just wish I could turn the cache overload feature on/off...I want to know what causes it to act differently.

Once again, it's all handled automatically by the kernel.  Turning it off would probably do you more harm than good.

---

### Post by Midway on 2006-09-11
I, too, was alarmed by Linux's memory usage when I first started using it a couple of years ago.  I remember making a similar post at the time on the distro's BB.  It is one of those "Windows" things (the less RAM usage the better) you have to let go, lol.

---

### Post by dickohead on 2006-09-11
My bad, I 'assumed' that he had termed cache incorrectly, which is why Iworded my reply the way I did - sorry!

If you're not seeing a performance decrease I wouldn't worry about it.

---

### Post by mobilehavoc on 2006-09-11
> **Midway said:**
> I, too, was alarmed by Linux's memory usage when I first started using it a couple of years ago.  I remember making a similar post at the time on the distro's BB.  It is one of those "Windows" things (the less RAM usage the better) you have to let go, lol.
LOL! Yeah I guess so. I can understand from a technical perspective why using all available RAM for cache is the smart thing to do...otherwise it's just sitting there doing squat..

I think what got to me was the scale/quantity...500MB was in use by the programs but 1.5GB!!!! was used as cache. Guess just seemed excessive but whatever...good to know its normal.

---

### Post by mobilehavoc on 2006-09-11
Here's the screenshot...remember I have 2GB of RAM. Right after I took this screenshot, it went from 40%/60%.

[[IMG]http://img90.imageshack.us/img90/8222/screenshotxv4.png[/IMG]](http://imageshack.us)

---

### Post by elvis on 2006-09-12
> **mobilehavoc said:**
> Here's the screenshot...remember I have 2GB of RAM. Right after I took this screenshot, it went from 40%/60%.

Once again, this is totally automatic, and does not affect your performance negatively in the slightest.  What it does to is help to speed up your system, so don't stress too much. :)

---

### Post by tribaal on 2006-09-12
The ultimate documentation for this (at least, that I found :) ), is the first link in my sig.

It's a gentoo forum, but it's exactly the same in Ubuntu.

Hope this helps :)

- trib'

---

### Post by Linuturk on 2006-09-12
I actually had the same problem, except it was effecting my system performance negatively. (it would take up to 2 minutes for my screensaver to shut off and show the password prompt. I tracked it down to my bittorrent client, that was seeding 8 gigs worth of information. Removing that torrent fixed the problem. It still uses lots of cache (and sometimes my swap), but my machine is always responsive now.

I've read the link in your sig (great read, btw)

I'd like to know about configuring swappiness in Ubuntu, if you have any information. That might be the root of my (and the thread's author) problems. I run a laptop, so a lower swappiness seems to be a better choice for me to increase battery life :)

5. Swappiness (2.6 kernels)
Since 2.6, there has been a way to tune how much Linux favors swapping out to disk compared to shrinking the caches when memory gets full.

ghoti adds:
When an application needs memory and all the RAM is fully occupied, the kernel has two ways to free some memory at its disposal: it can either reduce the disk cache in the RAM by eliminating the oldest data or it may swap some less used portions (pages) of programs out to the swap partition on disk.
It is not easy to predict which method would be more efficient.
The kernel makes a choice by roughly guessing the effectiveness of the two methods at a given instant, based on the recent history of activity.

Before the 2.6 kernels, the user had no possible means to influence the calculations and there could happen situations where the kernel often made the wrong choice, leading to thrashing and slow performance. The addition of swappiness in 2.6 changes this.
Thanks, ghoti!

Swappiness takes a value between 0 and 100 to change the balance between swapping applications and freeing cache. At 100, the kernel will always prefer to find inactive pages and swap them out; in other cases, whether a swapout occurs depends on how much application memory is in use and how poorly the cache is doing at finding and releasing inactive items.

The default swappiness is 60. A value of 0 gives something close to the old behavior where applications that wanted memory could shrink the cache to a tiny fraction of RAM. For laptops which would prefer to let their disk spin down, a value of 20 or less is recommended.

As a sysctl, the swappiness can be set at runtime with either of the following commands:
Code:
# sysctl -w vm.swappiness=30
# echo 30 >/proc/sys/vm/swappiness

The default when Gentoo boots can also be set in /etc/sysctl.conf:
Code:
# Control how much the kernel should favor swapping out applications (0-100)
vm.swappiness = 30


Some patchsets allow the kernel to auto-tune the swappiness level as it sees fit; they may not keep a user-set value.

---

### Post by mobilehavoc on 2006-09-13
> **Linuturk said:**
> I actually had the same problem, except it was effecting my system performance negatively. (it would take up to 2 minutes for my screensaver to shut off and show the password prompt. I tracked it down to my bittorrent client, that was seeding 8 gigs worth of information. Removing that torrent fixed the problem. It still uses lots of cache (and sometimes my swap), but my machine is always responsive now.

I've read the link in your sig (great read, btw)

I'd like to know about configuring swappiness in Ubuntu, if you have any information. That might be the root of my (and the thread's author) problems. I run a laptop, so a lower swappiness seems to be a better choice for me to increase battery life :)

5. Swappiness (2.6 kernels)
Since 2.6, there has been a way to tune how much Linux favors swapping out to disk compared to shrinking the caches when memory gets full.

ghoti adds:
When an application needs memory and all the RAM is fully occupied, the kernel has two ways to free some memory at its disposal: it can either reduce the disk cache in the RAM by eliminating the oldest data or it may swap some less used portions (pages) of programs out to the swap partition on disk.
It is not easy to predict which method would be more efficient.
The kernel makes a choice by roughly guessing the effectiveness of the two methods at a given instant, based on the recent history of activity.

Before the 2.6 kernels, the user had no possible means to influence the calculations and there could happen situations where the kernel often made the wrong choice, leading to thrashing and slow performance. The addition of swappiness in 2.6 changes this.
Thanks, ghoti!

Swappiness takes a value between 0 and 100 to change the balance between swapping applications and freeing cache. At 100, the kernel will always prefer to find inactive pages and swap them out; in other cases, whether a swapout occurs depends on how much application memory is in use and how poorly the cache is doing at finding and releasing inactive items.

The default swappiness is 60. A value of 0 gives something close to the old behavior where applications that wanted memory could shrink the cache to a tiny fraction of RAM. For laptops which would prefer to let their disk spin down, a value of 20 or less is recommended.

As a sysctl, the swappiness can be set at runtime with either of the following commands:
Code:
# sysctl -w vm.swappiness=30
# echo 30 >/proc/sys/vm/swappiness

The default when Gentoo boots can also be set in /etc/sysctl.conf:
Code:
# Control how much the kernel should favor swapping out applications (0-100)
vm.swappiness = 30


Some patchsets allow the kernel to auto-tune the swappiness level as it sees fit; they may not keep a user-set value.
I might try this...I have noticed that my memory cache is directly linked to disk access. i.e. I have a bash script that updates meta tags on a bunch of video files and I watch my memory cache rocket with this.

The worst was when I run a script to do a full tar backup of my system and it went from 15% cache to 80% (20% for apps)...

I don't really care because the most I've seen it use in swap file is like 18mb..so far it doesn't seem to negatively effect my performance either.

If it does get bad though, I'll try and reduce the swapiness...does this effect the hard drive, memory cache or both?

---

