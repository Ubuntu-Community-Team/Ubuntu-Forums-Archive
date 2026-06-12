---
title: "how do I build a Kernal???????"
date: 2008-12-21
forum: General Help
---

### Post by Nu music project on 2008-12-21
Actually there are some tutorials about how to use the software to build a kernal, but that's a bit like telling me how to stir a pudding.  I don't know what bits to put in, how they work, the correct sequence to add them or even what the look like.
Where can I learn about this?

All I want is a low latency Kernal to run rosegarden on Ubuntustudo 8.10

---

### Post by PatrickVogeli on 2008-12-21
ubuntusutudio already has a low latency kernel, hasn't it? It's the kernel finishing in -rt

---

### Post by Nu music project on 2008-12-21
It didn't used to.  There have been thread concerning this and I'm sure I read so release notes that specifically mentioned NOT having an RT Kernel.  I have 2.6.27-11 generic.  
but if there IS one, great!!  Where is it?  what exactly do I install?

---

### Post by Nepherte on 2008-12-21
Here's information about the package that provides the rt kernel: [http://packages.ubuntu.com/intrepid/linux-image-2.6.27-3-rt](http://packages.ubuntu.com/intrepid/linux-image-2.6.27-3-rt)

---

### Post by Nu music project on 2008-12-21
Great.  Thanks Nepherte.  I'll reply properly when I figure out what to do with it.  (newbie)

---

### Post by northern lights on 2008-12-21
Further you could run ```
aptitude search linux-image
```to check what kernels are part of the currently enabled repositories.

---

### Post by Nu music project on 2008-12-21
ok.  We move closer.  How do I know that 2.6.27-3-rt works with ubuntustudio?
Do I just apt-get install it?

---

### Post by northern lights on 2008-12-21
Yes.

Ubuntu developers won't add packages to the repositories that do not work with their OS.

```
sudo apt-get install linux-image-2.6.27-3-rt
```

You might have to add it to GRUB manually.

---

### Post by ibuclaw on 2008-12-21
Yep, install it, and reboot.

In the GRUB startup menu, you should see a new entry, press the down arrow till it is highlighted and press Enter to boot into it.

If you then wish to go on and build your own kernel based on the ubuntu realtime kernel, have a look at the Ubuntu Master Kernel Thread:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

The chances am that you won't get it right at first, but you will find that you can remove alot of modules from the kernel, and in doing so will help improve boot speed and lessen the amount of memory allocated in RAM for the kernel too.

But in order to know what to cut out, you need to know, to a very deep level of knowledge, what your PC is made of.

[The Linux Kernel in a Nutshell]("http://www.kroah.com/lkn/") book will help you with 50% of things in getting a bootable kernel.
But it certainly won't help you in ensuring that **that** kernel is usable for multimedia...

Regards
Iain

---

### Post by Nu music project on 2008-12-21
Oh now THIS is interesting.  I go into terminal and install the rt kernel.  It goes through the routine and finally tells me to reboot.  I reboot and there it is ........ the old kernel!
It didn't give me an option.  Do I need to pull out the old one so that it finds the new one?  Is it preventing me from doing something stupid?

---

### Post by nlz on 2008-12-21
you can also try synaptic to see if the kernel is installed. If it's installed, reinstall it using synaptic then it should work.

If you're crazy about music production, extreme stability and the lowest latency possible: try 64studio. I do all my audio stuff on it now. Much better than ubuntustudio...

You can also try dynebolic, then you don't have to install anything. It's a liveCD..

---

### Post by Nu music project on 2008-12-22
oh I get it.  I need to select the kernel I want to run at startup by pressing esc at the GRUB prompt!

Yeah..... didn't work though.  Get past the log in and i just get black screen of death.

................and then it did.

---

