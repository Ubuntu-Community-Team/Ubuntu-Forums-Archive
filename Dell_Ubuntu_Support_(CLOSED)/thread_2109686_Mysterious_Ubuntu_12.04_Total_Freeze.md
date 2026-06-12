---
title: "Mysterious Ubuntu 12.04 Total Freeze"
date: 2013-01-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by urielo on 2013-01-28
Hey,

I have a Dell Inspiron 14 2530 with Ubuntu 12.04. Once in a while the system freezes completely (can't move mouse, keyboard won't work, no HD led blinking) for no apparent reason. Sometimes I haven't even started any programs.
Anybody got the same issue, or knows what could cause such freezes? Currently I'm dealing with it by hard rebooting the system, and hoping it won't happen again.

---

### Post by furything on 2013-01-28
Have you ever opened your case and vacummed the dust out (carefully)?

I do this to all my PCs at least once a year as dust builds up in the heat sink and the PC either runs extremely slow or freezes once the cpu gets too hot.

Found this out a long time ago as amd used to just stop - disconnect power supply before able to switch back on.

Whilst Intel does speed stepping to how slow can you go until unresponsive.

May be unrelated but take a look.

---

### Post by urielo on 2013-01-28
> **furything said:**
> Have you ever opened your case and vacummed the dust out (carefully)?

I do this to all my PCs at least once a year as dust builds up in the heat sink and the PC either runs extremely slow or freezes once the cpu gets too hot.

Found this out a long time ago as amd used to just stop - disconnect power supply before able to switch back on.

Whilst Intel does speed stepping to how slow can you go until unresponsive.

May be unrelated but take a look.
I have not, but this seems unlikely since the laptop is only a month old and sometimes when it freezes i just turned it on and it's not warm at all.

---

### Post by SuperFreak on 2013-01-28
I had frequent freezes like that. For me the problem had to do with my Intel Ivy Bridge CPU I think. I updated the kernel to a later version then the stock version and problem disappeared. There is quite a bit of info on how online.

---

### Post by furything on 2013-01-29
Urielo
Should have looked to see what your machine was first. Sometimes though the most simple things turn out to be the answer.

Yes a one month laptop should not have sufficient dust and I also don't recommend taking them apart. They are a pain in the **** to get back together.

You can also see dust build up around the vents. 

Does look more like the other post though to do with the intel bridge set. Have you had any luck?

---

### Post by urielo on 2013-01-29
> **SuperFreak said:**
> I had frequent freezes like that. For me the problem had to do with my Intel Ivy Bridge CPU I think. I updated the kernel to a later version then the stock version and problem disappeared. There is quite a bit of info on how online.
Well, I just updated to Kernel 3.6.2 via this tutorial
[http://www.upubuntu.com/2012/10/install-linux-kernel-362-on-ubuntu.html?m=1]("http://www.upubuntu.com/2012/10/install-linux-kernel-362-on-ubuntu.html?m=1")

Is this the version you updated yours?

---

### Post by SuperFreak on 2013-01-29
Mine is 3.3.6-030306-generic so you should be OK

There was a Bug reported a long time ago when 12.04 first came out with a number of people having spontaneous freezing and using i7 (and i3,i5)CPUs([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)). The kernel update fixed my problem anyway so I hope it works for you too.

---

