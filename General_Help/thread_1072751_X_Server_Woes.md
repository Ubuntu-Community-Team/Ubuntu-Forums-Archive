---
title: "X Server Woes"
date: 2009-02-17
forum: General Help
---

### Post by Jimoid on 2009-02-17
I am having big problems with X and needs some help to repair it.

First of all, I am running Ubuntu 8.04 with a nVidia GeForce 7600 GS graphics card. X had been working fine for a long time and I was happy. Then on Sunday I decided to try to get glx to work, as it has never worked on this installation. Anyway, that was a couple of days ago and I have wasted too much time trying to get it to work correctly again.

The quickest way for me to have a working X server again I believe would be to uninstall all xserver, plus all the kernel modules related to nvidia. I have 2 main questions about this however; (i) if I remove all nvidia modules/drivers will the command line still be available to me (i.e. will the monitor work!), and (ii) how do I remove all?

TIA

---

### Post by olskar on 2009-02-17
> **Jimoid said:**
> I am having big problems with X and needs some help to repair it.

First of all, I am running Ubuntu 8.04 with a nVidia GeForce 7600 GS graphics card. X had been working fine for a long time and I was happy. Then on Sunday I decided to try to get glx to work, as it has never worked on this installation. Anyway, that was a couple of days ago and I have wasted too much time trying to get it to work correctly again.

The quickest way for me to have a working X server again I believe would be to uninstall all xserver, plus all the kernel modules related to nvidia. I have 2 main questions about this however; (i) if I remove all nvidia modules/drivers will the command line still be available to me (i.e. will the monitor work!), and (ii) how do I remove all?

TIA

The commandline will still be avaible

The easiest way I guess would be opening synaptic and marking everything nvidia-related (called nvidiasomething) for total removal

---

### Post by Jimoid on 2009-02-17
Thanks olskar, I guessed the command line would be available, but doesn't hurt to ask.

To remove all apt-get installed packages I will use apt-get remove [package] and to remove the kernel modules depmod -r [module]

However is there anything else I need to do to remove any leftover bits and pieces?

---

### Post by Titan8990 on 2009-02-17
I think you are going too far too fast. Have you tried changing the line in your xorg.conf from:


Driver "nvidia"

to:

Driver "nv"

---

### Post by Jimoid on 2009-02-17
I have tried various things to get X working as it used to, but none have worked. I have tried (not necessarily in this order):

(i) installing the nvidia driver again;

(ii) tried installing through apt-get
apt-get update
apt-get install nvidia-glx-new
dpkg-reconfigure xserver-xorg
apt-get install --reinstall xserver-xorg

(iii) configuring nvidia
nvidia-xconfig 
nvidia-installer

(iv) removed and installed X
apt-get remove xserver-xorg
apt-get install xserver-xorg

(v) I also installed something called envyng and got it to download, install and configure drivers for me, but didn't work.

None of these actions have helped. I have tried many, many things (see below), and think complete reinstall will be the easiest and quickest.

---

