---
title: "How does sidux compare to ubuntu interms of speed?"
date: 2008-03-05
forum: Debian
---

### Post by kpkeerthi on 2008-03-05
How does sidux compare to ubuntu interms of speed? I mean general boot time, application load time and the overall snappiness... and nothing else. Anyone who used ubuntu and sidux on the same hardware please chime in.

---

### Post by jeffus_il on 2008-03-05
No idea, it's Debian sid as far as speed goes, there has been no movement on their site since Christmas, Maybe they didn't wake up yet after the New Years party... Is that good enough for you?

---

### Post by kpkeerthi on 2008-03-05
LOL!... OK... so i take that as 'it is only as fast as ubuntu/debian is'..

---

### Post by Changturkey on 2008-03-05
It is fast, not as fast as Arch or Gentoo, but fast enough.

---

### Post by ZBREAKER on 2008-03-05
It is indeed fast...a bit snappier I'll feel than Ubuntu. Be advised though it is not as easy to run/maintain as Ubuntu imho and you should be at an intermediate level of understanding with linux before you make it a permanent addition to your computing.

---

### Post by Hallvor on 2008-03-05
> **kpkeerthi said:**
> How does sidux compare to ubuntu interms of speed? I mean general boot time, application load time and the overall snappiness... and nothing else. Anyone who used ubuntu and sidux on the same hardware please chime in.

Sidux is simply much faster. It also uses far less memory.

Boot time on my computer (AMD Athlon 2500+ XP, 1024 MB RAM) from Grub:

Ubuntu: about 60 seconds (Xubuntu is a little faster, but not as fast as Sidux.)
Sidux: about 40 seconds.

---

### Post by jeffus_il on 2008-03-05
How do you measure Sidux's speed and memory usage compared to Ubuntu?

---

### Post by Hallvor on 2008-03-05
> **jeffus_il said:**
> How do you measure Sidux's speed and memory usage compared to Ubuntu?

Bootup time is much faster. About 20 seconds differ on my computer. When it comes to regular use, it is subjective on my part, but Sidux feels faster and should compare to Debian. (It is really Debian Sid on a live cd with a few extra scripts. It even uses the same repositories.)

I ran htop after reboot once, and the memory in use was about 70 MB. And if you stick with KDE applications, the shared memory on the libraries will keep memory usage very low. Even Xubuntu is heavier.

Having said that, it is a distro better suited for intermediate users - pretty much like Debian. :)

---

### Post by kpkeerthi on 2008-03-06
Thanks for your replies guys.

---

### Post by Antman on 2008-03-06
+ 1 for Sidux as far as speed goes. But as I test the various Ubuntu 8.04 LTS daily snapshots I am getting more impressed with Ubuntu's speed.

For an Alpha product, it is pretty damn snappy on my laptop. It goes from grub to logon screen in 34 secs, and all the apps launch quickly.

Sidux is still my main OS, but Ubuntu 8.04 LTS will no doubt earn a spot on one of my laptops if it keeps up the good work (and supports suspend properly).

---

### Post by K.Mandla on 2008-03-06
Moved to Debian-based distributions subforum.

---

### Post by dptxp on 2008-03-07
sidux installs in 10 minutes where Ubuntu takes 35.
But Gnome is not supported.
sidux is not for beginners, you need some experience.
You use more CLI in sidux.
It is much closer to Debian than Ubuntu and runs well with good hardware detection.

You can try the Lite version- 450 MB, no openoffice or Gimp. Should
install in 5-7 minutes.

---

### Post by Antman on 2008-03-07
Best thing to do is just to try Sidux. If you are used to Debian, then you will simply love Sidux. :guitar:

I use it on my USB Flash as a LiveCD (fromiso) with persistance, my sub notebook, and my desktop.

My USBFlash fromiso install is great when I need to boot or install Sidux quickly on a device (installs in about 3.5 minutes). I have my "extra" stuff installed (packages, codecs, various wifi firmware, etc) so I can boot from various pc setups and have access to all my stuff.

At any rate, try Sidux. You WILL love it.

---

### Post by markharding557 on 2008-03-14
sidux is debian sid with some added scripts and other bits therefore its speed is the same as debian sid which is without doubt faster than ubuntu which has many things running to aid ease of use.

---

### Post by Oldster on 2008-03-14
I came from Sidux to Ubuntu. It is definitely more responsive than Gutsy. I left because the maintenance became a nightmare with things breaking. I couldn't get adequate help from the small Sidux community. Not enough experts to go around, I guess.

I'm willing to sacrifice a little performance for stability.

Just my 2 cents. :)

---

### Post by justaguynpc on 2008-03-15
I ran ubuntu since it's first release, and found myself leaving ubuntu with the release of 7.04 to try debian.  I lasted about a week on stable, then installed testing.  I now use testing as my "stable" install, and have sidux residing on its own drive.

I have only has sidux installed to hd for about 3 weeks, and I think it is the best distro I have tried to date.  I started with rh 8.0 "in-the-day."  

So, yea, sidux IS faster, and alot more challenging than ubuntu, if you are into that sort of thing.  =)

Cheers

---

### Post by greymongrey on 2008-03-17
sidux is a lot faster than Ubuntu, but it's not for everyone. It's based on Debian unstable and you will break your system if you aren't careful. For example, a dist-upgrade this past week would have removed about half of KDE. When it gets like that you wait for things to settle down. That said, I've been running sidux as my main OS for months without any problems.

---

### Post by dptxp on 2008-03-22
Can not say for other distros now, but I shall always have both Ubuntu and sidux on my laptop, installed.

Using sidux is like living on the edge, driving a new, fast, test car.

Obviously a PuppyLinux CD by my side (And maybe Knoppix too).

---

### Post by deepclutch on 2008-03-23
unfortunately,sidux is default with kde :( 
But these days Gnome is pretty much fastly hitting Sid repositories.for eg:Gnome-2.22 :D
thats why I am on Debian Sid ;)

---

### Post by dptxp on 2008-03-27
> **deepclutch said:**
> unfortunately,sidux is default with kde :( 
But these days Gnome is pretty much fastly hitting Sid repositories.for eg:Gnome-2.22 :D
thats why I am on Debian Sid ;)

Gnome in sidux is not officially supported, they do not have the man power, but you can use Gnome. The French use Gnome

---

### Post by deepclutch on 2008-03-27
Mepis is a good Debian distro(I'll say n00bs should try mepis!rather than kubuntu~for kde).It is fast!

---

### Post by keratos on 2008-03-27
my 2 pennies worth...

I've spent 18 years installing *nix and linux systems for clients such as Baesystems, Ferranti, Marconi, ICL, and the BBC to name but a few.

"Speed", responsiveness... its not that simple I'm afraid.

First off we should consider the CPU, available RAM and chipset in use, and whether one intends to run a 64 bit OS or a 32bit OS and of those two, what aspirational optimisations we expect or are satisfied with. For example, taking the desktop experience as a whole, there is some evidence that challenges certain claims relating to 64bit performance however, there is also evidence that supports 64bit performance. The debate has not finished yet and thank god it is out of scope for this post.

Then there is the O/S. When one looks at linux, one can easily identify a plethora of distributions build around a multitude of kernels where such kernels are optimised for specific architectures or flavours. The combination is bewildering. 

In the hardware (h/w), there exists different h/w capabilities in terms of the different levels of support via an O/S and associated driver/firmware interface. The experience cab be different depending on the quality of drivers.

Dont forget kernel optimisations. Some distributions go to great pains to optimise their kernel builds. I personally have experienced significant performance increases by tweaking what is usually "stock" kernels, through optimisation of a number of settings, not least in the way the CPU is managed:
clock HZ (CONFIG_NO_HZ)
scheduling (CONFIG_IO_SCHED)
preempting model (CONFIG_PREEMPT_xxx)
tickless (CONFIG_TICK_ONESHOT)
forcing 32bit on x64 amd (CONFIG_K7)
..and so on so forth.

Notwithstanding, distributions can and do perform some of the optimisations for you HOWEVER, this will never be at the maximum you can extract/yield in light of the fact they have to provide a "generic" capability to some degree. Specialising in specific machines/configurations would., naturally limit their development and progression.

People will talk about benchmarks on this and benchmarks on that, but I have yet to see concise scientific evidence reported through an impartial and objective panel that identifies one O/S as "faster" over another.

The one satisfaction that one can take, you can take, is that linux is FREE so install them all, give them a try, and make your own, your OWN informed decision.

For me, it would be possible without wishing to come across  arrogant, to make Mandrake run as fast as Gentoo, or Gentoo run as slow as Mandrake (accepting of course that Gentoo is "fast" and "mandrake" is slow - my perception only and may not reflect the views of others).

At the end of the day, try them all and make your own decision. It wont cost you a penny/cent !!!

---

