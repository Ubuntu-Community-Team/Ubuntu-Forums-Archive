---
title: "NVIDIA-Linux-x86_64-295.59.run"
date: 2012-07-18
forum: Desktop Environments
---

### Post by dcuster on 2012-07-18
xubuntu x86_64 desktop 12.04

I really don't want to be forced to reinstall, could anyone give me a step by step, assuming there are only like 3 steps.

Plz&Thx:popcorn:

---

### Post by papibe on 2012-07-18
I dcuster. Welcome to the forums :)

I would feel very unconformable giving you instructions without knowing a little more what you are trying to do.

Could you explain a little bit more?

Could you post the result of these commands?
```
sudo lshw -C display

lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by dcuster on 2012-07-18
> **papibe said:**
> I dcuster. Welcome to the forums :)

I would feel very unconformable giving you instructions without knowing a little more what you are trying to do.

Could you explain a little bit more?

Could you post the result of these commands?
```
sudo lshw -C display

lspci -nnk | grep -iA2 vga
```Regards.
[COLOR=Lime]
[COLOR=DarkGreen]**sudo lshw -C display**[/COLOR]
*-display UNCLAIMED     
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f6000000-f607ffff
  *-display
       description: VGA compatible controller
       product: Ivy Bridge Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)

[COLOR=DarkGreen]**lspci -nnk | grep -iA2 vga**[/COLOR]
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:10c7]
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0fd1] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:10c7]
    Kernel modules: nouveau, nvidiafb[/COLOR]

I have MSI GE60-ONC with a NVIDIA **Geforce GT 650M** / 2GB GDDR5. I went to **nvidia.com**, and downloaded the linux 64bit drivers **NVIDIA-Linux-x86_64-295.59.run**

I have had problems in the past installing NVIDIA-Linux-x86_64-*.run drivers, I was hoping I could get through this without any complications. As unlikely as that seems. :|

I really appreciate your help.

---

### Post by papibe on 2012-07-18
It was good that you provided more information because you have a special configuration.

You have Nvidia [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is (but a pessimist). And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

There are laptops that can either disable it, or simplify things by turning off the Nvidia card. Check your BIOS if you have any of those options.

If you are able to make it work, I would take the following procedure to install the Nvidia driver:

First I would try the suggested driver. Go to 'additional drivers' or 'hardware drivers' and install the suggested driver.

If that doesn't work I would upgrade to the version of this ppa:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

Then if that doesn't work either, there's another ppa with bleeding-edge versions:
 
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

I would let the driver from the Nvidia site as the last resort.

I hope that helps.
Regards.

---

### Post by dcuster on 2012-07-18
> **papibe said:**
> It was good that you provided more information because you have a special configuration.

You have Nvidia [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is (but a pessimist). And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

There are laptops that can either disable it, or simplify things by turning off the Nvidia card. Check your BIOS if you have any of those options.

If you are able to make it work, I would take the following procedure to install the Nvidia driver:

First I would try the suggested driver. Go to 'additional drivers' or 'hardware drivers' and install the suggested driver.

If that doesn't work I would upgrade to the version of this ppa:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```Then if that doesn't work either, there's another ppa with bleeding-edge versions:
 
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```I would let the driver from the Nvidia site as the last resort.

I hope that helps.
Regards.

I read everything that you gave me. I appreciate it. Let me as you another question. Overscan, is there any way to adjust for overscan when plugged in to a tv via hdmi?

---

### Post by papibe on 2012-07-18
> **dcuster said:**
> I read everything that you gave me. I appreciate it. Let me as you another question. Overscan, is there any way to adjust for overscan when plugged in to a tv via hdmi?

The easiest solution is to disable it on your TV.

If that's not possible, the Nvidia driver has a feature to adjusting/correcting it from the computer itself.

Regards.

---

### Post by dcuster on 2012-07-18
Thank You for all of your help.

Please close this thread.

---

### Post by papibe on 2012-07-18
You are very Welcome!

The best way to 'close it' is that you mark it as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")). You can create a new one if you encounter any problems in the feature.

Kind Regards.

---

