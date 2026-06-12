---
title: "Nvidia drivers not loading after 16.04-&gt;18.04"
date: 2018-05-12
forum: Desktop Environments
---

### Post by derekcentrico on 2018-05-12
Well, everything has been decent after the big upgrade until I tried to do some Steam gaming and noticed my NVIDIA dedicated GPU wasn't loaded.  So, I started toying around to try to fix it.  Purged and reinstalled latest drivers to no avail.  I am not using Wayland which I know had a support issue with NVIDIA at least in 17.10 which I was not using.

~$ nvidia-settings 
ERROR: NVIDIA driver is not loaded
ERROR: Unable to load info from any available system

~$ lsmod | grep nvidia
~$ lsmod | grep nouveau
nouveau              1716224  5
ttm                   106496  1 nouveau
mxm_wmi                16384  1 nouveau
wmi                    24576  4 asus_wmi,wmi_bmof,mxm_wmi,nouveau
i2c_algo_bit           16384  2 nouveau,i915
drm_kms_helper        167936  2 nouveau,i915
drm                   401408  26 nouveau,i915,ttm,drm_kms_helper
video                  40960  3 asus_wmi,nouveau,i915




The additional drivers section shows that it is using NVidia driver metapackage from nvidia-driver-396.

I had nvidia-390 installed originally when I upgraded from 16.04 and purged it out.

Any help would be greatly appreciated.  Thanks!

---

### Post by dino99 on 2018-05-12
There are some known issues with the latest published nvidia drivers; better trying <390 depending on your graphic stack (im neither sure about the used kernel able to support the latest nvidia drivers correctly)

If you was a noob, i probably asked you checking about built-essential & kernel headers installation, but it cant be that dont you :o

And as usual after a dist-upgrade, cleaning the system via gtkorphan & bleachbit (as root, carefully select options) is a good idea.

---

### Post by derekcentrico on 2018-05-12
Noob fun.  Yeah, so turns out there is something new and annoying.  I blacklisted the Nouveau drivers in the kernel, purged NVIDIA* again, and installed nvidia-390 for the 3rd time.  It now functions.  So, anyone out there having issues on 18.04 be sure to blacklist nouveau drivers from loading in the kernel.

---

### Post by dnamurphy on 2018-05-16
Adding a "me too" here - I just cannot get these drivers to load.

I've disabled wayland via /etc/gdm3/custom.conf
I've blacklisted nouveau, lbm-nouveau
I've installed nvidia-390 via the standard repo
I've purged that, installed nvidia-396 via the nvidia ppa

Each time I install an nvidia driver, it loads nouveau - I see it via lsmod and lshw

Infuriating. Any ideas?

Ubuntu 18.04 w/ xfce also installed
NVIDIA GTX 750Ti

---

### Post by wildmanne39 on 2018-05-16
Hello dnamurphy, please start your own thread instead of posting in another members thread, especially one that is solved that way you are much more likely to get the help you need.

Thanks

---

### Post by derekcentrico on 2018-05-16
Two things assuming you blacklisted correctly:

1.  on your login page click the gear and be sure the option selected does not indicate wayland.
2.  apt-purge nvidia*; re-add the ppa for nvidia proprietary drivers; apt install nvidia-390

I'm using the PPA for 390 which I think is newer (had an incremental update later on if I remember correctly) without issue.

---

### Post by kaushiksv on 2018-05-20
Noob here. Take my words with a grain of salt. I think NVIDIA doesn't yet support 18.04 officially.

Once I couldn't login to my desktop. X-server failed to start and I could see errors that no driver was found. Turns out that nouveau was loaded despite the existence of correct /etc/modprobe.d/blacklist-nouveau.conf file. I tried sudo update-initramfs and rebooted the computer. Got back my desktop. I'm using v390.48 for GeForce GTX 1060 3GB

---

### Post by cyberalex4life on 2018-07-17
Just be sure not to have any ```
/etc/X11/xorg.conf*
``` files.
Run this:
```
sudo rm -v /etc/X11/xorg.conf*
```
and reboot.
I had this problem recently on Ubuntu 18.04, and while being on intel, I ran
```
nvidia-xconfig
```
then
```
sudo prime-select nvidia
```
and rebooted; but gdm would no longer load. So I booted on an USB live image and noticed two /etc/X11/xorg.conf* files which I removed (one empty and the nvidia-xconfig file backed up). Then rebooted again and I could log in having nvidia driver perfectly working. 

Maybe this will help.

---

