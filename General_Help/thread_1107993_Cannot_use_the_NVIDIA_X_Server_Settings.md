---
title: "Cannot use the NVIDIA X Server Settings"
date: 2009-03-27
forum: General Help
---

### Post by victorliang on 2009-03-27
Hi,

I meet a problem when i install the NVIDIA driver on Ubuntu 8.10.

Laptop: ASUS W7SG
System: Ubuntu 8.10
Graphic: NVIDIA GeForce 9300M G
Driver: NVIDIA-Linux-x86-180.29-pkg1.run

I have successfully installed the NVIDIA driver as root. But when i restart the X Server after finishing installing the driver, the error message shows: 

------------------------------------------------------------
(EE) Failed to load module "type1" (module does not exist,0)
(EE) Failed to load module "xgl" (module does not exist, 0)
(EE) NVIDIA(0) Failed to load the NVIDIA Kernel Module
(EE) NVIDIA ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.
------------------------------------------------------------

Also when i open the NVIDIA X Server Settings, the message shows:
-------------------------------------------------------------
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
-------------------------------------------------------------
Even i run the nvidia-xconfig, it still cannot work.
Anyone could give me some solutions? Thank you so much.

---

### Post by James_Lochhead on 2009-03-27
1) 

Open Applications > Accessories > Terminal.

2) 

Type: 
```
sudo nvidia-xconfig
```
Then press enter.

3)

If an error occurs post it here, otherwise try NVidia X Server Settings.

---

### Post by James_Lochhead on 2009-03-27
I also notice that you have installing using the run script off the NVidia website.

It is is better to use the driver from the repositories as it will not break when you upgrade your kernel.

If you wait just a month until Jaunty comes out then you can install the 180.37 drivers.

---

### Post by stukpixel on 2009-03-27
> **victorliang said:**
> Hi,

I meet a problem when i install the NVIDIA driver on Ubuntu 8.10.

Laptop: ASUS W7SG
System: Ubuntu 8.10
Graphic: NVIDIA GeForce 9300M G
Driver: NVIDIA-Linux-x86-180.29-pkg1.run

I have successfully installed the NVIDIA driver as root. But when i restart the X Server after finishing installing the driver, the error message shows: 

------------------------------------------------------------
(EE) Failed to load module "type1" (module does not exist,0)
(EE) Failed to load module "xgl" (module does not exist, 0)
(EE) NVIDIA(0) Failed to load the NVIDIA Kernel Module
(EE) NVIDIA ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.
------------------------------------------------------------

Also when i open the NVIDIA X Server Settings, the message shows:
-------------------------------------------------------------
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
-------------------------------------------------------------
Even i run the nvidia-xconfig, it still cannot work.
Anyone could give me some solutions? Thank you so much.

I'm having the same issue, the only differenece is that the error message does not say "(EE) Failed to load module "xgl" (module does not exist, 0)"

How would you use a repository in command line when you have killed x (/.etc/init.d/gdm stop) ?

---

### Post by victorliang on 2009-03-27
> **James_Lochhead said:**
> 1) 

Open Applications > Accessories > Terminal.

2) 

Type: 
```
sudo nvidia-xconfig
```
Then press enter.

3)

If an error occurs post it here, otherwise try NVidia X Server Settings.

Acutally, I have tested "sudo nvidia-xconfig". The same error occurs when i open X Server Settings.

---

### Post by victorliang on 2009-03-27
Does anyone meet the same problem??

---

### Post by norwoods on 2009-03-27
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

---

### Post by victorliang on 2009-03-27
> **norwoods said:**
> i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

much thanks for your information. Does that work on your computer?

---

### Post by norwoods on 2009-03-27
it works well and is easy.  180.29 ran glxgears more slowly on my system but the last few upgrades have been easy and convenient, except for the file size on my dialup line.

---

