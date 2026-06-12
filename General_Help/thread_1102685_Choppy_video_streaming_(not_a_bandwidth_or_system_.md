---
title: "Choppy video streaming (not a bandwidth or system problem)"
date: 2009-03-21
forum: General Help
---

### Post by VeryLost on 2009-03-21
Right now I am dual booting ubuntu 8.10 with my XP machine.

On my XP side, I can play videos on the net just fine, no issues what so ever.

But, for some reason, on ubuntu when I go to watch videos on the net they are choppy as all hell, I would assume it a driver issue but do not know what to do.

Any ideas?

Thanks

System specs

AMD 3800 X2
2 Gig ram
Nvidia 8600 GTS

---

### Post by Nxion on 2009-03-22
Well it could be one of two issues or both. First of all what is the site that has the choppy videos? This could be just a case ou need to either reload or update flash. The second issu could be that the video driver is not install and it is just using the basic nv driver. Have you tried updating or installing a new video driver for your card?

---

### Post by VeryLost on 2009-03-23
youtube.com and hulu.com are the sites.

When I installed ubuntu I selected the recommended option for driver, which was nvidia proprietary if I recall correctly.

How do I check the settings you mentioned?

-Thanks

---

### Post by williane on 2009-03-23
Your running 64bit? I had this same problem under 64bit ubuntu. Been a while but IIRC it was a 64bit flash issue. I dont have the same problem on 32bit ubuntu or in windows.

---

### Post by VeryLost on 2009-03-24
I dont believe so, I am pretty sure I selected 32 bit, is there anyway I can verify?

---

### Post by fixitdude on 2009-03-28
It's fixed!

I had the problem that many flash videos, including hulu and nbc, were skipping, always had to download them using a Firefox plugin which doesn't work with hulu, talk about annoying.

I upgraded everything a few days ago using synaptic package manager and it had a new kernel 2.6.22-16-generic, so I rebooted and now it plays great! I'm on Gutsy.

So try to do a update on everything, reboot and see if that works.

---

### Post by Nxion on 2009-03-30
I'm glad its fixed :)

---

### Post by fixitdude on 2009-04-05
fieroboom made a good suggestion if you are still having problems, remove the "flashplugin-nonfree" and install "adobe-flashplugin", that may work.

[http://ubuntuforums.org/showthread.php?t=1092624&p=7003729](http://ubuntuforums.org/showthread.php?t=1092624&p=7003729)


sudo dpkg --purge flashplugin-nonfree

sudo apt-get update

sudo apt-get install adobe-flashplugin

---

### Post by VeryLost on 2009-04-07
> **fixitdude said:**
> It's fixed!

I had the problem that many flash videos, including hulu and nbc, were skipping, always had to download them using a Firefox plugin which doesn't work with hulu, talk about annoying.

I upgraded everything a few days ago using synaptic package manager and it had a new kernel 2.6.22-16-generic, so I rebooted and now it plays great! I'm on Gutsy.

So try to do a update on everything, reboot and see if that works.


How do you upgrade everything from within the package manager?

-Thanks

---

### Post by fixitdude on 2009-04-19
> **VeryLost said:**
> How do you upgrade everything from within the package manager?

-ThanksUsing Synaptic, press mark all upgrades and then apply, after doing a update to the package sources of course.

---

### Post by spike_naples on 2009-04-27
Thanks. I followed the same things re: synaptic.

---

