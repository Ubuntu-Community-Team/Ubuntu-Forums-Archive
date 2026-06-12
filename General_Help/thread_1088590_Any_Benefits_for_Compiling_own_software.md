---
title: "Any Benefits for Compiling own software?"
date: 2009-03-06
forum: General Help
---

### Post by Sir_Sid on 2009-03-06
Are there any performance benefits when compiling software from source? Do things run faster/more efficiently? 

I was also wondering about any benefits from running a distro that compiles more or less everything like gentoo.

---

### Post by beno1990 on 2009-03-06
There are differences in the architecture of different models of processors. Normally generic distributions like Ubuntu are aimed at the generic processor models, i386 on the x86 architecture, which is compatible with all future models of x86 processor.

However, on a modern computer which might have newer instructions added to the architecture, pipelines, and other architectural enhancements, using a generically compiled program won't use any of these enhancements and won't be running at peak efficiency, so you won't get everything your processor might have to offer.

A good example of this is virtualisation software like VirtualBox. Virtualisation software on x86 used to be pretty slow and inefficient, because x86 isn't very virtualisation friendly, but newer x86 processors have additional instructions called VT-x, which makes virtualisation a lot more efficient.

There are other things, like being able to tailor the program to your needs, and the Linux kernel is a good example of this, because you can customise almost everything in the kernel before compilation. Another is MySQL which allows you to choose things like which storage engines to compile into your custom build, etc.

So yeah, there are a lot of benefits from custom-building software if you know what you're doing.

---

### Post by nothingspecial on 2009-03-06
> **beno1990 said:**
> There are differences in the architecture of different models of processors. Normally generic distributions like Ubuntu are aimed at the generic processor models, i386 on the x86 architecture, which is compatible with all future models of x86 processor.

However, on a modern computer which might have newer instructions added to the architecture, pipelines, and other architectural enhancements, using a generically compiled program won't use any of these enhancements and won't be running at peak efficiency, so you won't get everything your processor might have to offer.

A good example of this is virtualisation software like VirtualBox. Virtualisation software on x86 used to be pretty slow and inefficient, because x86 isn't very virtualisation friendly, but newer x86 processors have additional instructions called VT-x, which makes virtualisation a lot more efficient.

There are other things, like being able to tailor the program to your needs, and the Linux kernel is a good example of this, because you can customise almost everything in the kernel before compilation. Another is MySQL which allows you to choose things like which storage engines to compile into your custom build, etc.

So yeah, there are a lot of benefits from custom-building software if you know what you're doing.

But for the basic home user - no

---

### Post by 3rdalbum on 2009-03-06
When compiling from source, yes there is a performance benefit over stock Ubuntu packages. When you compile, the resulting code is built for your processor micro-architecture rather than for a "lowest common denominator".

Having said that, compiling your own Openoffice.org doesn't make it boot in 2 seconds. You only see performance benefits with processor-intensive programs, and even there I'm not sure how much extra speed you'll get.

The main advantage with compiling your own software is if you're on a type of processor that doesn't get a lot of pre-built binaries made for it - like ARM, PowerPC, Itanium etc.  For standard PC users, the biggest advantage for compiling your own software is to enable bleeding-edge features or disable buggy features at compile-time. You could also gain access to new features and bugfixes by compiling against a newer version of a support library.

---

### Post by beno1990 on 2009-03-06
> **nothingspecial said:**
> But for the basic home user - no

I'd disagree. I've seen home computer systems run up to 25% faster with a custom built kernel. And the kernel is probably one of the easiest things to custom build these days.

---

### Post by SeanHodges on 2009-03-06
> **Sir_Sid said:**
> Are there any performance benefits when compiling software from source? Do things run faster/more efficiently? 

Yes, there are marginal performance benefits, as you can tweak the software that you compile to optimise it for your system.

In Ubuntu, you can achieve this using "apt-get source" to get the source code, then modifying the debian/rules file and re-building the package using dpkg-buildpackage.

> **Sir_Sid said:**
> I was also wondering about any benefits from running a distro that compiles more or less everything like gentoo.

If you need to ask, then no. 

Having said that, Gentoo is a very nice distro, and worth playing with if you have the time and patience.

---

### Post by sdennie on 2009-03-06
This gets asked fairly often and, as explained above, some parts of the system might be faster if they are custom compiled but for the vast majority of the packages on your system, recompiling them as is but with different compiler optimizations won't make any noticeable effect on the speed at which they run.  Recompiling gnome-terminal with SSE instructions isn't going to be beneficial.  Recompiling the gimp for your machine could make a very large difference when it's doing slow operations that are purely memory/CPU bound.

I would also agree that if you are looking to recompile something for performance reasons, the kernel is a good place to start.  Not necessary because it will actually make any measurable difference but because it's easy to do, very interesting and, if you use make-kpkg, very low risk because multiple kernels can co-exist on the machine at the same time.

---

### Post by TreGe on 2009-03-06
Benefit #1:  Understanding how large software projects are designed and implemented

Benefit #2:  Small overall speedup

Back in the day when I had the time to run Gentoo on all my boxes they were about 10%-15% faster, overall.  Also, as a whole, the system was more stable and ran a hell of a lot smoother (1+ years, no downtime, desktop/development use).

Disadvantage #1:  Bad use of pointers/integers will make a lot of packages fail to compile a lot of the time if you're using an odd architecture, or even just a 64-bit architecture.  A broken X build is NOT fun to debug :P.

---

### Post by Sir_Sid on 2009-03-06
Well ive been a linux user for about two years and I've compiled the odd program every now and then. (Mostly getting those nightlies for songbird). I think I may try recompliling my kernel to see what happens. 

Thanks guys;)

---

### Post by mªrty on 2009-03-06
> **Sir_Sid said:**
> I think I may try recompliling my kernel to see what happens. 
Ditto - but because I play games, and I'm curious how much performance I can get :P

---

### Post by Sir_Sid on 2009-03-06
tell me if you notice any better fps

---

### Post by Slim Odds on 2009-03-06
> **beno1990 said:**
> I'd disagree. I've seen home computer systems run up to 25% faster with a custom built kernel.

That's a pretty bold statement (which I doubt very much). Care to back it up with some facts?

---

### Post by dcstar on 2009-03-06
> **beno1990 said:**
> I'd disagree. I've seen home computer systems run up to 25% faster with a custom built kernel. And the kernel is probably one of the easiest things to custom build these days.

And I've seen many systems go faster when people (finally) stopped using i386 kernels and selected ones that actually used their hardware to the full potential.

I've built my own kernels in the past, and the only significant benefit was the ability to trim down the list of unnecessary modules which resulted in a far smaller kernel than the "standard" Repository kernel.

After a while that "benefit" becomes not worth the effort as continually recompiling whenever a new kernel version became available was hardly worth the tiny bit of disk space that was saved (which was lost by having the kernel source anyway.......)

If people want to get the best performance from their systems, they should find out if they have 64 bit hardware and switch to a 64 bit distro (which some of us did quite a while ago).

---

### Post by Sureshot324 on 2009-05-06
Are Windows executables the same way?  I always thought a windows exe would run on any x86 CPU, and automatically take advantage of any extra CPU instructions if your CPU has them.

---

### Post by Slim Odds on 2009-05-06
> **Sureshot324 said:**
> Are Windows executables the same way?  I always thought a windows exe would run on any x86 CPU, and automatically take advantage of any extra CPU instructions if your CPU has them.

Completely depends on the tools that you use to create the program.

---

### Post by Sureshot324 on 2009-05-07
> **Slim Odds said:**
> Completely depends on the tools that you use to create the program.

How about a regular app compiled in MS Visual C++?  If it can be done in Windows with the right tools why can't it be done in Linux?

---

### Post by Yellow Pasque on 2009-05-08
> **Sureshot324 said:**
> How about a regular app compiled in MS Visual C++?  If it can be done in Windows with the right tools why can't it be done in Linux?
You **can** set compile-time architecture (and optimization) flags with gcc on Linux. [http://gcc.gnu.org/onlinedocs/gcc-4.3.2/gcc/i386-and-x86_002d64-Options.html](http://gcc.gnu.org/onlinedocs/gcc-4.3.2/gcc/i386-and-x86_002d64-Options.html)

In general, Debian/Ubuntu strives for compatibility and making debugging easy over sheer performance. Running Gentoo and tweaking your way to performance-happiness can be fun and a great learning experience. It can also be time consuming.

Like dcstar said, some of us moved to amd64 a long time ago..

---

### Post by Slim Odds on 2009-05-08
> **Sureshot324 said:**
> How about a regular app compiled in MS Visual C++?  If it can be done in Windows with the right tools why can't it be done in Linux?

Some systems have libraries that have multiple implementations of key functions that are implemented (and optimized) for a number of different processors. Then, at runtime, it determines which one to use.

The main problem with this is BLOAT. There is also a small performance overhead for doing this. On a high performance system, it would be better to just compile your application optimized for the machine that you're actually running on.

---

