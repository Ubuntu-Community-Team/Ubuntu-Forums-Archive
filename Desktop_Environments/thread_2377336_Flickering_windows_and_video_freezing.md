---
title: "Flickering windows and video freezing"
date: 2017-11-12
forum: Desktop Environments
---

### Post by beardybear on 2017-11-12
Hello, 

I have recently updated for Ubuntu 17.10, I have the following issues since then:
[LIST=1]
[*]- Windows flickers when I open/resize them, with a thick black lines blinking around them 
[*]- After a while, videos tend to freeze the computer. The mouse/keyboard are no more responding, although the sound is still playing. 
[/LIST]

I am using the new default Gnome desktop, and also I do not have a super fancy graphic card, I don't think my problems are related to a lack of resources:
```
sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       produit: 4th Generation Core Processor Family Integrated Graphics Controller
       fabriquant: Intel Corporation
       identifiant matériel: 2
       information bus: pci@0000:00:02.0
       version: 06
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       ressources: irq:32 mémoire:f7800000-f7bfffff mémoire:e0000000-efffffff portE/S:f000(taille=64) mémoire:c0000-dffff
```

I followed the instructions on these threads:
[LIST]
[*][https://ubuntuforums.org/showthread.php?t=1405260&p=10342739#post10342739](https://ubuntuforums.org/showthread.php?t=1405260&p=10342739#post10342739) 
[*][https://askubuntu.com/questions/803640/system-freezes-completely-with-intel-bay-trail/803649#803649](https://askubuntu.com/questions/803640/system-freezes-completely-with-intel-bay-trail/803649#803649) 
[/LIST]

 but it did not fix the issue. In particular, I cannot use gstreamer-properties since gnome-video does not seem to be an official package since Ubuntu 14.Does anyone have an idea about what to do?

---

### Post by beardybear on 2017-11-15
I finally found an answer here:
[https://askubuntu.com/questions/976029/flickering-windows-and-video-freezing](https://askubuntu.com/questions/976029/flickering-windows-and-video-freezing)

You just have to re-enable X11.

---

