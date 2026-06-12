---
title: "What kernel is right for AMD X2 CPU?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by TitanKing on 2006-06-17
Thank you for looking at my thread, I have simple questions which I hope I could get an anwsers for. Its not crytical but itl help to know more. Please note that I am limited in using a different kernel as their are no other precompiled Kernels with Nvidia drivers for the AMD X2 CPU...  

1. I am running AMD64-2.6.15-23 Generic Kernel, is this the correct kernel for the AMD X2 ?
2. What is the Linux-Image in Synaptic ?
3. What is linux-kernel-headers in Synaptic ?
4. What is linux-source in Synaptic ?
5. What is nvidia-kernel-common in Synaptic ?

I apprecitate any feedback, if I could just get behind this I would be a happy duckling...

Please note that the generic kernel shows both my processors...

:)

Thank you,
Titan

---

### Post by x64Jimbo on 2006-06-17
I'm not sure about dual cores but i can enlighten you on some of your other questions...
the kernel headers are the header files for the kernel. these are usually needed if you're installing something with a kernel module like VMWare or the Cisco VPN client. linux-source is just the straight-up kernel source that you can use to compile your own if you choose.  That's about all I know about kernel stuff... but someone else might be able to help you.

---

### Post by TitanKing on 2006-06-17
Thanks for the fast response ! I appreciate it, I would seriously like answers as it seems like a "grey" area in Ubuntu forums...

---

### Post by tseliot on 2006-06-17
[QUOTE=TitanKing]Thank you for looking at my thread, I have simple questions which I hope I could get an anwsers for. Its not crytical but itl help to know more. Please note that I am limited in using a different kernel as their are no other precompiled Kernels with Nvidia drivers for the AMD X2 CPU...  

1. I am running AMD64-2.6.15-23 Generic Kernel, is this the correct kernel for the AMD X2 ?[/QUOTE]
Please post the output of the following command:
```
uname -a
```

[QUOTE=TitanKing]2. What is the Linux-Image in Synaptic ?[/CODE]
It's the kernel, without any restricted modules or dependencies.

[QUOTE=TitanKing]3. What is linux-kernel-headers in Synaptic ?[/CODE]
They contain the source code of your kernel (you will need them to compile some modules)

[QUOTE=TitanKing]4. What is linux-source in Synaptic ?[/CODE]
The source code of your kernel (you need it in order to compile a new kernel)

[QUOTE=TitanKing]5. What is nvidia-kernel-common in Synaptic ?[/CODE]
A package which makes sure that the nvidia module from the repos is loaded at boot.
You shouldn't bother with that. If you want to install the Nvidia driver, please follow my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")


[QUOTE=TitanKing]Please note that the generic kernel shows both my processors...[/CODE]
32 bit kernels has the support for SMP (multi-processors) enabled by default. And I think it's the same for 64 bit kernels.


BTW I would not recommend Ubuntu 64bit to newbies. Ubuntu 32 bit (which runs also on 64bit CPUs) can make your life easier.

---

### Post by TitanKing on 2006-06-17
Thank you very very much for the reply ! :rolleyes: You have cleared it up pretty well. I appreciate your reply. 

I have to agree the 64 bit can be a pain in the *** :D

Anyways, I think my kernel shows SMP support :

Linux TitanKing 2.6.15-23-amd64-generic #1 SMP PREEMPT Tue May 23 13:45:47 UTC 2006 x86_64 GNU/Linux

---

