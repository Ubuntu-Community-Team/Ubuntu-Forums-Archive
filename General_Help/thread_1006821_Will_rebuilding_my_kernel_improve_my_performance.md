---
title: "Will rebuilding my kernel improve my performance?"
date: 2008-12-09
forum: General Help
---

### Post by Serpreme on 2008-12-09
I'm a little let down by the speed and performance of ubuntu. It appears to be somewhat clunky. I'm wondering if i rebuild my kernel, could i through some swapping of "stuff" get better performance?
Or would i simply be better off finding what "drivers" i have installed and making sure they are the best ones possible?

---

### Post by binbash on 2008-12-09
if you done it right, it will improve performance a LOT

---

### Post by sdennie on 2008-12-09
In my experience you will see little to no difference in day to day applications using a custom compiled kernel (even with "optimal" settings).  If you have plenty of RAM, one thing that might help would be to install preload:

```

sudo apt-get preload

```

The program learns what applications you use most and tries to keep them in RAM so they load faster.  Linux in general will run faster the long your use it but, preload tries to artificially make that happen faster.

What specifically do you find slow about your machine?  It's hard to know what to recommend if you don't give more details.

---

### Post by Krupski on 2008-12-09
> **Serpreme said:**
> I'm a little let down by the speed and performance of ubuntu. It appears to be somewhat clunky. I'm wondering if i rebuild my kernel, could i through some swapping of "stuff" get better performance?
Or would i simply be better off finding what "drivers" i have installed and making sure they are the best ones possible?

Just run TOP and look how much CPU usage there is and how many processes are sleeping and you will find that the computer is doing virtually nothing *unless* you're running something.

So, all the "extra worthless" stuff that may be loaded by a generic kernel is not hurting you one bit.

Don't waste your time compiling a new kernel... you'll open yourself up to a world of headaches if you do.

---

### Post by dcstar on 2008-12-10
> **Serpreme said:**
> I'm a little let down by the speed and performance of ubuntu. It appears to be somewhat clunky. I'm wondering if i rebuild my kernel, could i through some swapping of "stuff" get better performance?
Or would i simply be better off finding what "drivers" i have installed and making sure they are the best ones possible?

Generic kernels are chock-full of code that is not applicable to your hardware/app requirements - but because the kernel has to be usable for the multitude of possible requirements out there you have to live with all the code you will never (ever) use.

You can customise your own kernel build with only the hardware components and features that you know you need, and if you do it right you will have a much smaller kernel that loads quicker and (in theory) performs better - but be warned that you have to do everything right and you will probably break things.

There are HOWTOs in the forums on how to customise and build you own kernel.

---

### Post by cr4nk on 2008-12-13
> **vor said:**
> In my experience you will see little to no difference in day to day applications using a custom compiled kernel (even with "optimal" settings).  If you have plenty of RAM, one thing that might help would be to install preload:

```

sudo apt-get preload

```

The program learns what applications you use most and tries to keep them in RAM so they load faster.  Linux in general will run faster the long your use it but, preload tries to artificially make that happen faster.

What specifically do you find slow about your machine?  It's hard to know what to recommend if you don't give more details.


What would you consider "plenty of RAM"? I got a sony vaio vgn-fs715/w laptop with 1.73ghz centrino, 1gig(upgraded from 512) ram, intel 915 graphix. Would I benefit from preload?

---

### Post by pseudonym on 2008-12-13
The best thing a kernel rebuild will give you is a faster boot time IMHO. If you want smoother day-to-day performance you can look into some of these tips [here]("http://kmandla.wordpress.com/set-up-ubuntu-for-speed/") (and similar threads on the forum).

If you can live with the simplicity you might also want to try a lightweight window manager like [Openbox]("https://help.ubuntu.com/community/Openbox?highlight=(openbox)"). This can make a big difference to your system's responsiveness but can take a little getting used to.

---

### Post by Arup on 2008-12-13
Turn off compiz, select desktop effects to none, use metacity instead. Also make sure the searh and indexing is running at lowest setting. All this speeded up the response in my system by a lot.

---

### Post by khelben1979 on 2008-12-13
Yes, if you build it correct.

You could also try to turn off some scripts from /etc/init.d/ to improve performance. Or... do what I have done in various Linux distributions: move the scripts to a new catalog so they don't start each time the computer starts up to speed things up.

From the experience I got from Ubuntu, I experienced it sloooow compared to Debian (which is my personal favourite).

---

### Post by sdennie on 2008-12-13
> **cr4nk said:**
> What would you consider "plenty of RAM"? I got a sony vaio vgn-fs715/w laptop with 1.73ghz centrino, 1gig(upgraded from 512) ram, intel 915 graphix. Would I benefit from preload?

You might find preload useful with 1G of RAM.  At the very least, it's very unlikely to make things slower.

As for people saying a custom kernel will make things faster, yes, for some things a custom and well configured kernel will make a difference however, it's not something that will magically speed up your entire machine.  If you choose to build a custom kernel, I would first identify what you think is slow about your machine.  Benchmark it in some way so that you are able to quantify "slow".  Then build a custom kernel and see if it's still "slow".  Chances are good that it will be.

---

### Post by logos34 on 2008-12-13
> **vor said:**
> In my experience you will see little to no difference in day to day applications using a custom compiled kernel (even with "optimal" settings).  If you have plenty of RAM, one thing that might help would be to install preload:

+1

that's my experience too. I just reconfigured prelinking and it speeds up the loading of some (but alas not very many) apps, while cleaning up the boot process with sys-rc-conf and disabling other uneeded background programs (britty, cups, tracker et al) has made the system a little quicker.  Also, the system will feel a little more agile if you run the real-time kernel (linux-rt).  But like VOr says, more ram offers the most payoff

add: but I see you already have 1 gb which is plenty

---

