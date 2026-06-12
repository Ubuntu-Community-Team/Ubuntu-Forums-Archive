---
title: "Which kernel should I use?"
date: 2005-10-24
forum: Gaming &amp; Leisure
---

### Post by ramba on 2005-10-24
I installed cedega and cs yesterday and I tested it and the fps was kind a low. I checked my nvidia drivers, which are from synaptic, and Fast writes was off and NVagp didn't work, yet I have nForce3 motherboard so it should.

So the question is if compiling a new kernel would enable these options, which should be working. Which kernel would be best for gaming and high performance. Is there any other ways to fix the nvidia driver module so it would use FW and NVagp?

---

### Post by seethru on 2005-10-24
I believe there's a howto somewhere on here regarding fastwrites

---

### Post by ramba on 2005-10-24
I tried it but it didn't work. I guess I have to go for the new kernel to get the drivers working. Do I have to excluce the nvidia drivers possibly from the configuration of kernel and then compile the driver. Last time I tried compiling a kernel with defaults and then installing the 'bleeding edge' drivers of nvidia messed up Xorg so it didn't start. :confused:

---

### Post by aminalshmu on 2005-10-24
do a ```
cat /proc/driver/nvidia/agp/card
cat /proc/driver/nvidia/agp/host-bridge
```to make sure fastwrites/sba are supported by your card and mobo, then edit /etc/modprobe.d/nvidia-kernel-nkc and add the line
```
options nvidia NVreg_EnableAGPFW=1
```i don't know what the option is for SBA, probably just SBA instead of FW. it's enabled by default on my card. for this to take into effect you have to reload the nvidia module, so log out of your X session and stop gdm, ```
sudo /etc/init.d/gdm stop
``` and then ```
sudo rmmod nvidia
sudo modprobe nvidia
``` and then restart gdm ```
sudo /etc/init.d/gdm start
``` and voila. should work. do a ```
cat /proc/driver/nvidia/agp/status
``` to make sure it's enabled.

by the way, i'm using the latest 686 smp kernel for breezy and the matching linux restricted modules package or whatever for nvidia drivers. no need to compile kernel or any drivers to get this working, it's just a command for when the module is initialized.

---

### Post by ramba on 2005-10-24
Okay, great. I had manually created /etc/modprobe.conf file which had a wrong line setting up those settings so I removed it and put the line in the other file.

:KS Thanks! :KS

---

