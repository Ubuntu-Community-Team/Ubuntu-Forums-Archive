---
title: "Going to Fedora Core 3 for a while..."
date: 2004-11-29
forum: Fedora/RedHat and derivatives
---

### Post by jdong on 2004-11-29
I am sad to say that on my primary desktop, I am wiping all the partitions and switching to Fedora Core 3...

The main reason lies in SELinux support, but lots of tiny things prompted the move, too.

Last week, I took advantage of Best Buy sales to upgrade my 1GHz server box with extra RAM and a huge hard drive, and loaded XP onto it to play with embedded motor control. I placed a D-Link Wifi-G router in its place (also cheap sale). As a result, the apache/php testbed that I was running on my server now has to run on my desktop.

I feel pretty paranoid with running public services without good lockdown. I experimented heavily with SELinux around July 2004, and found it quite effective at placing barriers and preventing major damage with PHP exec() compromises.

As a result, my desktop has migrated to FC3 for now. Perhaps I'll switch back to Ubuntu tomorrow if I can't survive in FC3!

Needless to say, I'm still gonna help people out here just like before -- after all, I still have 3 workstations @ school that are going to remain Ubuntu indefinitely.



--John Dong

---

### Post by jdodson on 2004-11-29
interesting.  let us know what you think if you decide to not switch back.  i would be interested in speed/stability/package management, etc.

---

### Post by jdong on 2004-11-29
Ok, just finished initial install. I definitely like the Fedora Bluecurve look-and-feel. In addition, I see that RedHat patched slick GNOME fileselectors into firefox. Slick!

I'm noticing disk IO slowdowns under high loads... I suspect this is a problem with the default kernel. I'm compiling a new kernel -- 2.6.9 vanilla + ACPI + swsusp2 + selected CK patches (mostly mapped watermark/swappiness patches).

Currently yum updating... I chose KDE: without Ubuntu, I'm still heavily KDE at heart.


Will be back with more extensive tests later.

---

### Post by poofyhairguy on 2004-11-29
[QUOTE=jdong]I am sad to say that on my primary desktop, I am wiping all the partitions and switching to Fedora Core 3...

The main reason lies in SELinux support, but lots of tiny things prompted the move, too.

Last week, I took advantage of Best Buy sales to upgrade my 1GHz server box with extra RAM and a huge hard drive, and loaded XP onto it to play with embedded motor control. I placed a D-Link Wifi-G router in its place (also cheap sale). As a result, the apache/php testbed that I was running on my server now has to run on my desktop.

I feel pretty paranoid with running public services without good lockdown. I experimented heavily with SELinux around July 2004, and found it quite effective at placing barriers and preventing major damage with PHP exec() compromises.

As a result, my desktop has migrated to FC3 for now. Perhaps I'll switch back to Ubuntu tomorrow if I can't survive in FC3!

Needless to say, I'm still gonna help people out here just like before -- after all, I still have 3 workstations @ school that are going to remain Ubuntu indefinitely.



--John Dong[/QUOTE]

Thats cool. I went the other way. After you open synaptic and see 14000 packages, no less will do!

---

### Post by knappen on 2004-11-29
jdong

Thanks for all the good support you have given to the Ubuntu community. I really hope you will come back soon!

---

### Post by jdodson on 2004-11-29
[QUOTE=knappen]jdong

Thanks for all the good support you have given to the Ubuntu community. I really hope you will come back soon![/QUOTE]

i dont think he is leaving..... just changing his desktop OS.i

---

### Post by knappen on 2004-11-29
Perfect!

---

### Post by jdong on 2004-11-29
[QUOTE=knappen]jdong

Thanks for all the good support you have given to the Ubuntu community. I really hope you will come back soon![/QUOTE]

Come on you guys! I still have Ubuntu installed on over half my computers! Just my main computer, I'd like to give Fedora Core a full blown jdong test before I bash it again... I like to be an informed basher  :p 

On the continuation of my previous post, I got the new kernel all working... SELinux is screaming at me for no reason -- time to start tweaking!


Speed-wise, Fedora Core feels horribly slower than any other distro... Especially under high CPU loads -- even with a preemptible -ck kernel, FC is just simply lagging when I compile stuff.

Bottom line: **I'm switching back now**. Screw this. Redhat is using all of us as testing subjects with Fedora...

Starting to download Hoary images....

---

### Post by knappen on 2004-11-29
If I say welcome back, someone will say that jdong never left :-)

Anyway, switching back was a good choice.

---

### Post by poofyhairguy on 2004-11-29
[QUOTE=jdong]


Starting to download Hoary images....[/QUOTE]

lol

---

### Post by TravisNewman on 2004-11-29
Has anyone ever got SELinux working in Ubuntu or Debian? I've been curious, and I see a few packages in apt-cache, but wouldn't know where to start really.

But I agree jdong. Fedora is just a pain.

---

### Post by jdong on 2004-11-29
I guess my next big project will be to rip SELinux Targeted Policies from Fedora.

My last venture with Yast2 failed miserably!

---

### Post by adbak on 2004-11-29
[QUOTE=jdong]
Bottom line: **I'm switching back now**. Screw this. Redhat is using all of us as testing subjects with Fedora...

Starting to download Hoary images....[/QUOTE]

Yay!  This story has a happy ending after all.

And jdong lived happily ever after....

---

### Post by jdong on 2004-11-29
Lol, at the end, I decided to go Warty... I don't want my primary desktop on a bleeding edge development distro -- I'll go easy and stay on the stable branch!

Oh yeah, me and spazzing out to try other distros... don't worry about it... I tend to do that excessively... I can boast that I've used all top 30 Distrowatch.org listed distros, and more!

---

### Post by zenwhen on 2004-11-29
I'm glad you stuck with us. I think you made a good decision picking Warty, too. It is rock solid.

---

### Post by HungSquirrel on 2004-11-29
[QUOTE=jdong]Lol, at the end, I decided to go Warty... I don't want my primary desktop on a bleeding edge development distro -- I'll go easy and stay on the stable branch!

Oh yeah, me and spazzing out to try other distros... don't worry about it... I tend to do that excessively... I can boast that I've used all top 30 Distrowatch.org listed distros, and more![/QUOTE]
 Glad to know I'm not the only distro junkie around!

---

### Post by jdodson on 2004-11-30
[QUOTE=HungSquirrel]Glad to know I'm not the only distro junkie around![/QUOTE]

your not, i downloaded fc3 a few days after its release.  i also have mandrake 10.1 and the latest gentoo.  i just dont have as much time as i used to to test distros anymore.  plus warty works great, it would be a waste to undo all that tweaking.  

i will someday test the latest core, as far as i am concerned they only have one place to go from fc2 and that is up.  however peoples expieriences i have read about, not sure that is true.

---

### Post by arctic on 2004-11-30
hehehe...
i am going the other way round. i will erase my last fc3 and gentoo partitions soon and have ubuntu only on all of my boxes. no need for something different in my case.  :)

---

### Post by wallijonn on 2004-11-30
Jong,

Have you upgraded Warty's kernel to 2.6.9? That's the only way I can see Security Enhanced Linux being integrated into Warty or Hoardy.

I do notice that SPM has checkpolicy, libselinux1, libselinux-dev, policycoreutils, selinux-policy-default, libpam, sysvinit and util-linux. So all you would need would be to patch in slat, vixie-cron, libselpol, etc.  [http://www.nsa.gov/selinux/code/download5.cfm](http://www.nsa.gov/selinux/code/download5.cfm) You'd probably have to hack the PATHs in the complete kernel but you would end up doing all the work in the SPM packages.

I wonder if Hoary has all the rest of the necessary libs?, since it is based on 2.6.9. 

I know that you must've tried OpenBSD, FreeBSD...

The way you feel about FC3 is how I felt about FC1 after being happy with RH9. Had RH continued support for Red Hat 9 I would never had found Ubuntu. 

Sounds like you'd need a dual boot Ubuntu, one for production and one for test. I had a dual Warty / Hoary and ended up just using Warty. It just seemed as too much work when I was perfectly happy with Warty.

---

### Post by jdodson on 2004-11-30
its not hoardy, its hoary. :)

---

### Post by jdong on 2004-11-30
I think I'll actually research UserMode Linux, and do testing inside there.

Yes, I do use the latest official kernel, plus patches I can't live without (like swsusp2)

---

### Post by piedamaro on 2004-11-30
Not that I'm very much into selinux, but after fc3 install I had to disable it totally, it won't let me create any new user (no permission on /etc/password). Even with their permissive policy.
Also, the kernel on Fedora is really slow with pentium4 (there is a bug opened), and in general has very slow syscalls beacause of exec-shield.

---

### Post by jdong on 2004-11-30
Hmm, since Athlon64's are fully compatible with -march=pentium4 optimization, there might be a problem in that case, too!


But even with my own kernel -- virtually the same one I'm using on Ubuntu now, I still get AWFUL disk performance in FC3.

---

### Post by costoa on 2004-11-30
Trader! Trader! Just kidding. =)

You running different distros brings up one of the great strengths of GNU/Linux which is diversity (aka "hybrid vigor" if you may) . No one distro is the "best". Fedora is an excellent distro. For two years I ran RH Linux and liked it (even paid for RHN which was a good deal). If RH hadn't killed it off for RH Enterprise WS I might still be there (since, for me, there was no big reason to try another distro).

Gentoo was my next one which is also quite good. It reminds me of owning an old VW bug, lots of tweaking but when it runs right it runs very well. I enjoyed that but didn't have the time to play with it so I looked for something else and found Ubuntu. It runs great from the start with little adjustment. A first class distro and is what I use for my personal/work machines. It's also what I recommend 95% of the time for use on a workstation. I still use Gentoo on our servers but might change some day. Off topic but next year I'll have the company almost Microsoft free (still need one Win2k server with terminal services for the Accounting staff). Ubuntu will be replacing XP.

For the last few months or so my boss has been trying to get a contract to supply a couple of call centers (inbound reservation center, about 60 seats per site) with new workstations and a support contract. They only have two applications that the users need to access and I'll most likely use a customized version of Gentoo. The contract also includes about 10 seats for "general" office type workstations and I'll use Ubuntu for those. Ubuntu is just too much (meaning I'd have to strip away most of it) for the call center seats and Gentoo is too much of a hassle to set up and maintain for the office staff. Not to mention Ubuntu is, IMO, much more user friendly.

People need to understand that jdong's switch is not because of a weakness in Ubuntu but a strength in Fedora. No one distro will, and shouldn't, fit everyone. jdong is smart enough to realize that. That's why he's still running Ubuntu on other boxes.

It's fun to trash talk other distros but in the end it should just be in jest. All the other distros* do, to some extent, work together.

*Except OpenLinux by Caldera (aka SCO). I would touch that thing with a 3m cattle prod. =)

---

### Post by jdong on 2004-12-01
Guess what.... **I'm running Fedora again!**

It occured to me (in a dream last night) that perhaps undoing exec-shield and doing normal prelinking would improve performance.


So here I am, testing my hypothesis...

---

### Post by TravisNewman on 2004-12-01
*L* It actually occurred to you in a dream? I guess that doesn't seem to weird, but it's one of those things you hear about all the time that just never seem to happen.

Ah well, let us know how it goes :)

---

### Post by jdong on 2004-12-01
It's worse when I realize in a dream that I left out a negative sign on # 16 (a) on a math test I took the day before -- and there's 7 parts! ouch, there's a sleepless night

---

### Post by jdong on 2004-12-01
Oh yeah, **yum is a piece of crap**.... Apt4rpm is hundreds of times faster and more efficient!

---

### Post by TravisNewman on 2004-12-01
[QUOTE=jdong]Oh yeah, **yum is a piece of crap**.... Apt4rpm is hundreds of times faster and more efficient![/QUOTE]
 preaching to the choir there buddy. One of the main reasons I decided to switch away from RH based distros. That was before I knew about apt4rpm, but I don't regret it.

---

### Post by jdong on 2004-12-02
heh, once again, back to Hoary fun.


Trying  to rip SELinux from Fedora, though!

---

### Post by gabbman on 2004-12-02
The ONLY thing I found that FC-3 did really well, was install my HP-PSC1210 printer through my network connection, and the printer is running off my wifes laptop using XP.  No muss, no fuss, just a few clicks and it worked.

Why is it the women get all the new toys, and we are left to tweak for ourselves.??
:D

---

### Post by piedamaro on 2004-12-03
[QUOTE=jdong]
Trying  to rip SELinux from Fedora, though![/QUOTE]
Me too, but I have found that I have to throw away all of their ~60 kernel patches, and reconfiguring the beast from scratch.
I still I have a vfs panic at boot time. I have a serial ata chip, and yes I've compiled serial ata support and ICH5 support (my chip) built in into the kernel as well as filessytem support.
I keep trying, but I'm starting to think that there are issues with selinux enabled libc or something, so if I strip their kernel patches I can't boot. Who knows :P

---

### Post by mikeymike on 2004-12-03
isnt SELINUX in FC3 have a few bugs 

im still usin FC3 but once i figure out how to use this distrib unbuntu without needing to keep lookin stuff up it can become default

---

