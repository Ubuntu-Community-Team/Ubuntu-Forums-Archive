---
title: "Dual monitor won't work - Video card is Nvidia Quadro FX 540"
date: 2008-01-16
forum: Dell  Ubuntu Support
---

### Post by conradinsf on 2008-01-16
Hi all,

I am having issues with my dual monitor setup with Ubuntu. I just completed a dual-boot system with XP Pro and Ubuntu (thanks to all the contributers). The video card is **NVIDIA QUADRA FX 540 **with a **dual monitor setup** (single desktop) with XP Pro, and it works fine.

My computer specs (in case it is needed) is the following:
[I]Dell Precision 670 workstation
Dual Processors, 2.8 GHz Intel Xeon (hypertheading on)
4Gb Memory
SATA0 drive (Ubuntu)
SATA1 drive (XP Pro)
NVIDIA Quadro FX 540 Graphics Card
Dual monitor - both are Dell 1905FP monitors (one digital in, one analog in); this is just the nature of the video card outs[/I]

It boots up fine with XP as dual monitor, which is how I've had it configured the past three years.  Since installing Ubuntu this week (for dual-boot), when I try to boot into Ubuntu, my main monitor remains blank and the second monitor gives an error message saying there is no signal (or unplugged?). If I turn the second monitor off, the main monitor still does not work. The only way I can get a functional monitor is to unplug the video cable from the video card and start the computer from "off". Basically, the only way I am able to boot up Ubuntu is to unplug one of the monitors (either one) from the vid card and start/restart the computer.

I need help! I don't want to have to unplug/replug a monitor whenever I switch OS's. I shouldn't have to, right?!

---

### Post by conradinsf on 2008-01-17
> **conradinsf said:**
> Hi all,

I am having issues with my dual monitor setup with Ubuntu. I just completed a dual-boot system with XP Pro and Ubuntu (thanks to all the contributers). The video card is **NVIDIA QUADRA FX 540 **with a **dual monitor setup** (single desktop) with XP Pro, and it works fine.

My computer specs (in case it is needed) is the following:
[I]Dell Precision 670 workstation
Dual Processors, 2.8 GHz Intel Xeon (hypertheading on)
4Gb Memory
SATA0 drive (Ubuntu)
SATA1 drive (XP Pro)
NVIDIA Quadro FX 540 Graphics Card
Dual monitor - both are Dell 1905FP monitors (one digital in, one analog in); this is just the nature of the video card outs[/I]

It boots up fine with XP as dual monitor, which is how I've had it configured the past three years.  Since installing Ubuntu this week (for dual-boot), when I try to boot into Ubuntu, my main monitor remains blank and the second monitor gives an error message saying there is no signal (or unplugged?). If I turn the second monitor off, the main monitor still does not work. The only way I can get a functional monitor is to unplug the video cable from the video card and start the computer from "off". Basically, the only way I am able to boot up Ubuntu is to unplug one of the monitors (either one) from the vid card and start/restart the computer.

I need help! I don't want to have to unplug/replug a monitor whenever I switch OS's. I shouldn't have to, right?!

I am happy to say that I have resolved my problem.  I ran into a tool called SysInfo, which apparently can run a program to change NVIDIA VC settings.  This was a new tool that was included with Ubuntu 7.10, in response to Fedora's success with a dual-monitor configuration.  Now, I am happy with my dual-monitor setup.  

I will be posting a step-by-step manual on how to do this.  Unfortunately, I think this only applies to NVIDIA VC with NVIDIA nonfree drivers.

---

### Post by Bölvaður on 2008-01-17
Nice. I am happy for you that it all worked out.


You might also be able to use ```
nvidia-settings
```

---

### Post by alexsabree on 2008-04-07
I had the exact same problem with 7.10.

However I installed hardy heron and started from scratch. Make sure to get the latest drivers from nvidia, or install the nonfree drivers from the synaptic package manager. Once you have the latest drivers open up the nvidia settings (using command shown last post) and go thru all of the settings and enable "twin-view." once you reboot you should be able to use both at the same time.

Hope you fix your prob :)

---

