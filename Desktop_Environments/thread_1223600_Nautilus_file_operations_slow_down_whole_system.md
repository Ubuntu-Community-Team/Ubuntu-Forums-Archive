---
title: "Nautilus file operations slow down whole system"
date: 2009-07-26
forum: Desktop Environments
---

### Post by ridetheteapot on 2009-07-26
hey, I've been noticing that when i use nautilus to move or copy large files my whole system slows down, making multitasking a pain. I dont have this problem at all moving the same files at cli.
i use reiserfs, if that matters on 2 decently fast satas.

Is there a fix for this, or am i the only one experiencing it?

---

### Post by Anzan on 2009-07-26
No, Nautilus sucks. Literally.

You might want to try Thunar or PCMan or Rox.

---

### Post by ridetheteapot on 2009-07-29
wow --- if i dump nautilus will i still have a desktop area for files and launchers?

too bad nautilus is still kinda bunk --- it has more features than thunar, but like 0 of them work.

---

### Post by AoSteve on 2009-07-29
I still use Nautilis.   I do a few large file transfers and get the slowdowns but I don't mind too much as I usually set aside time just for file transfers.  Thunar is nice but lacks features.   I just make do for now.   I may try out Rox tho.

---

### Post by asmoore82 on 2009-07-29
hmmm... I don't have any trouble with Nautilus except for network transfers.

---

### Post by Anzan on 2009-08-01
Oh, I still use it. Even in Fluxbox (nautilus --no-desktop). It's good for network servers and such.

And the new tabbing is an improvement.

But it can take up to a minute to load dirs with a lot of files, especially if there are thumbnails.

I just give it its own workspace so I can just let it spin its wheels and go back to it later.

But if the lagginess bothers anyone, PCMan and so on are good choices. Or Midnight Commander even.

But then the fastest is $ cd.

---

### Post by gunbladeiv on 2009-08-02
I'm having the same problem even when i use CLI to transfer files. The whole system will turn slow and multitasking is a pain.  So i dont think it's a problem with nautilus after all.

---

### Post by c-shadow on 2009-08-02
There are some features of linux kernel that could be responsible for the simptoms you have.
Check these links:

[http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that](http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)

[http://stackoverflow.com/questions/392198/how-to-make-linux-gui-usable-when-lots-of-disk-activity-is-happening](http://stackoverflow.com/questions/392198/how-to-make-linux-gui-usable-when-lots-of-disk-activity-is-happening)

[http://friedcpu.wordpress.com/2007/07/17/why-arent-you-using-ionice-yet/](http://friedcpu.wordpress.com/2007/07/17/why-arent-you-using-ionice-yet/)

[http://www.linuxjournal.com/article/6931](http://www.linuxjournal.com/article/6931)

---

### Post by ridetheteapot on 2009-08-02
cshadow, thanks for the link to ionice! thats a awesome program i never saw before. i'll post an update after i test it out.
changing swapiness didnt help me, i got 4 gigs of ram and an empty swap file. has anyone tried moving systems logs into ram or reduce harddrive io? i was looking into it. i dunno if its worth it, being that i have been having power troubles, and wouldlike my logs on disk asap ;-).

---

### Post by c-shadow on 2009-08-02
> **ridetheteapot said:**
> cshadow, thanks for the link to ionice! thats a awesome program i never saw before. i'll post an update after i test it out.


It' s kinda clumsy to use, having to manually adjust ionice for a process. It would be really nice if the system would do that automagically for long disk operations :)

> 
changing swapiness didnt help me, i got 4 gigs of 
ram and an empty swap file. has anyone tried moving 


It's kinda hard to notice, I also got 4 GB RAM, and have 
2 users always logged on. Mem usage is like this:
```

alen@Amber:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3546       3409        136          0         32       1718
-/+ buffers/cache:       1659       1887
Swap:         2047          5       2042
alen@Amber:~$

```
As you can see, i have only 136MB free! It's nothing bad, system has 1718MB in cache and it releases it when needed (loading new apps).
My system usually starts to swap when I run virtualbox wit 1 or 2 VMs open (about 384or 512 MB per VM).
What is important to know, linux doesn't swap when you are out of RAM. It swaps "unused" portions of apps even earlier. That is a good thing. But, it likes to do that a bit aggresive - you start copying large files around and end up with all your started apps in swap and a HD movie you are copying in cache. Swappines just tries to regulate that aggresiveness. You can try changing vfs_cache_pressure parameter to some lower value and swappiness to 1.

> 
systems logs into ram or reduce harddrive io? i was looking into it. i dunno if its worth it, being that i have been having power troubles, and wouldlike my logs on disk asap ;-).

Don't bother with this, leave logs on disk. If you want to minimize disk io, try mounting the partitions with 'noatime' option (ext3,4,...) partitions, or change the journaling option.

---

### Post by ridetheteapot on 2009-08-02
im getting great results with ionice suppressing rtorrent evil hash check.
still my gripe is nautilus compared to cli for file operation, i dont really have any slowdown when not using naughtylus.

on a side note im not really liking how so many of the packages chosen for ubuntu are in the "just don't bother" category. and as everyone who feels this way knows, there are better alternatives out there. i know its a bitchy complaint, but where is the judgement? or what are the standards?
gstreamer/totem, brasero (before that serpintine),*cough firefox 3*, eog, music player, pulseaudio, i cant even remember all the brokenware that comes with ubuntu.

---

### Post by c-shadow on 2009-08-02
> **ridetheteapot said:**
> im getting great results with ionice suppressing rtorrent evil hash check.

Try ionice-ing rtorrent on startup. Also check out 'nice'. I start a lot of programs with plain 'nice' so starting FF3 doesn't cause frame skipping when watching movies on second screen :)

> 
still my gripe is nautilus compared to cli for file operation, i dont really have any slowdown when not using naughtylus.


Should not happen,are you sure you don't have the same problem with cp from terminal? Never had a problem with nautilus like that. Have you watched cpu/disk usage while nautilus is copying?
Try top, or better, i recommend htop for that.
Don't know how reiserfs works with something like rtorrent. I had big preformance hits on a partition that i used for torrenting when using ext3. With all the twaeking options it was still slow as hell and after a while it got realy fragmented. So fragmented that reading a 7 GB file into /dev/null went at about 10 MB/S! I solved these problems by formating this partition (about 600GB) to xfs (on over 90% full partition fragmentation is now only 4%, and there is A LOT od write/delete). Don't really know about reiser, but maybe it's killing the performance, try something like running this in a terminal while copying (you would need package sysstat for this):

```
 
sudo iostat -m 1

``` 

Now watch the figures for a while: user, nice, system, iowait, steal and idle. If iowait is large (it could go over 90%) it means that kernel is waiting for disks. It could also mean you have a fragmentation problem, or a bad mount option or disk caching is off,...

> 
on a side note im not really liking how so many of the packages chosen for ubuntu are in the "just don't bother" category. and as everyone who feels this way knows, there are better alternatives out there. i know its a bitchy complaint, but where is the judgement? or what are the standards?
gstreamer/totem, brasero (before that serpintine),*cough firefox 3*, eog, music player, pulseaudio, i cant even remember all the brokenware that comes with ubuntu.

Yes, it's a bitchy complaint, I agree partially, but you are OT with this.

---

### Post by ridetheteapot on 2009-08-03
kk thanks for the attention cshadow, im going to try iostat tonight and see whats going on.

i did mean in my previous post that ionice was doing magic for rtorrent. it runs a hash check on completed files that sends disk io through the roof, making multitasking so annoying, but not with it's ionice set nice and high. only thing is im curious to see if there will be side effects writing to disk when i'm downloading fast.

only really mention that complaint cause one of the first recommendations was to stop using nautilus.


____________________________EDIT 7-25-10_____________________________________
I'm going to keep this marked solved; although 1 year later with newer software and different hardware, i still find this to absolutely true. if i am lazy and click and drag too much GB worth of files nautilus makes me pay. it does not happen if i just use mv or cp. (i dont have a clue why it happens for larger amount of space and not smaller ones 300GB operation vs 100 GB operation. 100 GB operation might not see these effects for any amount of time, 300GB operation it happens the whole time)
right now i have a single file operation being preformed by nautilus, 337 GB from one drive to the next - i can not unmount a usb volume while this is going on (times out), i can not use apt-get while this is going on (unpacking a little deb takes forever).

---

