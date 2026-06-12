---
title: "Cannot install nvidia-glx-new drivers - no 3D yet"
date: 2007-10-29
forum: Desktop Effects &amp; Customization
---

### Post by geovino on 2007-10-29
Since my upgrade to Gutsy I haven't been able to install the nvidia-glx-new drivers. Here's the error message:

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb: subprocess pre-installation script returned error exit status 2

I can't install the nvidia-glx either. What is causing that it not to install?

How do I find out what video drivers are installed now? The upgrade had me intially reboot in a safe mode with bad graphics and then I found the Screens and graphics preferences and set the monitor to Samsung SyncMaster 910v (mine is 914v) and the graphics card to  nvidia geforce6. That got the screen to look good and clear, but I still can't install the nvidia drivers to makek the special effect work. Do I have to do a clean install of Gutsy to fix this problem? I can see now that these version upgrades can cause problems. Also most of the screensavers don't work. maybe it's related. Any clues? I can't be the only one with this problem. :confused:

---

### Post by Zorael on 2007-10-29
Have you tried Envy? It's a script installer for Nvidia and ATI drivers.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

New versions coming out pretty regularly, but no repository for it yet, I believe.

---

### Post by geovino on 2007-10-29
I did try Envy and it didn't work at the time. 

At this point I've given up on fixing this video problem, many of you have tried, but nothing has worked. One day I'll do a clean install of Gutsy, but for now most everything works except no nvidia drivers for 3D and no Amarok, it died and most screensavers don't work either.  Odd mix of broken parts from this version upgrade.

---

### Post by erginemr on 2007-10-29
Had you installed your NVidia drivers while you were running in Feisty from the repositories of from the NVidia web page? (It matters if the latter was the case, because you may need to explicitly remove and purge the former NVidia driver from your system.)

---

### Post by geovino on 2007-10-29
> **erginemr said:**
> Had you installed your NVidia drivers while you were running in Feisty from the repositories of from the NVidia web page? (It matters if the latter was the case, because you may need to explicitly remove and purge the former NVidia driver from your system.)

I think I installed the Nvidia drivers in Feisty via Envy. I did not go to the Nvidia web page.

---

### Post by froy02 on 2007-10-29
I installed the nvidia drivers glx new from synaptics package manager.  I de-selected the old ones and selected the new ones for installation.  I clicked apply then they were installed.

---

### Post by erginemr on 2007-10-30
Please follow this thread:
[http://ubuntuforums.org/archive/index.php/t-436240.html](http://ubuntuforums.org/archive/index.php/t-436240.html)

The error message given there is exactly the same as geovino's. 
Maybe it will help...

---

### Post by geovino on 2007-10-30
> **froy02 said:**
> I installed the nvidia drivers glx new from synaptics package manager.  I de-selected the old ones and selected the new ones for installation.  I clicked apply then they were installed.

Here's a screenshot of my Synaptic. This may help to see what I have and what needs to be changed.

---

