---
title: "Driver Problems"
date: 2009-04-10
forum: General Help
---

### Post by Musicologynut85 on 2009-04-10
I'm trying to get my Ubuntu set up, and I cannot get my computer to detect any drivers. It is currently running on the VERSA driver. Again, "System->Administration->Hardware Drivers" is empty of anything. I have updated and installed both "Nvidia Server Settings" and "Nvidia binary X.Orgdriver (version 177)" and rebooted after installation.


Various outputs that I know I will be asked for:


```
lspci | grep VGA
```

VGA Compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 

```
nvidia-xconfig
```

This gives several warnings and ends with "ERROR: Unable to write to directory '/etc/X11'"

```
./compiz-check
```

"ERROR: No rendering method in use"
"The Versa driver is not capable of running Compiz, you need to install the proper driver for your graphics card."

Asking it to check if there is an alternate driver results in the aforementioned empty list.



Would someone be so kind as to tell me what I've missed and what I need to do to get the drivers working?

Thanks...

---

### Post by Thura on 2009-04-10
Make sure you Graphics card is NVIDIA ...
If you already installed the drivers, run "sudo nvidia-xconfig" ... **you need sudo** !!!

---

### Post by Musicologynut85 on 2009-04-11
*headdesk*

I should not be using NVidia, after all. I think I found the driver,"xserver-xorg-video-intel" but I'm not sure how get my computer to use it. I've tried reinstalling it from synaptic, but it still will not register under the "hardware manager."

How do I get Ubuntu to use the Intel driver and not the Vesa driver?

---

### Post by Musicologynut85 on 2009-04-11
So, I'm stupid...

I had installed the Ubuntu in "safe graphics mode."

Everything is fine now...

*headdesk*

---

