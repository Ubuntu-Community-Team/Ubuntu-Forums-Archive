---
title: "Cannot connect to the internet after installing custom kernel"
date: 2007-05-06
forum: Desktop Environments
---

### Post by jRobin on 2007-05-06
Hi, I'm new to linux and decided to try out Ubuntu. After reading some articles on the internet I came across a very useful guide that suggested that I should compile my own kernel, which I did by following the simple steps from the guide.

After installing the new customized kernel and trying it out, the first thing I noticed was that I couldn't connect to the internet any more. The Keyring manager does not appear at start-up and my best guess is that this is causing automatic denial to the web service.

I would be glad if anyone could help me out with this as it is really annoying.

Is there a big difference between the generic kernel and one customized for a Pentium M processor at 1.86GHz?  What is the advantage of compiling source codes instead of using the packages delivered directly by developers?

---

### Post by kidders on 2007-05-08
Hi there,

Since you mention compiling a custom kernel, my first instinct would be to suspect you've forgotten to switch something important on. It's impossible to say exactly what, although here are a few suggestions:

[LIST]
[*]Module auto-loading (without which you need to tell Ubuntu which kernel modules to load, rather than letting it guess).
[*]Your network card driver.
[*]A critical networking option (eg support for IPv4!)
[*]In the case of wireless networks, perhaps something encryption-related?
[/LIST]

Lots of other things can happen too ... for example your network cards (eg eth0, eth1) may have swapped names.

The easiest thing to do would be to try to determine exactly what's wrong, and (where applicable) check the relevant part of your custom kernel configuration.

> **jRobin said:**
> I'm new to linux and decided to try out Ubuntu.Custom kernel compilation is certainly ambitious, if Linux is new to you. :-) Don't let problems like this networking one stop you though ... it can take a few attempts to get a kernel _totally_ right. At least yours booted (which is more than I can say for some of mine!)

> **jRobin said:**
> Is there a big difference between the generic kernel and one customized for a Pentium M processor at 1.86GHz?There *can* be. CPU-specific customisations are only part of the story though. CPU optimisation lets your kernel use instruction sets specific to your architecture, that it wouldn't otherwise take advantage of.

> **jRobin said:**
> What is the advantage of compiling source codes instead of using the packages delivered directly by developers?Like kernel customisation, there can be no advantage at all ... or there can be major advantages ... depending on your situation.

[LIST]
[*]You can use architecture-specific instruction sets.
[*]You can increase (or decrease) the amount of bytecode optimisation going on.
[*]You can use CVS versions of software.
[*]You can switch application features on and off at will.
[*]Etc...
[/LIST]

---

### Post by mlind on 2007-05-08
There shouldn't be need to compile your custom kernel unless you have hardware that's not yet supported by Ubuntu kernel. For my own, experience the overall gain I've got from using a custom kernel has been relatively small if any at all.

New 2.6 kernel's optimize on-the-fly pretty nicely and most of the stuff is compiled as modules. As you said, you're new to linux so don't bother compiling a vanilla kernel just yet.
The learning curve is somewhat steep.

---

### Post by kidders on 2007-05-08
I have to say I agree ... but then again, it doesn't hurt to play around. :-P Building kernels & software from source isn't something one can do on all operating systems, after all.

---

