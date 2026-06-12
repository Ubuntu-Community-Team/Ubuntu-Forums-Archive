---
title: "No display when booting to Kubuntu after Windows upgrade"
date: 2021-01-15
forum: Desktop Environments
---

### Post by LotsOfStuff on 2021-01-15
Hi, I have another emergency on a dual boot...

After Windows forced an upgrade, I no longer get a display in Kubuntu 18.04.  I fixed the [COLOR=#373737][FONT=&quot]SATA Operation mode back to AHCI after the upgrade, but I after I boot into Kubuntu, I see the Kubuntu logo, and then... blank.

The other relevant thing I can think of is that I had been playing with running some neural network software on my GPU prior to the boot into Windows, so I guess it's possible I messed up something with the drivers.

I can boot into recovery mode, but after I exit that, it only displays a few white pixels in the top left of my screen.  From there if I hit the power button, it prints a bunch of statements in the shut down sequence before shutting down.

Any suggestions on how to troubleshoot this?[/FONT][/COLOR]

---

### Post by yancek on 2021-01-15
I don't see how a windows update would affect the GUI/Graphics on your Kubuntu install as they are totally separate operating systems.  Common problems with windows upgrades are turning on Secure Boot and hibernation but if you can boot Kubuntu, that doesn't seem to be the issue.

>  [COLOR=#373737][FONT=&amp]I had been playing with running some neural network software on my GPU prior to the boot into Windows[/FONT][/COLOR]

That seems more likely to be the cause of the problem.  Review your notes on what exactly you did and post some of that information here to try to get help.

---

### Post by LotsOfStuff on 2021-01-15
Thanks, that makes sense.

I was able to find the instructions I was trying to follow.  I was trying to give GPU access to code running in a Docker container, so I installed nvidia-docker: [https://github.com/NVIDIA/nvidia-docker](https://github.com/NVIDIA/nvidia-docker)

If believe I was trying to follow these steps here:
[https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#setting-up-nvidia-container-toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#setting-up-nvidia-container-toolkit)

and these here:
[https://docs.nvidia.com/datacenter/tesla/tesla-installation-notes/index.html#ubuntu-lts](https://docs.nvidia.com/datacenter/tesla/tesla-installation-notes/index.html#ubuntu-lts)
Although I don't think I did the post-installation steps.

Any ideas from those links?

---

