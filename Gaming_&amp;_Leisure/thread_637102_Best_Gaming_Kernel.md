---
title: "Best Gaming Kernel"
date: 2007-12-10
forum: Gaming &amp; Leisure
---

### Post by horizonbreakk on 2007-12-10
Im somewhat new at the gaming scene in linux. So far I have managed to get Half life2 and steam running great under wine doors and wine, but I was wondering which is the best kernel image to use for gaming? Rt or Server? any help would be greatly appreciated:)

---

### Post by matthewcraig on 2007-12-10
I heard Half Life 2 and Steam run really well under the Windows XP kernel... These are games that only support Windows, right?
A question about running Quake Wars, which supports Linux kernels, might be more applicable.

---

### Post by Vadi on 2007-12-10
Can you really compile your kernel for noticable performance gains? Isn't it all in the video card?

---

### Post by cogadh on 2007-12-10
A video card which only runs because of support either compiled into or built as a module for the kernel.

Yes, you can build a custom kernel that may improve your gaming performance, but only because you can customize the kernel for your specific system and it ends up improving your overall system performance. For example, you can strip out all the unecessary stuff that you will never use because your system does not have the hardware it supports. 

I haven't done this in a really long time, but the last time I built a kernel from scratch, I pulled out almost all the tape drive, infra red device, ham radio and ISDN kernel support and my system speed went through the roof. Of course this was back in the dark days before the 2.2 kernel on a wimpy little AMD K6-2 333MHz, 64MB RAM system using Slackware Linux.

---

### Post by sirdilznik on 2007-12-11
There are all sorts of kernel patches floating around.  Some of them are quite good and are geared toward desktops and interactivity.  Personally I prefer a clean streamlined kernel.  I'm used to compiling my own kernels and I only compile in what I need (I know my hardware and needs inside and out).  It seems daunting at first but it's really not that hard.  I needed a custom kernel for several reasons.  One was a conflict with the splash and NVIDIA drivers with the standard 2.6.22 kernel that came with Gutsy that didn't allow me to have a splash screen (or NVIDIA drivers...  one or the other not both).  Another reason is that I needed reiser4 support for an old partition from my Gentoo install.  2.6.23 had performance issues with the scheduler.  I'm generally not too keen on running RC releases (Release Candidate), but the 2.6.24 RCs have been really good IMHO.  I'm currently running 2.6.24-rc3 vanilla (the basic mainline kernel) with minimal patches added (reiser4, gspca [I like it in-kernel rather than an outside module], and the sched-cfs-boost patch).  I've been really happy with the performance and stability of this kernel (despite the fact that it is a release candidate) and will probably stick with it until 2.6.24 final comes out.  Then I'll compile and install that.  Sometimes adding many "performance boosting" patches creates more overhead and you actually take a hit rather than a gain.  I prefer a clean kernel with minimum patches.  Your mileage may vary.

---

### Post by sirdilznik on 2007-12-11
Also your CPU, memory, and kernel configs will have a great effect on loading data and will have a greater effect on games at low resolution levels.  When you crank the graphics up really high that's when the GPU (Video Card) makes a much bigger difference.

---

### Post by horizonbreakk on 2007-12-11
Thanks guys:) Im going to take a look at how to compile the kernel for my own system...gaming wise. And yeah, oddly enough Half life2 runs faster on Linux then on Windows. Any good sites or forums with some info on how to compile? (I know its a big question but any help would be greatly appreciated) once again thanks a bunch.

---

### Post by cogadh on 2007-12-11
[http://www.linuxdocs.org/HOWTOs/Kernel-HOWTO.html](http://www.linuxdocs.org/HOWTOs/Kernel-HOWTO.html)

---

### Post by sirdilznik on 2007-12-11
[http://www.quietearth.us/articles/2006/09/15/Ubuntu-Compiling-a-custom-kernel]("http://www.quietearth.us/articles/2006/09/15/Ubuntu-Compiling-a-custom-kernel")
[http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")

It's a lot to take in at first, but once you do it a couple of times it becomes second nature.  Most options have help messages to help you along in the kernel compile itself.

---

### Post by MetalMusicAddict on 2007-12-11
Honestly Ive been down this path and the -generic kernel is fine. You will get performance gains that border on placebo if you recompile your kernel or even use -rt.

If you have a low amount of system memory, say 256, using a lighter weight WM would help. But with a fairly beefy machine (common to gamers) the effort involved will yield very little fruit.

---

### Post by sirdilznik on 2007-12-12
> **MetalMusicAddict said:**
> Honestly Ive been down this path and the -generic kernel is fine. You will get performance gains that border on placebo if you recompile your kernel or even use -rt.

If you have a low amount of system memory, say 256, using a lighter weight WM would help. But with a fairly beefy machine (common to gamers) the effort involved will yield very little fruit.
I will agree with that.  You **might** get a performance increase of 2-5% at probably the most.  It's not going to blow your socks off, you probably won't notice the difference.  That being said, compiling a custom kernel is something that is well worth learning if you plan to use Linux on a regular basis.  It's not necessary, but it's really good knowledge to have.

---

### Post by horizonbreakk on 2007-12-12
Awesome guys, thanks a lot! I'm going to take a go at compiling. The support on these forums is great!

---

