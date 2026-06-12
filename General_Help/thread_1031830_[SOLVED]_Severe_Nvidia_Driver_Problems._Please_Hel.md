---
title: "[SOLVED] Severe Nvidia Driver Problems. Please Help"
date: 2009-01-05
forum: General Help
---

### Post by Valok on 2009-01-05
Earlier today I decided that I would try to install the nvidia 180.11 drivers.  But all it did was mess everything up.  When I booted up I had to mannually configure my driver and monitor setup, and after that I still wasn't able to get things going the way it was before.

So the stage I'm at now is I have the following nvidia packages installed.

```
v   nvidia-kernel-1.0.7184          -                                           
v   nvidia-kernel-1.0.8774          -                                           
v   nvidia-kernel-169.12            -                                           
v   nvidia-kernel-71.86.04          -                                           
v   nvidia-kernel-96.43.05          -                                           
i A nvidia-kernel-common            - NVIDIA binary kernel module common files  
p   nvidia-kernel-source            - NVIDIA binary kernel module source        
p   nvidia-kernel-source-envy       - NVIDIA binary kernel module source
```

I'm still having the problem where I can't turn on any graphic effects and can't change the desktop resolution any higher than 800x600.  Is there a way I can just globally un install all the nvdia drivers and settings then re install and have it running just like I was when I first installed Ubuntu?

Pretty crippling at the moment so I'd love any help people can offer.

---

### Post by blazemore on 2009-01-05
Go to Synaptic and search for nvidia. Uninstall everything.
Then use the official ubuntu method of stable driver installation, to install nvidia driver 177 or 173. (Administration - > Hardware drivers)

---

### Post by Valok on 2009-01-05
For some reason when I got to the Hardware Drivers page it doesn't have any options to chose from like it normally did.  Am I missing something else that would cause that to show up?

Also note that even after completely removing everything nvidia from synaptic, I still get the same return as above when doing

sudo aptitude search nvidia-kernel

---

### Post by mcloer on 2009-01-05
I am having the same issue.  Please help....

---

### Post by Valok on 2009-01-05
I was able to figure it out!

Simply run the command 

```
sudo apt-get install envyng-gtk
```

Then once that if finished go to Applications >>> System Tools >>> EnvyNG

Once you get that screen up just select which video card type you are using (ATI or Nvidia) and click the 'apply' button and vwala!

Just had to restart my computer and everything is back to normal with the Nvidia 173 series driver.

---

