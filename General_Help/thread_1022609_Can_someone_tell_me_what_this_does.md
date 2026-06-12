---
title: "Can someone tell me what this does?"
date: 2008-12-27
forum: General Help
---

### Post by JBauer5 on 2008-12-27
This is probably the 5th time I've installed linux, but the first time I'm actually keeping it.   I figured it'd be a lot easer to do CS labs in linux instead of installing a million things in windows to get system calls like fork() to work properly.

Anyways, I'm reading a set of instructions on getting injection to work on a certain wifi card by recompiling the kernel, etc, etc.. and was wondering what this line did (technically), and how I could change it to use something more recent.
[quote=noone in particular]
sudo apt-get install kernel-package libncurses5-dev fakeroot wget bzip2 linux-source[/quote]

I've figured out what sudo, and apt-get install do, but why does fakeroot, wget, bzip2, and linux-source have to be tagged onto the back?

Thanks ;)

---

### Post by lykwydchykyn on 2008-12-27
Everything after the word "install" are names of packages you are installing.

---

### Post by p_quarles on 2008-12-27
> **lykwydchykyn said:**
> Everything after the word "install" are names of packages you are installing.
Exactly. Those are just the names of tools you need to compile your own kernel.

---

### Post by JBauer5 on 2008-12-27
Ahh.. ic.  That's why all those things have man pages, because I installed them. :oops:  Okay thanks!

---

### Post by p_quarles on 2008-12-27
> **JBauer5 said:**
> Ahh.. ic.  That's why all those things have man pages, because I installed them. :oops:  Okay thanks!

Just FYI, once you begin to see the logic of how Bash works, you'll be able to see the difference between a separate command and an argument for the first command. 

The following symbols all indicate that a new command will follow:
```
&& ; | $(command) ||
```
In the absence of that kind of special syntax, it's usually safe to assume you're looking at arguments for the first command.

---

