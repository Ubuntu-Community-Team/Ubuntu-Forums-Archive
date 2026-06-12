---
title: "Ubuntu slow - uses a lot of CPU"
date: 2008-12-04
forum: General Help
---

### Post by JoostV on 2008-12-04
Hi there,

I am new to Ubuntu. I have installed it on my standard Dell Dimension 2300. However, it is terribly slow. Starting up takes ages.

How can I optimize my installation?

I took a look in my System Monitor. My CPU is constantly up to 70% and more in an idle situation. It is constantly swapping 6%. Is that normal?

Any tips to optimize my system or to detect what the problem is?

Thanks a lot in advance

Joost

---

### Post by gabril on 2008-12-04
You have a graphics dirver problem.. everything is software rendered! Try istalling  drivers for your card!

If intel:

$ sudo aptitude install xserver-xorg-driver-intel

---

### Post by ajcham on 2008-12-04
You might struggle with that system - if what I've read is correct the Dimension 2300 has only 128MB of RAM, and that's slow 133MHz RAM at that.

Have you tried Xubuntu?  It may be better suited.

---

### Post by gTinker on 2008-12-04
I agree with ajcham, if the system has only 128MB RAM (the minimum) it is going to be slow. Your system might even have a celeron rather than P4 also. The documentation says 1GB RAM as max., if you can upgrade to at least 512MB you should see some improvement and probably less swapping. If you can, I would suggest you upgrade to the full 1GB, that should give you an acceptable user experience. That system would run XP like a dog too, it probably came with W98.

---

### Post by barbedsaber on 2008-12-04
can you open a terminal, and run
```
top
```
then post the output here.
(it should change every three seconds)
what this is, is a system moniter thing. it will tell us if you have a rouge process that is sucking up your ram and cpu cycles.

---

### Post by barbedsaber on 2008-12-05
oh, and gabril is right.
I would also suggest upgrading your RAM as well. 512 MB can get you out of swap memory completely, and higher speed RAM can't be a bad thing either.

---

### Post by JoostV on 2009-02-09
I have 385 Mhz of RAm (3x128) if I am not mistaken. But I turned to Ubuntu because Linux claims to have a far better memory management than Windows! My old XP Home that came with the machine runs reasonably smoothly on the same machine. And on the internet, there are no noticeable slowdowns under XP. Ubuntu is so slow on the internet, that I stopped using it.

---

### Post by kerry_s on 2009-02-09
> **JoostV said:**
> I have 385 Mhz of RAm (3x128) if I am not mistaken. But I turned to Ubuntu because Linux claims to have a far better memory management than Windows! My old XP Home that came with the machine runs reasonably smoothly on the same machine. And on the internet, there are no noticeable slowdowns under XP. Ubuntu is so slow on the internet, that I stopped using it.

that "linux" grouping is the twist, there are different setups of linux(distro's), you want to get one that works with your hardware or modify the linux to work with the limitations of the hardware. not all linux is the same, there are some that are specifically built to use less resource, then there are others such as ubuntu, who's goal is a modern desktop for modern systems.

---

### Post by lavinog on 2009-02-09
Memory is fairly cheap for this machine. It isn't going to get any cheaper either...you might as well get it now and reap the benefits.

If you system is constantly paging swap, you could be wearing down your hd.

There are a couple of things you can do to lighten the load too. Use Xubuntu instead of Ubuntu. Disable tracker and other services you don't need.
If your system shares memory with your video card, see if you can reduce the shared video memory.

---

### Post by 3rdalbum on 2009-02-09
> **JoostV said:**
> I have 385 Mhz of RAm (3x128) if I am not mistaken. But I turned to Ubuntu because Linux claims to have a far better memory management than Windows! My old XP Home that came with the machine runs reasonably smoothly on the same machine.

The keyword here is "old" - you're comparing an old version of Windows with the latest Ubuntu. Windows XP's system requirements are lower than Ubuntu 8.10's, just as Windows 95 had lower system requirements than XP.

However, Linux does have better memory *management* than XP. Ubuntu uses no swap space on my father's computer, but Win XP uses over 500 MiB. Ubuntu uses as much memory as possible for cache to speed things up, assuming that you have RAM to spare (which you don't).

---

### Post by lavinog on 2009-02-09
> **3rdalbum said:**
> 
However, Linux does have better memory *management* than XP. Ubuntu uses no swap space on my father's computer, but Win XP uses over 500 MiB. Ubuntu uses as much memory as possible for cache to speed things up, assuming that you have RAM to spare (which you don't).
Also the use of shared libraries means that more programs can be run with a smaller memory footprint.

---

### Post by Adrian0 on 2010-05-18
> **gabril said:**
> You have a graphics dirver problem.. everything is software rendered! Try istalling  drivers for your card!

If intel:

$ sudo aptitude install xserver-xorg-driver-intel

Hi Gabril.  On my laptop (a STAMP, 1.6GHz, P4, RAM 1GHz, onboard Intel sound/video etc); recently upgraded my Ubuntu 9.10 to 10.04, in which I'm finding everything very slow - bootup, applications, graphics .. jerky also.   

Tried your Intel Graphics driver install in both normal and Root Terminal, but get following message:  "$: command not found".  Pls explain and say what I should do.  

Thanks.

---

### Post by lavinog on 2010-05-19
> **Adrian0 said:**
> Hi Gabril.  On my laptop (a STAMP, 1.6GHz, P4, RAM 1GHz, onboard Intel sound/video etc); recently upgraded my Ubuntu 9.10 to 10.04, in which I'm finding everything very slow - bootup, applications, graphics .. jerky also.   

Tried your Intel Graphics driver install in both normal and Root Terminal, but get following message:  "$: command not found".  Pls explain and say what I should do.  

Thanks.

try:
```

sudo aptitude install xserver-xorg-driver-intel

```
The $ was part of the prompt.

---

### Post by Adrian0 on 2010-05-19
Thanks.  (Should have tried that!)

However, while the command runs, it doesn't find the target:

     "Couldn't find any package whose name or description matched "xserver-xorg-driver-intel"

Sorry for my lack of knowledge here (haven't had the time I thought I'd get)!  :(  But, I'd like to pursue this, ....  so hope you can guide me further.

---

### Post by lavinog on 2010-05-19
xserver-xorg-driver-intel doesn't exist for me too...don't know where he got that info.

You really should start a new thread since the cause of OP's issue was not enough memory, but you claim to have 1G which should be enough.

In a new thread you should include your hardware info:
use lspci,lshw, lsusb
also post dmesg

it could also help to install bootchart and post a bootchart (located in /var/log/bootchart)

---

### Post by cascade9 on 2010-05-19
> **lavinog said:**
> xserver-xorg-driver-intel doesn't exist for me too...don't know where he got that info.
 
Misnamed the package I guess- 

[http://packages.ubuntu.com/lucid/xserver-xorg-video-intel](http://packages.ubuntu.com/lucid/xserver-xorg-video-intel)

---

### Post by Adrian0 on 2010-05-20
> **lavinog said:**
> xserver-xorg-driver-intel doesn't exist for me too...don't know where he got that info.

You really should start a new thread since the cause of OP's issue was not enough memory, but you claim to have 1G which should be enough.

In a new thread you should include your hardware info:
use lspci,lshw, lsusb
also post dmesg

it could also help to install bootchart and post a bootchart (located in /var/log/bootchart)
Thanks for your help - will try to get to it this weekend! (Meanwhile, a few re-boots later, it's behaving a bit better, but still not what I think it should be). Cheers

---

