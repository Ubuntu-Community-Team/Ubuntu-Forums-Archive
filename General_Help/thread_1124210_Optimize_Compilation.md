---
title: "Optimize Compilation"
date: 2009-04-13
forum: General Help
---

### Post by Labello on 2009-04-13
Hi all!

I have a general question regarding compilation of packages.

When I normally compile something i just invoke:

> 
./configure
make
make install


But I have read that when I compile from scratch I am able to optimize the programm for my architecture. Does "make" consider my architecture or do i have got to hand own build-flags to make? how do i do that? because afaik gcc is used for compilation most of the time. And I also found some build-flags for gcc to optimize the code by using more time to compile. But still I wonder how to make "make" use these optimization-flags. Could anyone be able to help me out? A nice link would be enough!

Thanks in advance!

---

### Post by lloyd_b on 2009-04-13
> **Labello said:**
> Hi all!

I have a general question regarding compilation of packages.

When I normally compile something i just invoke:



But I have read that when I compile from scratch I am able to optimize the programm for my architecture. Does "make" consider my architecture or do i have got to hand own build-flags to make? how do i do that? because afaik gcc is used for compilation most of the time. And I also found some build-flags for gcc to optimize the code by using more time to compile. But still I wonder how to make "make" use these optimization-flags. Could anyone be able to help me out? A nice link would be enough!

Thanks in advance!

First off, try running "./configure --help".  This will list a whole mess of options that can be passed to the configure script.

Typically, these scripts do take into account the different architectures, though this varies from project to project.

If you want to tweak the compilation process, you can run the "./configure", and then manually modify the resulting "Makefile", which is what controls what the "make" utility is doing to compile the program. 

Lloyd B.

---

### Post by Aubergines on 2009-04-13
Take a look at [this](http://gcc.gnu.org/onlinedocs/gcc-4.3.3/gcc/Optimize-Options.html#Optimize-Options) and also at the optimisations in the Gentoo forums [here](https://forums.gentoo.org/viewtopic.php?t=5717). The thread is quite old but gets more current over the 55 pages of discussion over two parts.

---

### Post by sdennie on 2009-04-13
Most of the time applications include their own optimization flags.  Usually it's just -O2 but, some things (the things that are likely to benefit from them) will detect what your machine is and build for that.  For example, MPFR and GMP.  Most software isn't CPU bound and so increasing the optimization makes no difference.  In fact, most software is I/O bound and so increasing the optimization and making the binary larger but "faster" probably has the opposite effect.

---

### Post by Labello on 2009-04-13
I already read the article in the gcc-manual. but thanks for that and the link to this gentoo-thread. I have noticed that the gentoo wiki and forums are quite good for research concerning compilation

> 
Most of the time applications include their own optimization flags. Usually it's just -O2 but, some things (the things that are likely to benefit from them) will detect what your machine is and build for that. For example, MPFR and GMP. Most software isn't CPU bound and so increasing the optimization makes no difference. In fact, most software is I/O bound and so increasing the optimization and making the binary larger but "faster" probably has the opposite effect.

Could you please explain this a little further? I don't really get what you want to say to be honest. :)

---

### Post by sdennie on 2009-04-13
> **Labello said:**
> I already read the article in the gcc-manual. but thanks for that and the link to this gentoo-thread. I have noticed that the gentoo wiki and forums are quite good for research concerning compilation


Could you please explain this a little further? I don't really get what you want to say to be honest. :)

What I'm saying is that when you click on an icon, if there is a delay, it's probably because it's reading binaries and libraries from your disk.  If there is no delay, it's because it's reading them from cache.  Making those things "more optimized" but larger (which high levels of optimization imply) means that they take longer to read and that they probably occupy more space in the cache.  So, by optimizing, you've slowed down the initial read and made the subsequent reads more burdensome on the system by occupying more space in the cache.

Basically, you want to do obvious optimizations with the compiler and then try to produce the smallest thing possible (So, -Os).  Unless of course your app is CPU bound.  Then go crazy tweaking the compiler optimizations.

---

### Post by Aubergines on 2009-04-13
Back in 2002 to 2005 I used to be a die hard Gentoo fan. Installing from stage 1 and "optimising" stuff I didn't really have a huge understanding of. It was my first linux distro, it was great fun and the process taught me a lot about linux. There's much content on the gentoo forums that's misinformed, people like I used to be playing around with various switches. Much of it leads to over optimisation or using switches that weren't particularly stable at the time and you end up with something slower than the default. On a modern machine it's probably not even hugely noticeable.

What sdennie is saying tweaking doesn't always yield desirable effects.

Furthermore unless you use a meta distro like Gentoo or Freebsd where stuff is compiled you'll have fun later when updating and maintaining software.

---

### Post by sdennie on 2009-04-13
> **Aubergines said:**
> 
What sdennie is saying tweaking doesn't always yield desirable effects.


That's exactly what I'm saying.  And the reason is what I use for a signature.

---

### Post by defaultusername on 2009-04-13
Labello,

Compiling Firefox and some other apps with -O3 tends to bad results. If you're knowledgeable, you could always try setting switches individually instead of using optimization levels (-O2, -O3, etc.). I don't suggest this unless you know what the switches do.

Most systems will do just fine on debs installed through Synaptic. Additional optimization either won't lead to noticeable benefits or will contribute to PM woes or instability.

---

### Post by Labello on 2009-04-13
Hi you all!

Thanks for all those hints and points of view. Well I rather like fiddling around with my system and i tend to break stuff very often. but with every resetup I learn something new.

But what I think is: When I fetch a package from the ubuntu-repos. These packages are compiled for a broad range of architectures. But I know that one can push the kind of processor to gcc and it will optimize the built for this processor-type. And moreover these parameters with "-Ox" seem to apply many parameters at once.

Let's assume that we have three different types of package-collections to compile:
-Kernel
-X-Server
-Gnome

Which collection is expected to run best with which build-flags?

Labello

---

### Post by Aubergines on 2009-04-13
sdennie will be able to tell you more but I think -O2 is what most things are compiled as and is probably best to stick with it. -Os is basically -O2 with some stuff disabled to make binaries as small as possible. Small binaries will load faster.

-march="xxxx" is where you can optimise for specific cpus. You can find valid cpu options [here](http://gcc.gnu.org/onlinedocs/gcc-4.3.3/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options)

Something like:
```
CFLAGS="-march=core2 -Os -pipe"
CXXFLAGS="${CFLAGS}"
```

Do realise anything built like this will be very specific so you couldn't move the drive to say an AMD machine and expect it to work properly.

---

### Post by Labello on 2009-04-14
> **Aubergines said:**
> Do realise anything built like this will be very specific so you couldn't move the drive to say an AMD machine and expect it to work properly.

I am perfectly aware of this fact! Thanks to all of you!

---

### Post by sdennie on 2009-04-14
Yes, most things will compile as -O2 by default because the optimizations applied are safe and well known.  I've been creating a LFS (Linux From Scratch) build and for the "major stuff", I've been using the defaults because using anything else tends to not work.  However, for everything else, I've been using exactly what Aubergines posted (except without the -pipe).

If you are going to try to optimize something, you really need to have some sort of measurement to compare your optimized version to.  Otherwise you are very susceptible to a placebo effect where you think it's faster but, in reality it's the same or slower.

---

### Post by sdennie on 2009-04-16
Just to follow up on this, I'd like to add that I really think for a desktop machine compiling with the highest optimization is not as good as compiling for the smallest size (though, it depends on the application).  For example, on the LFS build I'm creating, I compiled the package that produces the "ls" command with "-Os -march=core2".  The "ls" binary is 20% smaller than the same binary under Ubuntu.  That makes no difference (93k vs. 73k isn't a big deal) but, if you apply that sort of size reduction across the entire system, it's something you'll notice.

It's a theory I'm in the midst of testing but, I think -Os is probably the optimal setting for a desktop machine.  If a piece of software is not CPU bound, it's probably better to have it small than possibly a tiny, tiny bit faster.

(By the way, I used to work at Sun doing performance analysis and optimization.  I'm not just making this stuff up.)

---

### Post by Labello on 2009-04-16
So is the kernel (i.e.) more CPU bound oder rather file bound?

---

### Post by sdennie on 2009-04-16
> **Labello said:**
> So is the kernel (i.e.) more CPU bound oder rather file bound?

No, the kernel is configuration bound.  If you build your own and configure it right, your machine will be faster (but, you have to understand how you use your machine and to make this work).  The compilation options in the kernel probably make no difference.  It's written as straight and simple C and so (based on the nature of it in the first place) compiling it with higher optimization will likely make no difference at all.

---

### Post by Labello on 2009-04-16
> **sdennie said:**
> No, the kernel is configuration bound.  If you build your own and configure it right, your machine will be faster (but, you have to understand how you use your machine and to make this work).  The compilation options in the kernel probably make no difference.  It's written as straight and simple C and so (based on the nature of it in the first place) compiling it with higher optimization will likely make no difference at all.

So it does affect the speed more if I configure the kernel right? so i choose which modules are to compiled and which parts are to be left out right?

---

### Post by sdennie on 2009-04-16
> **Labello said:**
> So it does affect the speed more if I configure the kernel right? so i choose which modules are to compiled and which parts are to be left out right?

Kernel compilation is tricky.  Only compiling what you need may increase boot speed because the depmod at boot time has fewer things to look at.  But, really, to get something out of building your own kernel, you need to only look at the first three/four options in "make menuconfig".  They have the tweakable options that could, in theory, make your machine run better.

---

