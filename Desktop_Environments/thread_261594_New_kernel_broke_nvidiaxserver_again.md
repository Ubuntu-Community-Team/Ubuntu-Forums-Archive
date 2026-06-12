---
title: "New kernel broke nvidia/xserver again"
date: 2006-09-20
forum: Desktop Environments
---

### Post by trzmiel on 2006-09-20
Hello,

I know there's a couple of similar topics in the forum, but none of those seem to solve my problem. So I'm starting a new topic, hoping to get a more personalized support.

When installing (kernel 2.6.15-23), I've had serious problems with displaying anything using nv driver. Needed to install nvidia-glx, which seems to work properly (I have GF6600).

After upgrading to 2.6.15-26 (missed 25), it became impossible to start xserver. Now I upgraded to 2.6.15-27, and still can't start xserver on neither this 27 build, nor on older 26. The message is obviously "FATAL: module nvidia not found".

All packages are up to date, including linux-restricted-modules (at least adept/synaptic/apt say so).

Any clues on where to start?

---

### Post by cmost on 2006-09-20
Reinstall nvidia-glx.

---

### Post by kick6 on 2006-09-20
```
 sudo apt-get install nvidia-glx
```


should get you up and running.  If you installed the nvidia drivers using a different method, the updater didn't "know" that they needed to be updated with the kernel.

---

### Post by jpkotta on 2006-09-20
> **trzmiel said:**
> Hello,

I know there's a couple of similar topics in the forum, but none of those seem to solve my problem. So I'm starting a new topic, hoping to get a more personalized support.

When installing (kernel 2.6.15-23), I've had serious problems with displaying anything using nv driver. Needed to install nvidia-glx, which seems to work properly (I have GF6600).

After upgrading to 2.6.15-26 (missed 25), it became impossible to start xserver. Now I upgraded to 2.6.15-27, and still can't start xserver on neither this 27 build, nor on older 26. The message is obviously "FATAL: module nvidia not found".

All packages are up to date, including linux-restricted-modules (at least adept/synaptic/apt say so).

Any clues on where to start?

Is linux-restricted-modules up to date in the sense that the version matches the kernel version?

---

### Post by Robor on 2006-09-20
Same thing happened to me with my ATI card.  I'm getting so sick of this crap with Ubuntu.  I'm newish to Linux so don't know if this is 'a Linux thing' and happens in other distros as well or if it's just Ubuntu.  If it's the latter I'll be switching sooner rather than later...   ](*,)

---

### Post by kick6 on 2006-09-20
In my experience most linux distros don't have an automatic update feature, and if they do, its only for very "core" packages.

---

### Post by Beaucephus on 2006-09-20
> **Robor said:**
> Same thing happened to me with my ATI card.  I'm getting so sick of this crap with Ubuntu.  I'm newish to Linux so don't know if this is 'a Linux thing' and happens in other distros as well or if it's just Ubuntu.  If it's the latter I'll be switching sooner rather than later...   ](*,)
The automatic update thing is new. This is the only distro Ive seen it in. In my opinion kernel upgrades are inappropriate for automatic updates.  Kernel upgrades should not be taken as lightly as the automatic windows updates people are accustomed to. 

My idea would be to list the kernel upgrades that are available but not have them selected for automatic download.  That would at least increase awareness of kernel upgrades.

---

### Post by Atomic Dog on 2006-09-20
> **Beaucephus said:**
> The automatic update thing is new. This is the only distro Ive seen it in. In my opinion kernel upgrades are inappropriate for automatic updates.  Kernel upgrades should not be taken as lightly as the automatic windows updates people are accustomed to. 


I agree.  I learned this lesson a while ago.

---

### Post by zippy028 on 2006-09-22
I generally do not use an X based program to due any major updates such as kerenl, Xorg, and even major Gnome updates. I go to a terminal session (?) kill X and then; "sudo apt-get update" "sudo apt-get upgrade". I have had very positive results using this process, YMMV. I do not claim to know if their is any real benefit to this but it was something a more experienced user I met told me is good practice.

John Wheat

---

### Post by Gillingham on 2006-09-22
> **jpkotta said:**
> Is linux-restricted-modules up to date in the sense that the version matches the kernel version?

Which meta-package do I need to install to make sure I get the right ristricted modules?

I upgraded yesterday and found that while I'm sure I saw the restricted modules was being upgraded apparently it was the wrong version, which was easily fixed, but annoying (I'm using the 686 kernal and an nvidia 6600Gt card).

---

### Post by bioborg on 2006-09-30
The kernel update will always break the Nvidia driver, I think...
maybe change to the nv driver first, to make your experience even nicer...

But here's what I do:

I use automatix to simplify the experience.
Upgrade kernel.  Reboot.  Xserver crashes.
now, when I get to the terminal, I type:

dpkg-reconfigure xserver-xorg

and walk thru that process, selecting nv for driver,
hitting enter the rest of the time.

Then, when I boot into ubuntu, I run automatix, tell it to install the nvidia drivers, let it do its thing, reboot, and voila!

---

### Post by Beaucephus on 2006-10-28
> **zippy028 said:**
> I generally do not use an X based program to due any major updates such as kerenl, Xorg, and even major Gnome updates. I go to a terminal session (?) kill X and then; "sudo apt-get update" "sudo apt-get upgrade". I have had very positive results using this process, YMMV. I do not claim to know if their is any real benefit to this but it was something a more experienced user I met told me is good practice.

John Wheat

I think going to the terminal is good practice for all.  I cant imagine trying to actually learn how linux works with all of this automation.  I learned in the slackware distro which forces you to build your system up from the command line.  Its a serious PITA and not for everyone, but Im better for it.

KERNEL UPDATES WILL ALWAYS BREAK X WHEN USING NVIDIA DRIVER

When updating the kernel make sure you have the restricted kernel modules for that kernel version and just reinstall the driver.  This would happen in any distro.

---

