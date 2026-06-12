---
title: "Huge nvidia re-install problem"
date: 2009-03-10
forum: General Help
---

### Post by sha.goyjo on 2009-03-10
I've been trying to install the nvidia restricted drivers for about a week now.I've tried most of the common options, and uninstalled and reinstalled more times than I can think. I've tried:

envyng (from the repos)
Hardware drivers (nvidia-glx-180)
Synaptic (nvidia-glx-180 metapackage)
Nvidia installer (180.29)

Running 64 bit with a geforce 6400go

The error with the first three methods is that xorg cannot find a compatible nvidia driver.

The nvidia installer produces a whole slew of errors saying that I don't have a compatible gpu.

any advice?

---

### Post by taurus on 2009-03-10
Have you tried the version 177 in System -> Administration -> Hardware Drivers because I have 6800XT and don't have any problem running that driver on my machine.

---

### Post by sha.goyjo on 2009-03-10
Sorry, I should clear that up. This error holds for all versions of the nvidia-glx driver. I had this working a bit ago, so I know it works with my system, But I was trying to enable my tablet functions in xorg.conf and futzed it. I'm now using the debconf, but everytime I re-install the drivers (and consequently alter my xorg.conf) I get one of those errors again. As I said before, I have scoured the forums (and google) for a solution. I am looking for NON-TYPICAL solutions to this problem.

---

### Post by fcuk112 on 2009-03-10
this worked for me -

download latest driver from nvidia.com.
open up synaptic package manager, search for nvidia and remove all packages.
type modprobe -l | grep nvidia and remove all .ko files

ctrl-alt-f1 to enter terminal
sudo killall gdm
sudo sh NVIDIAxxx.run
startx

---

