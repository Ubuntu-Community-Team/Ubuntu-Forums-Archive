---
title: "tweaks for linux gamers"
date: 2009-01-19
forum: Gaming &amp; Leisure
---

### Post by v1nsai on 2009-01-19
I've recently converted to linux, and I have seen the top of the mountain, and it is good, but the one thing that windows seems to beat us in is video performance.

That being said, I found in [this]("http://www.linuxquestions.org/questions/linux-games-33/best-linux-distro-for-gaming-pc-429938/") thread a link to the [con kolivas]("http://members.optusnet.com.au/ckolivas/kernel/") kernel patch, which affects the scheduler and the amount of memory given to any given app, however the patch is for an earlier version of the kernel and all I know about this patch is the name con kolivas, which a google search only yields the name of the guy who wrote the patch and stuff about him which doesn't help me :) .

Would it be safe to apply this patch to my system and test it out?  It seems like it could make a BIG difference in power hungry apps that need a little extra juice.

---

### Post by hikaricore on 2009-01-19
To apply the patch you'd have to recompile your system kernel.
That patch is from 2007 (quite ancient) and I doubt it would be of any use or even compatible.

As far as video performance I've never had trouble using decent hardware.

Might I ask what hardware and drivers you're using?

---

### Post by linuxguymarshall on 2009-01-19
v1nsai, I believe you misunderstand the difference between software and hardware performance. Your hardware functions just as it does on Windows however the software you run it with may be slower. Take for example this : 

If I run the Windows version of DOOM 3 on Linux via Wine then it will be slow. If I run the Linux client then I get maximum FPS. One is made for linux. The other is not. 'nuff said

---

### Post by v1nsai on 2009-01-19
I'm using an nvidia geforce 6600 with 2gb ram and an amd dual core 2.4ghz processor.  I suffer bad framerates just watching videos in full screen, runs beautifully on my windows partition.  Not that I'm thinking about switching back, but I've definitely noticed a drop in performance on linux.

But anyway, I figured I wouldn't be able to use the scheduler tweak, it was worth a shot though.  I do understand the difference between hardware and software performance, I switched to linux as a platform for writing programs to enjoy the beauty of open source so I haven't done much gaming, it wasn't my purpose anyway.

---

### Post by hikaricore on 2009-01-20
Which driver version are you using for your card?
The 177.xx series is probably the most stable, the 180.xx series has its place but is seriously buggy on most systems.

What resolution are the videos in?
The 6600 is NOT a powerful card and my studder when trying to play 720p or 1080p.

Which video player are you using?
Some players such as mplayer need to be configured properly for performance.

Are you using Ubuntu or Kubuntu?
While running KDE4 or using desktop effects under gnome your video playback performance my suffer.


A few of these items obviously will have an effect on gaming as well as video playback, so make sure everything is properly configured.

---

### Post by donkyhotay on 2009-01-20
Another question is what type of videos are you watching? If it's youtube I've found that the flash player for linux doesn't seem quite as robust as it's windows counterparts.



//edit: oops, someone beat me to the question. (c:

---

### Post by linuxisevolution on 2009-01-20
> **donkyhotay said:**
> Another question is what type of videos are you watching? If it's youtube I've found that the flash player for linux doesn't seem quite as robust as it's windows counterparts.



//edit: oops, someone beat me to the question. (c:


Flash seems to run better in Fluxbox. I was running Xubuntu with XFCE on my sisters Pentium 3 1ghz 8mb video ram, and it was fast, but flash games sucked ( that's all she does on the computer ). So I replaced Xfce with Fluxbox and she loves it :)

---

### Post by donkyhotay on 2009-01-20
Sounds like a good tip for any other gnome users like me. Course I don't care about the speed of flash videos so I don't worry about it.

---

### Post by v1nsai on 2009-01-21
Thanks for the tips, I'm having a nightmare of a time with the 180 driver from nvidia right now actually, luckily I had a 2gb fedora partition that I made just to play with ;) .  I'll try downgrading tomorrow, it's late but that's a good tip.  Didn't mean for this to become a support thread lol.

Also I wouldn't try that tweak donky, it's for an earlier kernel (unless your running that kernel version) and will most likely give you a headache.

---

### Post by v1nsai on 2009-01-21
Thanks for the tips, I'm having a nightmare of a time with the 180 driver from nvidia right now actually, luckily I had a 2gb fedora partition that I made just to play with ;) .  I'll try downgrading tomorrow, it's late now but that's a good tip.  Didn't mean for this to become a support thread lol.

Also I wouldn't try that tweak donky, it's for an earlier kernel and will most likely give you a headache.

---

