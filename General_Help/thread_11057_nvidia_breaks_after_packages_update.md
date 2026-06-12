---
title: "nvidia breaks after packages update"
date: 2005-01-13
forum: General Help
---

### Post by Chokableu on 2005-01-13
Hi!
I'm experiencing an ongoing problem with Nvidia. I installed the Nvidia driver sometime ago (with synaptic using the Ubuntu repositories), and it's works well. The following guide was very useful [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto).
However, now and then, the X server fails at boot up after, ( i think it always happens after I did some udpgrades with Synaptic, but i can't be sure ). In the text terminal, I do the following command 
sudo dpkg-reconfigure xserver-xfree86
all parameters I previously entered are there, so I change nothing . After the last screen, I reboot, and all is OK again.
So what do you think that means? (I have a geforce FX5700 graphics card and a logitech 3wheel optical mouse and my kernel is 2.6.8.1-4-686).
Thanks in advance.

---

### Post by Chokableu on 2005-01-13
[QUOTE=Chokableu]Hi!
I'm experiencing an ongoing problem with Nvidia. I installed the Nvidia driver sometime ago (with synaptic using the Ubuntu repositories), and it's works well. The following guide was very useful [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto).
However, now and then, the X server fails at boot up after, ( i think it always happens after I did some udpgrades with Synaptic, but i can't be sure ). In the text terminal, I do the following command 
sudo dpkg-reconfigure xserver-xfree86
all parameters I previously entered are there, so I change nothing . After the last screen, I reboot, and all is OK again.
So what do you think that means? (I have a geforce FX5700 graphics card and a logitech 3wheel optical mouse and my kernel is 2.6.8.1-4-686).
Thanks in advance.[/QUOTE]

A precision : i never use Hoary, just Warty.

---

### Post by Rotarychainsaw on 2005-01-13
What error do you get?

---

### Post by magnus on 2005-01-20
yea, same problem
i'm running warty (amd64) with a FX5600 and my xserver hangs about 10 seconds after i get the login prompt
this only happened after i ran 

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable

i get some weird thing at boot about maybe needing to upgrade my bios and something about not being able to read my hardware clock, could it be that?

when it crashes i don't get any error messages or anything, everything stops responding except the mouse.

help

---

