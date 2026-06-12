---
title: "Compiz not working with Intel HD3000 (HP probook 4530s)"
date: 2012-05-17
forum: Desktop Environments
---

### Post by razedafear on 2012-05-17
HI 

I am installing Ubuntu 10.10amd64 for my Intel i72630QM through wubi (within win7 x64). The compiz does not seem to work here? 
ANy idea why. Also is there a graphics card problem ??
When i right click and try to change the effect from none to "extra" or "normal" under visual styles, it throws an error. Desktop configuration could not be changed (dont know the exact error message though)

ANY HELP??

---

### Post by trulynon on 2012-06-21
I have a Probook 4530s with HD 3000 graphics card and Compiz works flawlessly. I'm working on 32-bit 12.04 LTS. Have you try install a newer versions?

---

### Post by razedafear on 2012-06-22
> **trulynon said:**
> I have a Probook 4530s with HD 3000 graphics card and Compiz works flawlessly. I'm working on 32-bit 12.04 LTS. Have you try install a newer versions?

I have a quad core so i am using x64bit 10.10LTS

---

### Post by 3Miro on 2012-06-22
Intel HD 3000 is also known as Sandy Bridge Graphics. The very first Sandy Bridge drivers that were released by Intel were total garbage. It took some time before the community made enough improvements and since so much effort was thrown to fix the problems, the fixes were never backported to older kernels and releases.

Ubuntu 11.04 is the earliest that can support decent Sandy Bridge graphics. My System76 Pangolin Laptop came with Intel HD 3000 graphics and Ubuntu 11.04. However, you will get better performance with 11.10 and 12.04.

PS: just a note, 10.10 is not and LTS release. LTS means long term support and those releases are 10.04 and 12.04. Canonical will drop the support for 10.10 soon, if they have not done that already.

---

### Post by razedafear on 2012-06-26
> **3Miro said:**
> Intel HD 3000 is also known as Sandy Bridge Graphics. The very first Sandy Bridge drivers that were released by Intel were total garbage. It took some time before the community made enough improvements and since so much effort was thrown to fix the problems, the fixes were never backported to older kernels and releases.

Ubuntu 11.04 is the earliest that can support decent Sandy Bridge graphics. My System76 Pangolin Laptop came with Intel HD 3000 graphics and Ubuntu 11.04. However, you will get better performance with 11.10 and 12.04.

PS: just a note, 10.10 is not and LTS release. LTS means long term support and those releases are 10.04 and 12.04. Canonical will drop the support for 10.10 soon, if they have not done that already.

Thanks!! BTW i have my office desktop running Ubuntu 10.04LTS and its an core i5 machine. Here is the graphics info from command lshw -c video :
```
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:e000(size=128) memory:fb000000-fb07ffff

```

This one has Nvidia enabled right now and compiz works flawless on this. So does that mean if i disable this nvidia and use IntelHD graphics, i will still be able to use compiz?

Also if that is possible, should i switch back to 10.04LTS on my laptop too to use compiz on Intel HD graphics?

---

### Post by 3Miro on 2012-06-27
Couple of notes:
- Generation 1 Intel i5 CPUs did not come with video cards. If  you have an older Intel video card, it would be part of the motherboard chipset and not the CPU. Older Intel cards had no issues.

- Generation 2 Intel i5 CPUs come with video cards. The CPU part works fine on any Ubuntu, the GPU part of the i5 works great, but only on Ubuntu 11.04 and newer.

- Nvidia video cards have issues when they are paired with an Intel video card. If you have two video cards, disabling one and using the other should work well. There are ways to use both video cards, but things get tricky.

- Nvidia video cards have no issues when used by themselves. If your laptop comes with Nvidia video card and you disable the Intel video, you can use Compiz. However, Nvidia video cards will give you bad battery life.

- My guess is that you desktop has only Nvivia video card and your laptop has only Intel. Only the newest desktops come with two video cards and if you had two cards on your laptop you would probably be having more issues.

- Why do you insist on using Ubuntu 10.10 or 10.04, support for those would soon end. If you don't like Unity, you should look at XFCE or Cinnamon (or Mate, KDE, LXDE).

---

