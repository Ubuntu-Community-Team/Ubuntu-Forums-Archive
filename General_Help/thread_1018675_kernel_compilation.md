---
title: "kernel compilation"
date: 2008-12-22
forum: General Help
---

### Post by rusty_jones on 2008-12-22
this is my first time trying to compile a kernel. I got this error ```

```rusty@rusty-green:~/linux/linux-2.6.27.10$ sudo ~/linux/linux-2.6.27.11/Makefile[sudo] password for rusty: 
sudo: /home/rusty/linux/linux-2.6.27.11/Makefile: command not found

I have the latest version of make. What is the problem?

thxs

---

### Post by sdennie on 2008-12-22
If you are determined to compile your own kernel, this guide might be useful for you: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu).  Generally compiling your own kernel isn't needed though.  What specifically are you trying to accomplish?

---

### Post by rusty_jones on 2008-12-22
I'm trying my hand at building a kernel and following directions from a book "Linux kernel in a nutshell" I got to this command,

```
sudo ls ~/linux/linux-2.6.27.11/Makefile
```

and got stuck. I don't know what Makefile is?

thxs

---

### Post by ostracize on 2008-12-22
> **rusty_jones said:**
> I'm trying my hand at building a kernel and following directions from a book "Linux kernel in a nutshell" I got to this command,

```
sudo ls ~/linux/linux-2.6.27.11/Makefile
```

and got stuck. I don't know what Makefile is?

thxs

The Makefile tells the make command how to compile your kernel. If the Makefile doesn't exist, it's possible you have not done the './configure' command? (If you haven't configured your kernel, how could it have a Makefile to know how to compile your kernel?)

I compiled my own kernel for a while just for the sheer thrill of knowing that I've done it. In the end though, on a run of the mill PC, it isn't worth the hassle at all. The benefit of a manually compiled kernel vs. the vanilla version is non-existent.

---

### Post by sdennie on 2008-12-22
> **ostracize said:**
> 
I compiled my own kernel for a while just for the sheer thrill of knowing that I've done it. In the end though, on a run of the mill PC, it isn't worth the hassle at all. The benefit of a manually compiled kernel vs. the vanilla version is non-existent.

I would agree here.  I've run custom compiled kernels for years and "performance" is not a valid reason to compile your own kernel.  There aren't many valid reasons to compile your own kernel.

---

### Post by fmb on 2008-12-22
It might be worth it if you want to patch kernel module yourself. I know this only requires module rebuilding, but once I did that (having most recent generic-kernel and kernel sources) I couldn't insmod the result. I had to have my very own full kernel. Luckily I had kernel config since my gentoo times, so it wasn't a problem. 

The module I'm talking about is uvcvideo. Since 2.6.27 it's included in mainstream kernel, but Logitech Quickcam Pro 5000 has issues with it, so a third-party patch is requred.

---

### Post by sdennie on 2008-12-22
> **fmb said:**
> It might be worth it if you want to patch kernel module yourself. I know this only requires module rebuilding, but once I did that (having most recent generic-kernel and kernel sources) I couldn't insmod the result. I had to have my very own full kernel. Luckily I had kernel config since my gentoo times, so it wasn't a problem. 

The module I'm talking about is uvcvideo. Since 2.6.27 it's included in mainstream kernel, but Logitech Quickcam Pro 5000 has issues with it, so a third-party patch is requred.

The v4l modules can be a bit tricky to build if you get them out of mercurial.  They don't install in standard places and so you are likely to get conflicts when loading the modules.  I generally have to delete the entire v4l subsystem from the kernel modules before installing it.

---

