---
title: "Atom ION and nvidia drivers"
date: 2010-09-01
forum: Desktop Environments
---

### Post by SrAgaporni on 2010-09-01
Hi all.

I am testing Lubuntu for my home server. Till now, it works great, is fast and rock solid. But I have a problem with the nvidia drivers. It has an ION (Nvidia 9400m) card. I have been trying to install de proprietary drivers without been successful. I have been searching google and also at this forum and I have tried several "howto's", but neither worked for me.

At this moment, I am using the "vesa" driver writed at xorg.conf file, but it isn't a real solution as far as I can only setup my monitor to 640x480, and it is not very usable while working on graphical mode.

Would you mind helping me? I have spent last 4 hours researching and I am really starting to have a headache...

Thanks pals!

---

### Post by randywilharm on 2010-09-01
What happens when you try
System/Administration/Hardware Drivers?


Also: Nvidia drivers should be installed by becoming root.
I use sudo -i to install them in a  terminal (Ctrl + Alt + F1)
but when you get the driver,
be sure to enable (in properties/permissions) "Allow executing file as program".
or from a terminal you can use chmod.

---

### Post by 3rdalbum on 2010-09-01
Reload your package list by going into Synaptic Package Manager and click the Reload button. When that is finished, close Synaptic and go into Hardware Drivers. Click on the "recommended" Nvidia driver and click Activate.

When that is finished, reboot.

---

### Post by SrAgaporni on 2010-09-02
I installed the drivers from Package Manager, more exactly, the nvidia-current package. After that, I rebooted and checked if the "hardware drivers" had some info, the message that I got was "no nvidia hardware present".

I have also tried installing latest drivers from Nvidia, but I get the "kernel" problem with that, and I haven't been able to fix it following the howto's on the forum. 

I love ubuntu, but it is really a nonsense when something like installing a simple drivers becomes so difficult. At this moment, I am working on vesa driver, but I can't get any decent resolution, only 800x600 and it is a crap.

---

