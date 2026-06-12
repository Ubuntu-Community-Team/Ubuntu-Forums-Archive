---
title: "Virtualbox, VMware, Ubuntu, XP and performance"
date: 2011-05-30
forum: Desktop Environments
---

### Post by frankvw on 2011-05-30
Hi, everyone,

I hesitate to raise this delicate matter in this forum, but I have to. 

For reasons I cannot change (i.e. Those Who Hand Me My Paycheck) I simply *have* to run some heavy Windows apps. Except I run Ubuntu and I'm not about to replace it with Windows. I have tried to run said apps in Wine, and while some of them mostly work, Wine doesn't quite cut it. Nor will any other Linux alternatives be sufficient in this case. I simply have to be pragmatic, and face the fact that due to obligations to my employers and customers, I will have to live with running Windows. However I also need Linux in order to simply Get Things Done (not to mention remain sane) at the end of the day. Obviously some sort of virtualization to support multiple OS environments is in order.

I have tried running XP (which is sufficient) in a Virtualbox, and that does work. However, performance leaves a lot to be desired: on Linux I see a maxed out CPU load, while in the virtual XP environment things run slowly. I have tried VMware Workstation on Ubuntu as well, but that is quite a process with similar overhead. Virtualbox ran better (in my case - I'm sure one's mileage will vary).

The question before the house, then, is whether or not it would be better (performance-wise, not reliability-wise, of course) to use XP as the native OS. I've seen several tests and it looks like VMware outperforms Virtualbox in that case. I have done this before, years ago, when I ran CentOS in a VMware workstation box on XP, and that worked very well. I liked VMware Workstation for XP.

So. What would you all suggest? Keeping in mind that I need to run some heavy XP apps, what should be my host OS (XP or Ubuntu) and which virtualization product (VMware or Virtualbox) might be the best choice?

I'm interested in your viewpoints here, people. Hesitate not. :-)

// FvW

---

### Post by An Sanct on 2011-05-30
Hello!

Well, first of all, WINE is not an emulator. On the [Wine-HQ]("http://appdb.winehq.org/") website you have a fairly large list of apps, that *run* and apps, that simply *do not*.

From my personal experience as a windows developer: applications, that have some kind of "Designed for Windows _(edition here)_" certificate work 99.9% in Wine, whilst badly developed, "quick-fix"-hacked, applications that use rough workarounds and applications (hard-coding stuff, ...), that use extremely low level hardware access work very very badly.

My question would be: Which version of VirtualBox are you using? I have read about CPU out-maxing older versions (versions before 4.0)

the second thing would be going 100% non-virtual: Is a dual booting an option? If so, it is always better to dual boot Win/Linux then to virtualize.

PS. I have no (recent) experience with VMWare.

---

### Post by frankvw on 2011-05-30
> **An Sanct said:**
> Well, first of all, WINE is not an emulator.I am well aware of that. With the capitals and everything. :-) I have looked at (and am now discussing) WINE merely as one of the options one might have when it comes to running WinApps on Linux. In some cases this works great, in other cases the results vary from not-so-well to not-at-all. Me and my particular set of WinApps happen to fall in the latter category.

So I have to be pragmatic and accept the fact that right now WINE does not solve my problem and I have to look at virtualization.

> **An Sanct said:**
> My question would be: Which version of VirtualBox are you using? I have read about CPU out-maxing older versions (versions before 4.0)Hm. My version is far older than that. Right now I'm running a *very* stale Ubuntu 8.10 which is about to be replaced with a fresh copy of 11.04... which is why I am debating this particular choice of virtual machine products right now.

That said, the laptop on which all this will be running is not a very muscular model.

> **An Sanct said:**
> the second thing would be going 100% non-virtual: Is a dual booting an option? If so, it is always better to dual boot Win/Linux then to virtualize.That is not an option. I need to have both platforms available all the time. I use Linux for Internet application development, while I will need Windows to connect with existing back end services, graphics and video (if it were just that, than OSX would also be an option, but unfortunately that's just one of the requirements) and document-level compatibility with clients and employers.

> **An Sanct said:**
> PS. I have no (recent) experience with VMWare.I used to run VMware on XP so that I could have a Linux server available on my laptop all the time, and it worked very well (within the context of having to live with XP as the host OS, that is). Two and a half years ago I switched to Linux and then was forced to repeat the exercise the other way around, by running XP in a virtualbox session. There's no rest for the wicked. :-)

// FvW

---

### Post by frankvw on 2011-06-04
A bit of feedback - maybe it will be of some use to someone some day. ;)

I've bitten the bullet, and installed Natty as my host OS and XP in a VirtualBox session. Right off the bat, it works MUCH better than it did on my old 8.04 distro. Virtualbox 4 runs smoother, has a lower CPU load, gives better performance to the guest OS, and seamless mode is lots, lots better than in the 2.x version, too. It may help that I installed VB to use a separate NTFS partition for XP instead of a virtual disk inside a file living in my Linux file system.

So I'm happy - Natty as a host OS and XP as a guest OS works fine without any performance issues.

// FvW

---

### Post by AlexanderDGreat on 2011-06-04
Sorry I didn't read your long post, but it seems you really like VirtualBox, I beg to differ, you can't copy / paste a simple file to VBox, you have to go through a file sharing if ever.

VMware Player - you can run games, dual monitor, c/p files, etc... And it's free. But then again, whichever works for you is great. :)

---

