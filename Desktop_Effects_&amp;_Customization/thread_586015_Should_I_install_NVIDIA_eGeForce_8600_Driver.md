---
title: "Should I install NVIDIA eGeForce 8600 Driver?"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by harsh2209 on 2007-10-21
Hi Friends,

I installed Ubuntu 7.10. I have NVIDIA eGeForce 8600 GT Graphics card. After installation I checked for the updates. In the Software sources I checked Canonical and Universal source.  I installed the ‘sudo aptitude install build essential’. Then went to restricted drivers window and I saw two: NVIDIA graphics card (latest drivers) and my wireless PCI card WMP54GS bcm43xx. I enabled them. Amazingly they were enabled.

My question is that is it necessary for me to go ahead and install NVIDIA drivers from the NVIDIA site. Compiz and emerald does work without it. Would installation of the driver in question improve some performance like looks etc.?

---

### Post by ezak on 2007-10-21
I would certainly suggest installing the latest update from the Nvidia site due to the various compatibility fixes and micro updates for the newer 8xxx series cards. The restricted Nvidia drivers that show up in Ubuntu updates are, for the most part, stable as in "they work on almost all system configs" Latest drivers aren't usually "as stable" but the do indeed tend to give you better performance. Without a doubt they will be included in the next package update for restricted drivers anyway. 

Here is the link to the latest linux x86 drivers:

[http://www.nvidia.com/object/linux_display_ia32_100.14.23.html](http://www.nvidia.com/object/linux_display_ia32_100.14.23.html)

---

### Post by harsh2209 on 2007-10-22
Hi ezak,

I did install the latest x 86 drivers '100-14.23'. I installed successfully. Before installing this the state of the OS was:-

Nvidia-glx-new: enabled
bcm 43xx (fwcutter): enabled
build-essential installed.

I went to channel 1 (ctrl+alt+F1), logged in as root and installed the latest NVIDIA driver. As soon as I ran ‘sudo /etc/init.d/gdm restart’ (because I stopped it before installing driver):-

I hear a beep.
System restarts process goes on and stops and Running boot scripts. It blinks 3 times.
Then, I see a message 'Ubuntu is running in low graphics mode'. This message has two tabs. Reslution and for graphics card.
Even after selecting the right monitor, resolution and graphics card the resolution doesn't change.
I login to ubuntu anyway. Then got to Application-NVIDIA tool. It says ‘It seems you aren't running the nvidia xconfig server. Type nvidia-xconfig in the terminal.’. It doesn't help either. 

So, basically the driver never loads up. Any light?

---

### Post by ezak on 2007-10-22
Let's see, did you let the Nvidia driver panel configure your xorg.conf for you when you were installing the latest driver or did you manually go in and change it yourself? I generally tend to let it configure for me, due to the same result you had. 
Another thing, have you went into nvidia-settings and configured your display modes/resolution after logging in as well?

Also, check to see in Restricted Drivers Manager to see if they are enabled.

If you have tried the above, with still no results,then i would simply revert back to the latest nvidia-glx-new ubuntu package in restricted.  

I am interested to see the output of the situation here.

---

