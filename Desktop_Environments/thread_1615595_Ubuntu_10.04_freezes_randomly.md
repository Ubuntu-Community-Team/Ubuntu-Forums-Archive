---
title: "Ubuntu 10.04 freezes randomly"
date: 2010-11-07
forum: Desktop Environments
---

### Post by AGue on 2010-11-07
Hey..

I have been using ubuntu 10.04 since around May, June. 
During last month it started to freeze randomly, either right after boot, or at no particular moment, some other times while searching for wireless network, or when just idling.. I don't remember this happening after any particular system change aswell.

I have little linux knowledge, for all i know there could be something on kernel log ($dmesg) but after booting up again (after system freezing) that log is filled up with boot-info so i can't really check anything.

System info:
OS: Ubuntu 10.04 (almost clean. no compiz installed)
RAM: 3GB 
Graphics: ATI Mobility Radeon HD 4650
CPU: Intel core i3 M 330  @ 2.13GHz

May i get some help in here please? Thanks in advance!

---

### Post by mziskandar on 2010-11-07
Try disable the apic. (noapic)
how-to: [http://digitalspine.blogspot.com/2010/11/ubuntu-lucid-1004-freezeslock-ups.html]("http://digitalspine.blogspot.com/2010/11/ubuntu-lucid-1004-freezeslock-ups.html")

Let me know the result either its working for you.

Thanks.

---

### Post by AGue on 2010-11-07
I followed that guide and let the computer idling (not working on it now) for about an hour already since then. So far so good, didn't freeze :P

I'll still reply here either it works or not, during the week.
I notice this disables hyper-threading in cpu. Do new versions (10.10... and next ones, if known) have this issue with hyper-threading? Disabling hardware functionality is not an elegant solution, although i won't need it in the near future so i won't complain :)

Thank you for the quick answer, mziskandar!

---

### Post by mziskandar on 2010-11-07
Try "nolapic" instead of "noapic". Lets see how it goes..

---

### Post by AGue on 2010-11-08
The "noapic" seems to have solved the issue, but if i'm wrong about that i'll keep in mind to try "nolapic" instead, if it'll still freeze.
I don't think the difference between noapic and nolapic would affect me (as long as the OS won't freeze of course) even though i don't fully understand those. 

Thank you again !

---

### Post by AGue on 2010-11-10
Mmm. It froze today. Twice x.x I'll try the nolapic solution instead, tomorrow:)

---

### Post by eeyoreinthesky on 2010-11-15
I'm curious to know if the nolapic worked.  I am having the same problem.  I tried re-installing and that worked for a little while.  But then while booting it will stop and have a page of what looks like kernel programming that almost always ends with child_rip.  I messed around and am able to use my computer with the live CD but I have to select the boot option: nolapic.  

My system:  Core i3 530  -  Asus P7P55D-E Pro  -  PNY Geforce 9800 GTX+  -  WD6401AALS Black Caviar  -  OCZ Gold 2x2GB  DDR3 SDRAM  -  OCZ StealthXstream II 600W

---

### Post by AGue on 2010-11-15
Yes, so far the nolapic solution has been working. Hope it does for both of us:P

---

### Post by deconstrained on 2010-11-16
YESSSSSSS!!!! Now I know where to put kernel parameters. 

10.10 was locking up during heavy CPU usage and I/O, but I gave it nolapic and enabled hyperthreading with ht=on and now I'm heavily loading all four cores and simultaneously doing an rsync back up of my music collection, and so far it's all been smooth sailing.

---

### Post by eeyoreinthesky on 2010-11-16
how did you do nolapic?  i'm guessing you made it a boot parameter but I can't figure out how to do that in GRUB2 or BIOS.  I seriously use Ubuntu because I'm not a computer person.  I like to set it and forget it.

---

### Post by deconstrained on 2010-11-16
^Actually, I spoke too soon. I walked away leaving it burdened and returned to a locked-up system.

Also, I did a little more research/poking-around and discovered that noapic/nolapic cause a disabling of SMP - if that's not it, then what I did discover to my chagrin is that when I looked in /proc/cpuinfo (and in System Monitor) only one cpu core was detected/active.

Here's [a nice page on kernel parameters I found](http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php).

[s]I've since stripped the kernel parameters back down to 'quiet splash ht=on', re-run update-grub, rebooted and subjected it to similar loads, and it pulled through just fine. I'll just have to wait and see if it's finally been "cured" of its freezy-locky behavior.[/s] **[color=red]OH THE IRONY[/color]** - I was just about to hit "Post", the cpu almost completely idle, and it froze. Thanks to the Lazarus form recovery plugin I can now share this hilarity with you.

---

### Post by eeyoreinthesky on 2010-11-16
This is frustrating me too.  Ubuntu runs fine with the Live CD.  I haven't had that freeze yet.  And I also noticed that in system monitor only one core is recognized.  Is there maybe another kernel that is more stable or does it have to do with hardware?

---

### Post by AGue on 2010-11-17
> **eeyoreinthesky said:**
> how did you do nolapic?  i'm guessing you made it a boot parameter but I can't figure out how to do that in GRUB2 or BIOS.  I seriously use Ubuntu because I'm not a computer person.  I like to set it and forget it.

I followed the [how-to]("http://digitalspine.blogspot.com/2010/11/ubuntu-lucid-1004-freezeslock-ups.html") provided by the user [mziskandar]("http://ubuntuforums.org/member.php?u=387056"), and typed "nolapic" instead "noapic". 

(..)
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=red]noapic[/COLOR]"
replaced by
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=red]nolapic[/COLOR]"
(..)

However, as i mentioned previously already, I'm not using the computer that often to be sure it's working for sure even though it seems so, for now..

---

### Post by stevedes on 2011-03-10
I tried noapic, and so far so good,

Crashes have been getting far too common these past few weeks, even though nothing significant has changed on my system.....

---

### Post by AGue on 2011-05-06
Not sure if it's a good idea to revive an old thread but i'm passing by  to say i've been using the OS more than usual the past couple months and  indeed i never had another crash since last i mentioned earlier in this  thread.

Thanks again to mziskandar for his help :)

---

