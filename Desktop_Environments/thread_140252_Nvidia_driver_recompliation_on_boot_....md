---
title: "Nvidia driver recompliation on boot ..."
date: 2006-03-05
forum: Desktop Environments
---

### Post by dbee on 2006-03-05
I have to run the nvidia installer and recompile the nvidia kernel module everytime I boot up in order to start up X. I go through the process and click yes when it asks me if I want to save the configuration. But it doesn't help.

I still have to set CC=gcc-3.4, then run the installer, complie the kernel module, save it and then switch back to user - before I can start up X properly. 

Anyone have any ideas ?

---

### Post by Sutekh on 2006-03-05
Have you tried following this HOWTO?

[Ubuntu Forums - HOWTO: Latest NVIDIA Drivers - by ]("http://ubuntuforums.org/showthread.php?t=75074")[tseliot]("http://ubuntuforums.org/member.php?u=19388")

I'm afraid I have no idea why you would need to run the installer every time you boot up.  Try the HOWTO and see if it works out (apologies if you've already tried it)

---

### Post by dbee on 2006-03-06
Ya, I tired the howto but it didn't work unfortunately.

I have the thing working (sort of ) now at least - so I don' t want to have to go back and do it again. But thanks anyway...

Anyone else have a solution ?

---

### Post by Sutekh on 2006-03-06
[QUOTE=dbee]Ya, I tired the howto but it didn't work unfortunately.[/QUOTE] If you had problems after using the HOWTO you should post in that main thread, particularly since you tried that method and had problems.  

It gets plenty of exposure, and so many people would have used it, that its quite likely someone has come across it before, or that tseliot can diagnose the problem.

---

### Post by dbee on 2006-03-06
My problem isn't with the HOW-TO ... I have nvidia working perfectly. My problem is that the kernel module has to recompile everytime I boot up. 

I'd imagine that either there is a gcc library issue or that there is some problem overwriting a configuration file. 

I don't think I need to post in the HOW-TO section when I didn't actually use the HOW-TO. Surely my question is a general linux one, and not specific to an NVIDIA HOW-TO section that I didn't use ?

But I guess you might be right ... if I can't get a response here I'll post over on the NVIDIA HOW-TO section. 

Thanks, :)

---

### Post by dbee on 2006-03-15
So I still have the same issue, everytime I boot up I have to recompile the nvidia kernel.

The output from dmesg is like this ...
> 
NVRM: RM client version mismatch
NVRM: Aborting to avoid catastrophe

... so it seems that the nvidia module is in my kernel, its just that there is a 'client version mismatch'

Can anyone help me out here ?

THanks

---

