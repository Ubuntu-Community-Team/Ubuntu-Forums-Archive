---
title: "Smp?"
date: 2005-11-06
forum: Desktop Environments
---

### Post by aaronshaf on 2005-11-06
My Ubuntu installation seems only to be using one CPU. How can I get it to use both?

Thanks for helping a newbie,

Aaron

---

### Post by RAOF on 2005-11-06
You need to install the smp kernel.

If you're running the 32bit breezy, you want one of the
"linux-smp", "linux-686-smp" (if you've got intel processors, pentium2 or better), or "linux-k7-smp" (if you've got AMD athlon processors, or better) packages.

If you're running 64bit breezy, you want either
"linux-amd64-k8-smp", if you've got amd processors, or "linux-amd64-xeon-smp" if you've got intel processors.

---

### Post by audax321 on 2005-11-06
You will have to install the linux-686-smp package using Synaptic for multiple processor support (it will automatically install all the appropriate packages). After installation and reboot, you can optionally remove the linux-386 kernel:

The packages to remove the 386 kernel should be:
linux-386
linux-image-2.6.12-9-386
linux-image-386
linux-restricted-modules-2.6.12-9-386
linux-restricted-modules-386

NOTE: Damn, got beaten to it.. but follow the above directions for 64-bit or AMD... these are only for 32-bit Intel.

---

### Post by aaronshaf on 2005-11-06
How do I get one of those packages?

---

### Post by RAOF on 2005-11-06
Through synaptic/apt-get.  There's a help page for installing stuff [here]("http://help.ubuntu.com/starterguide/C/ch02.html").

But briefly, at a console you want to run
```
sudo apt-get install linux-686-smp
``` to get the linux-686-smp package.

---

### Post by aaronshaf on 2005-11-08
Thank you so much... it worked!

---

