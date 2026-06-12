---
title: "Benifits of Custom Kernel"
date: 2009-05-31
forum: General Help
---

### Post by boblemur on 2009-05-31
Hey all.

I was just wondering what the benefits were of compiling my own custom kernel.
 
I was mainly going to do it as a learning exercise, but i was wondering how much difference a slimed down kernel makes to boot time and system performance etc.

any other information to do with whats good about a custom kernel is much appreciated.

Thanks in advance

---

### Post by kidders on 2009-06-01
Hi there,

The conventional wisdom is that if you don't already know why you need to rebuild your kernel, then you don't need to do it.

Common reasons for doing so include ...[LIST]
[*]You need to exclude buggy code that is causing your system to misbehave.
[*]You need to include code that is not available by default.
[*]You want to patch your kernel.
[*]You perform very computationally intensive tasks that would benefit from tighter optimisation.
[*]You are running in a resource-limited environment (eg a PDA or very old PC) and want to reduce the kernel's footprint.
[*]You want to change the design principle behind the default kernel ... eg switch from a modularised approach to a monolithic one.
[*]You want to rebuild your kernel with more aggressive gcc options for some reason (Risky).
[/LIST]

The difference made to system performance depends on how you use your computer and what you wanted to achieve by rebuilding your kernel ... You may want to make changes that would slow your system down slightly. On the other hand, if you have unusual usage patterns or very specialised hardware, there is some scope for tailoring your kernel to your needs.

Per se, rebuilding your kernel will have no effect on boot time.

In general, using a custom kernel creates maintenance overhead that you may not be used to. It also complicates support in an environment like this one, because can be hard to gauge whether the root cause of a problem is an unstable kernel configuration, or something else entirely.

If you're primarily interested in squeezing a little more juice out of your system, I would suggest looking at options such as ...[LIST]
[*]Tweaking your operating environment to take best advantage of the hardware you've got. For example, if your hard disk is slow, and you only have one of them, you may wish to tinker with your system's swappiness, to make it a little less inclined to page.
[*]A little time spent on filesystem optimisation can often yield surprising results.
[*]You might like to try prelinking your system ... particularly if you're using KDE.
[*]If your graphics hardware is poor, disabling things like compiz & console framebuffer support can have a significant impact.
[/LIST]

Anyhow, I hope that's of some help.

---

