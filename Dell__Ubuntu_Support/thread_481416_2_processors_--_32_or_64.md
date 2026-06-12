---
title: "2 processors -- 32 or 64"
date: 2007-06-22
forum: Dell  Ubuntu Support
---

### Post by FiReSTaRT on 2007-06-22
I just picked up a Dell Precision 450 with two 2.4GHz CPU's. Should  I be installing the 32bit or the 64bit kernel for it?

---

### Post by fjgaude on 2007-06-22
Either will automatically recognize the two processors. As for the 64-bit, if you need Adobe Flash for online movies and the like, forget it. Go with the 32-bit version.

frank

---

### Post by Motoxrdude on 2007-06-22
Are you sure it's two CPUs or dual core? Dual core and two CPUs are completely different.
What processor(s) is it btw?

---

### Post by FiReSTaRT on 2007-06-22
It's running 2 Xeons. My coleague is saying that 2x32 doesn't equal 64 in this case and that I should be using a 32bit OS. I guess tht answers it unless there's a voice of dissent?

P.S. That's what I get for having the same machine (other than running through a casing, 2 power supplies and a few drives) since 2001 lol

---

### Post by apel_2804 on 2007-06-22
isnt it indifferent how many cpus are realy inside?

---

### Post by Motoxrdude on 2007-06-22
Yeah, two 32bit processors don't make a 64bit one ;)
O well, 64bit is not noticably faster from my experience.

---

### Post by apel_2804 on 2007-06-22
yes I know that two 32bit cpus don't make a 64bit one. but i think that these xeons are 64bit extended so its indifferent which os is installed.

---

### Post by Motoxrdude on 2007-06-22
Yeah, go ahead and try out both. The main thing will 64bit ubuntu (as with every 64bit OS) is that flash will not work without some hacking (not illegal hacking, just requires some workarounds)

---

### Post by FiReSTaRT on 2007-06-22
Thank you gentlemen. I will be downloading the 64bit version and trying it out as well... How much of a hassle are those work-arounds?

---

### Post by Kilz on 2007-06-22
> **Motoxrdude said:**
> Yeah, go ahead and try out both. The main thing will 64bit ubuntu (as with every 64bit OS) is that flash will not work without some hacking (not illegal hacking, just requires some workarounds)

Please dont spread the Flash FUD. Nspluginwrapper makes Flash work quite well with the 64bit browser already installed. 10 seconds, and a click or 2 will have it up and running.

---

### Post by FiReSTaRT on 2007-06-22
Has anyone tried running Opera w/ flash on Ubuntu?

---

### Post by avik on 2007-06-22
> Has anyone tried running Opera w/ flash on Ubuntu?

Yeah, I got it working.  I used [this guide]("http://ubuntuforums.org/showthread.php?t=413040").

---

### Post by Motoxrdude on 2007-06-22
> **Kilz said:**
> Please dont spread the Flash FUD. Nspluginwrapper makes Flash work quite well with the 64bit browser already installed. 10 seconds, and a click or 2 will have it up and running.

All i said that it takes some workarounds, which as you shown it does.

---

### Post by Kilz on 2007-06-22
> **Motoxrdude said:**
> All i said that it takes some workarounds, which as you shown it does.

No work arounds, nspluginwrapper isnt a work around, its an application. Ten seconds, one install script, click click its done. 
A work around would be hacking in 32bit Firefox , 32bit flash, libs, a startup script. But that hasnt been needed since Dapper.

---

### Post by FiReSTaRT on 2007-06-23
Thanks for the link. The comp came with a mildly dirty install of XP, so I'll set it up like I had it before, run PM and do dual boot with 7.04 as default. This buys me some leisure time with setting up my system.

---

### Post by Tethtibis on 2007-06-26
as far as I'm aware, dell does not sell dual cpu desktop or laptop computers, just dual cores. there is a difference, dual cpu has two processors, whereas dualcores are two processors on top of eachother, both sharing the same cache and data busses. so naturally dual cpu systems will run faster, that's why they make em servers. :OP

---

### Post by Tethtibis on 2007-06-26
oh, and dual cores are generally 32 bit, it would tell you 64 bit on a sticker on the case usually, "they're proud of the neww 64 bit architecture" even though it's still buggy.

---

### Post by rkevans on 2007-10-27
> **Tethtibis said:**
>  as far as I'm aware, dell does not sell dual CPU desktop or laptop computers, just dual cores. there is a difference, dual cpu has two processors, whereas dual-cores are two processors on top of each other, both sharing the same cache and data buses. so naturally dual CPU systems will run faster, that's why they make em servers. :OP

You're not looking very hard.  Dell Precision 490/690 has two sockets and is available with quad-core processors in each socket.  So, 8 cores in a desktop/workstation package.  

Rick
Who is typing this on an obsolete Dell Precision 470, Dual Xeons, 22,300 BogoMips, on my desktop.  Upgradeable to a pair of dual-core Xeons (P4 arch) -- if I had a briefcase full of unmarked bills.

---

