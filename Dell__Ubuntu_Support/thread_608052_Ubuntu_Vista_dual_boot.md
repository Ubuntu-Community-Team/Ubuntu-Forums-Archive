---
title: "Ubuntu Vista dual boot?"
date: 2007-11-09
forum: Dell  Ubuntu Support
---

### Post by Justleftlife on 2007-11-09
I would like to play with Ubuntu. and see what the work of unix/linux is about. But i dont want to wipe my drive and do a fresh install. Can a dual boot set up work with vista and linux? would it even be worth it?


Here are the spec's of my laptop

Dell inspiron E1505
Intel Core Duo @ 1.73ghz
2gig ram
Windows vista home premium 32bit

I would like to put it on the laptop, but if the desktop would be better then maybe the desktop it should be here are the specs on the desk top

Windows XP Pro service pack 2
Intel pentium 4 3.0 ghz 
1 gig ram


I heard from some one that  dual boot between ubuntu and windows would have a problem because the two OS's would fight for the kernal. Making tons problems for me and most likely causeing me to do what i dont want to do, wipe my hard drive. So if this had been done cleanly, i would like to do it as well. thanks in advance. 

-JJL

---

### Post by Fire_Chief on 2007-11-09
See this article [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by RobertGloverJr on 2007-11-09
What I did was to install VMWare Workstation 6.02.  You can use it for 30 days free, after which it costs $189 to purchase.  You can download the version that runs under Windows or you can download the version which runs under Linux.  I use the Linux version; it installed flawlessly into Ubuntu 7.04.  (It is also easy to uninstall Vmware Workstation if you get tired of it).
   It is simple to create a guest machine using Vmware workstation, after which it is easy to install a guest operating system into it.  A couple of days ago I installed WinXp into a guest machine on VMWare which in turn is running under Ubuntu 7.04.   I'm going to make some more guest machines and run Fedora and Sun Solaris.  All 3 will be able to run at the same time and you can switch between them as if they were  applications.
   That seems like a much safer way for you to go than trying to dual boot physically.

---

### Post by rsambuca on 2007-11-09
Dual booting is fine.  Since only one OS is running at a time, there is no "fight for the kernel!?".

I started with an XP/Ubuntu dual boot, and have progressed to having XP, Vista, and five linux distros on my PC.

---

### Post by StefAndrew on 2007-11-09
I used gParted Live CD to shrink my Windows Vista partition down and free up 20 gb free space for my linux partition.  And it's working like a charm.  I edited my boot loader screen so I only have 2 entries and so that Vista is loaded by default, since unfortunately it is what I use the most right now.

---

### Post by rsambuca on 2007-11-09
> **StefAndrew said:**
> I used gParted Live CD to shrink my Windows Vista partition down and free up 20 gb free space for my linux partition.  And it's working like a charm.  I edited my boot loader screen so I only have 2 entries and so that Vista is loaded by default, since unfortunately it is what I use the most right now.

Wow, you are one of the lucky few who have used gParted on Vista and survived!  It isn't the recommended course of action.

---

### Post by Dellfan on 2007-11-09
Dual boot works fine. Make sure that you follow Fire_Chief's recommendation and read the article first.

If you are lucky and have the Nvidia graphics card in your 1505 it will work great. If you have the ATI card, you can get it to work but there is a bit of fiddling required, especially if you want suspend and resume to work.

...currently running 7.10 on a 1505 with Intel 3945 wireless card and Nvidia graphics (the Ubuntu configuration). Works great!

---

### Post by Multi-Booter on 2007-11-09
> **Justleftlife said:**
> I would like to play with Ubuntu. and see what the work of unix/linux is about. But i dont want to wipe my drive and do a fresh install. Can a dual boot set up work with vista and linux? would it even be worth it?


Here are the spec's of my laptop

Dell inspiron E1505
Intel Core Duo @ 1.73ghz
2gig ram
Windows vista home premium 32bit

I would like to put it on the laptop, but if the desktop would be better then maybe the desktop it should be here are the specs on the desk top

Windows XP Pro service pack 2
Intel pentium 4 3.0 ghz 
1 gig ram


I heard from some one that  dual boot between ubuntu and windows would have a problem because the two OS's would fight for the kernal. Making tons problems for me and most likely causeing me to do what i dont want to do, wipe my hard drive. So if this had been done cleanly, i would like to do it as well. thanks in advance. 

-JJL

Here is what I suggest...

If your pentium 4 has hyper threading... where it can run 64-bit... download the Ubuntu or Kubuntu 7.10 **live CD**. Save it somewhere in a folder on your hard drive. Then use your burner software to burn the live CD.

Then simply restart, select to boot from CD.
Soon you will have a choice screen... choose to boot/install.

This will literally BOOT 7.10 in a live mode.
The OS boots and runs live off of the CD... no install required.

You can play with it all you want and see how well you like it and how well it works with your hardware using the "default" hardware drivers. Everything may work perfect... everything may not...

But anyways, play with it off the live CD and see what you think... as this is a no-risk trial.

Report back what you think and we can go from there on dual-booting if you want it hard installed.

:guitar:

---

### Post by StefAndrew on 2007-11-19
> **rsambuca said:**
> Wow, you are one of the lucky few who have used gParted on Vista and survived!  It isn't the recommended course of action.

It took a few hours to complete, but I just let it do it's thing and didn't have any problems whatsoever.  I backed up everything I needed to just in case I did have issues, but it worked out fine.

---

