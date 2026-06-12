---
title: "Install Kernel?"
date: 2009-03-09
forum: General Help
---

### Post by sjefsape on 2009-03-09
Where can I get the newest kernel? And how do I install it?
I`ve tried to download from kernel.org. But don`t understand what I should do with the file!?

---

### Post by drs305 on 2009-03-09
Is there a reason you need a kernel newer than those available from synaptic or apt-get? They are listed in synaptic as "linux-image-2-6....".  These kernels have been tested with your version of ubuntu and have a high probability of working correctly, which may not be the case with kernels downloaded from outside sources.

You can check the current running kernel with "uname -a". You can use synaptic to find which kernels are installed on your computer. If you have a newer kernel installed than you are currently running you can check your grub menu settings to see which kernel is the default. To do this, I recommend using StartUp-Manager. There is a link to a tutorial in my signature line.

---

### Post by sdennie on 2009-03-09
If you really want to build the newest kernel, you will need a guide.  This is a good start: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu).  It doesn't point out all the caveats and various things you may also need to do but, it's a good start.

---

### Post by blazemore on 2009-03-09
Kernelcheck
[http://sourceforge.net/project/showfiles.php?group_id=199755](http://sourceforge.net/project/showfiles.php?group_id=199755)

---

### Post by sjefsape on 2009-03-09
> **drs305 said:**
> Is there a reason you need a kernel newer than those available from synaptic or apt-get? They are listed in synaptic as "linux-image-2-6....".  These kernels have been tested with your version of ubuntu and have a high probability of working correctly, which may not be the case with kernels downloaded from outside sources.

You can check the current running kernel with "uname -a". You can use synaptic to find which kernels are installed on your computer. If you have a newer kernel installed than you are currently running you can check your grub menu settings to see which kernel is the default. To do this, I recommend using StartUp-Manager. There is a link to a tutorial in my signature line.

I read in a different forum that if I had problems with the NIC
I could try to update my kernel.

---

### Post by drs305 on 2009-03-09
> **sjefsape said:**
> I read in a different forum that if I had problems with the NIC
I could try to update my kernel.

A newer kernel can indeed sometimes fix a particular issue. As you are new to this forum (welcome, by the way) it is possible you have recently installed ubuntu. If that is the case, you are probably already using the most recent kernel for your version and there have been great improvements in networking issues.

We might be able to provide more information if you tell us the version and kernel you are currently running. System, Administration, System Monitor: System.  (Version and kernel).

In general, it is often helpful to include a link to the thread you were reading, and for a NIC problem (if it wasn't your thread) include the type of card you are using. If we see the thread we might be able to see which kernel is being recommended and would have better advice on how to install it.

You will find lots of helpful people on this forum. If you can find the answers by searching threads we can help. 

Asking why you needed a new kernel wasn't meant to be a reproach, just a question since sometimes there are solutions which don't necessarily point in the same direction as the poster is moving.

---

### Post by sjefsape on 2009-03-09
> **drs305 said:**
> A newer kernel can indeed sometimes fix a particular issue. As you are new to this forum (welcome, by the way) it is possible you have recently installed ubuntu. If that is the case, you are probably already using the most recent kernel for your version and there have been great improvements in networking issues.

We might be able to provide more information if you tell us the version and kernel you are currently running. System, Administration, System Monitor: System.  (Version and kernel).

In general, it is often helpful to include a link to the thread you were reading, and for a NIC problem (if it wasn't your thread) include the type of card you are using. If we see the thread we might be able to see which kernel is being recommended and would have better advice on how to install it.

You will find lots of helpful people on this forum. If you can find the answers by searching threads we can help. 

Asking why you needed a new kernel wasn't meant to be a reproach, just a question since sometimes there are solutions which don't necessarily point in the same direction as the poster is moving.

Thanks :D
Yeah, I`m totaly new to the forum and ubuntu.
I have started a thread in networking & wireless. 
Got som tips there too. 
[http://ubuntuforums.org/showthread.php?t=1091435](http://ubuntuforums.org/showthread.php?t=1091435)

---

### Post by blazemore on 2009-03-10
Seriously, KernelCheck is brilliant. It downloads the latest kernel and patch, lets you configure, and then builds and installs it for you. It even builds debs, so you don't have to go through the whole process again in future.

Oh, if you run into problems with Nvidia drivers, just do
```
sudo apt-get purge nvidia-common -y && sudo apt-get install nvidia-common -y
```

---

