---
title: "Video Drivers / Visual Effects Problems"
date: 2009-03-18
forum: General Help
---

### Post by jdorenbush on 2009-03-18
I am not sure of the exact problem here, but here is a run down of the situation.

First I was having problems with those gnome black boxes that trail a window when minimizing. So I was trying to fix that (still haven't fixed).

I looked at my Appearance Preferences, Visual Effects and they were set to None, so I tried to switch -- didn't work because I didn't have my video driver setup or something.

So I went to Harddrive Drivers, and there was some NVIDIA drivers to choose from. I selected the recommended one and rebooted. It booted to a black screen. So I had to boot into Recovery Mode and do the option, "Try To Fix X Server". Then resume and it boots up fine, but I still can't enable Visual Effects and the Harddrive Drivers keep saying, "A different version of this driver is in use."

Any idea how to fix drivers and desktop effects?

---

### Post by RhysTheNewGuy on 2009-03-18
ok, uninstall all of your Proprietary drivers (the ones found in "hardware drivers")

next go to this page [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and choose from the drop-down menu your card type, for example a 7600GS would be GeForce 7 series, and your OS etc etc.

then click search, and scroll down the page till you reach the download button and click it.

it should download something along the lines of NVIDIA-Linux-x86-180.29-pkg1

then you may want to write down/print the following steps

hit ctrl-alt f2, this should take you to a black screen and will prompt you to login to <your computers name> do so as you would when logging in through the graphical interface.

you then want to type 
```
sudo /etc/init.d/gdm stop
```

it will then prompt you for your password, enter it and it will say 
GNOME Desktop Manager stopped or something like that.

Next, cd to the directory you saved the driver to, for example

```
cd Desktop
```

then you want to run 
```
sudo sh NVIDIA-Linux-x86-180.29-pkg1.run
```

It would be worth using <tab> to auto-complete the file name to avoid mistakes.

this should bring up a menu, use tab and enter to answer yes to everything until you reach the end of the setup menu.

then when the menu closes, type 
```
sudo /etc/init.d/gdm start
```

then it should take you back into your ubuntu screen, it would be a wise plan to reboot aswell.

you should now be able to change your Visual effects by installing 
```
sudo apt-get install compizconfig-settings-manager
```

if you have any problems please reply

---

### Post by jdorenbush on 2009-03-18
> **RhysTheNewGuy said:**
> ok, uninstall all of your Proprietary drivers (the ones found in "hardware drivers")

Ugh..this is probably a stupid question. How do I "uninstall" them?:redface:

---

### Post by jdorenbush on 2009-03-19
Anyone else? :\

---

### Post by RhysTheNewGuy on 2009-03-21
Sorry for the slow response :) 

in hardware drivers I believe if you highlight the driver currently installed then it will have a deactivate button, if not then I suggest a fresh install of ubuntu, and its smooth sailing.

its always worth a clean install if you are having trouble.

---

### Post by jdorenbush on 2009-03-25
> **RhysTheNewGuy said:**
> Sorry for the slow response :) 

in hardware drivers I believe if you highlight the driver currently installed then it will have a deactivate button, if not then I suggest a fresh install of ubuntu, and its smooth sailing.

its always worth a clean install if you are having trouble.

Fresh install of Ubuntu ftw. :)

---

### Post by norwoods on 2009-03-25
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
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

---

### Post by RhysTheNewGuy on 2009-03-26
if the problem is dealt with, please mark the thread as solved

(you can do this by clicking on thread tools and then "Mark as solved")

---

### Post by jdorenbush on 2009-03-26
I didn't really find a fix... I just re-installed Ubuntu.

---

