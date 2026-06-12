---
title: "Nvidia driver problem.."
date: 2009-03-22
forum: General Help
---

### Post by PetterDK on 2009-03-22
uHi!

First post here as user.. Make it a good one :)

Okay, so i have installed a new driver for my GPU, but having some problems. When i do 'nvidia-settings' the system tells me that:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Well i have tried this, but no luck.

I have searched the forum for a solution, but nothing helped..

Any help would be great!

---

### Post by taurus on 2009-03-22
Have you installed an nvidia driver for your graphic card and how did you install it?

System -> Administration -> Hardware Drivers

---

### Post by PetterDK on 2009-03-22
I downloaded the newest driver from nvidia.com which is 180.29..

I then did ctrl+alt+f1

sudo /etc/init.d/gdm stop

sudo sh /home/user/driver

sudo /etc/init.d/gdm start

ctrl+alt+f7

None of the drivers in System -> Administration -> Hardware Drivers are active..

---

### Post by taurus on 2009-03-22
Open a terminal and run

```
sudo nvidia-xconfig
```
Then, restart your X server with <Ctrl><Alt>Backspace.

---

### Post by PetterDK on 2009-03-22
Yep did that.. still:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by taurus on 2009-03-22
Reboot.

---

### Post by men28 on 2009-03-22
Try Envy.

---

### Post by mhgsys on 2009-03-22
> **PetterDK said:**
> I downloaded the newest driver from nvidia.com which is 180.29..

I then did ctrl+alt+f1

sudo /etc/init.d/gdm stop

sudo sh /home/user/driver

sudo /etc/init.d/gdm start

ctrl+alt+f7

None of the drivers in System -> Administration -> Hardware Drivers are active..

Well,If you see them, can't you make them active by clicking on it?

Edit: Try to reboot first, like taurus also mentioned

---

### Post by PetterDK on 2009-03-22
Ok..

Before the login screen comes, a window shows up saying:

"The following error was encountered. You may need to update your configuration to solve this.

(EE) Failed to load module "type1" (module does not exist, 0)
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
Please ensure
(EE) NVIDIA(0): that there is a supported NVIDIA GPU in this
system, and
(EE) NVIDIA(0): that the NVIDIA device files have been
created properly.
(EE) NVIDIA(0): Please consult the NVIDIA README for details.
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration."

---

### Post by PetterDK on 2009-03-22
> **mhgsys said:**
> Well,If you see them, can't you make them active by clicking on it?

Edit: Try to reboot first, like taurus also mentioned

The drivers i can see is not 180.29.. only 96, 173 and 177..

---

### Post by taurus on 2009-03-22
Which model of nvidia card do you have?  

Does it drop you into a console with a login prompt?  If it does, try to log in with your username and password, then run 

```
sudo nvidia-xconfig
```

---

### Post by mhgsys on 2009-03-22
whoops. allready did that

---

### Post by men28 on 2009-03-22
```
apt-get install envyng-gtk
```

It helped me in similar situation very match.

---

### Post by PetterDK on 2009-03-22
> **taurus said:**
> Which model of nvidia card do you have?  


It's an 7900 GT/GTO

---

### Post by PetterDK on 2009-03-22
> **men28 said:**
> ```
apt-get install envyng-gtk
```

It helped me in similar situation very match.

Tried that, but no luck.. exactly the same problem.

---

### Post by PetterDK on 2009-03-22
Is there a way to remove all drivers that i have installed and reverting to the original state? This way i can try again from scratch..

---

### Post by verlyn13 on 2009-03-23
I am looking to do the same thing.  How can ALL remnants of existing drivers be removed/uninstalled so that it will not conflict with 180.29?

I have a 9800 GTX and have similar problems trying to install the new driver.  In fact, I always have problems installing the new drivers when they are released and usually have to reinstall my entire system.  Very annoying.

---

### Post by Nano_ext3 on 2009-03-23
See my blog entry:  [http://thelinuxcauldron.wordpress.com/2009/03/17/how-to-session-installing-your-nvidia-or-ati-card/](http://thelinuxcauldron.wordpress.com/2009/03/17/how-to-session-installing-your-nvidia-or-ati-card/)

Instructions on how to install EnvyNG.  Should work like a charm
Cheers!

_Nano

---

### Post by PetterDK on 2009-03-23
I just tried EnvyNG.. First did an uninstall then an install of 180.11.. everything seem to work fine, no forced 'low graphics mode' at boot or anything, but when i do nvidia-settings it still says

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

This is getting annoying :S

---

### Post by norwoods on 2009-03-23
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

then open System--Administration--Hardware Drivers.
if there is an active video driver, click on it and then click Deactivate
click on the NVIDIA 180 driver
click Activate.
clock Close.

reboot

---

### Post by Miaxi on 2009-03-23
180.17 worked without problems for me. 180.29 gave the same errors as you have. You can get the older version from the driver archives at nvidia.com.

---

### Post by PetterDK on 2009-03-24
> **norwoods said:**
> i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

then open System--Administration--Hardware Drivers.
if there is an active video driver, click on it and then click Deactivate
click on the NVIDIA 180 driver
click Activate.
clock Close.

reboot

Will try this when i get home, but i'm quite sure i have tried this..

---

### Post by PetterDK on 2009-03-24
Miaxi ->

So how did you revert to that older driver when you already had 180.29 installed?

EnvyNG?

---

### Post by Nano_ext3 on 2009-03-24
If you need to add a third party PPA , or software source, see my blog :

[http://thelinuxcauldron.wordpress.com/2009/03/24/how-to-session-open-your-minderr-system-changing-your-ubuntu-software-sources/](http://thelinuxcauldron.wordpress.com/2009/03/24/how-to-session-open-your-minderr-system-changing-your-ubuntu-software-sources/)

Cheers,

_Nano

---

### Post by tad1073 on 2009-03-24
> **Miaxi said:**
> 180.17 worked without problems for me. 180.29 gave the same errors as you have. You can get the older version from the driver archives at nvidia.com.

Did you deactivate the 180.17 driver before you installed 180.29?

---

### Post by PetterDK on 2009-03-31
Okay.. Problem solved by using EnvyNG to remove the nvidia drivers, then installing the 180.17 driver by first dropping to ctrl+alt+F1, stopping gdm, sh the driver and then reboot..

Guess it was a problem with 180.29

---

