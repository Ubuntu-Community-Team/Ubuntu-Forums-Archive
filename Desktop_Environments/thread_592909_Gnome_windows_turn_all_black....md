---
title: "Gnome windows turn all black..."
date: 2007-10-26
forum: Desktop Environments
---

### Post by kmamykin on 2007-10-26
I just started playing with Ubuntu Desktop 7.10, on Dell Latitude 800, 512M RAM. nVidia NV34M [GeForce FX Go5200 64M] card.
But I am experiencing this problem when Gnome windows just go black. Current window goes black, and then any consequently opened window is also blank black. However previously opened windows still function.

Below are the screenshots of the problem. I am using NVIDIA accelerated graphics driver (latest cards) in case you wondered and and it makes any difference. 

Does anyone have any idea how to fix this? 

[ [IMG]http://www.imagehosting.com/out.php/t1301329_Screenshot4.png[/IMG]](http://www.imagehosting.com/out.php/i1301329_Screenshot4.png)

[ [IMG]http://www.imagehosting.com/out.php/t1301328_Screenshot3.png[/IMG]](http://www.imagehosting.com/out.php/i1301328_Screenshot3.png)

Thanks

---

### Post by Billisnice on 2007-10-26
This upgrade is a downgrade....7.04 just worked.  7.10 stinks...

---

### Post by isecore on 2007-10-26
The black windows is a result of how a compositing window manager handles what it draws. Long and complicated story made short: the black windows is due to the graphics subsystem running out of video RAM to draw windows on. This is why you get that after a while, and especially with several windows open. Since your card is only equipped with 64 megs this happens quicker than cards with more memory.

This is essentially a driver issue with Nvidia-drivers. There's a few ways around it, none of them very elegant unfortunately. I read somewhere that Nvidia has fixed it in the latest drivers, but those haven't made it into Ubuntus repos yet. If you're feeling adventurous you can install it from Nvidias site, but it's not as smooth as many would wish.

The other option is to disable the desktop effects, but then you won't have a desktop full of eyecandy.

---

### Post by kmamykin on 2007-10-26
Would switching to Xfce be advisable for 64M video memory?

---

### Post by kmamykin on 2007-10-26
Thanks isecore, 
I installed the latest drivers for my card from nVidia web site and it seems to be working fine now. I also disabled the visual effects for the desktop. I will give it a bit more testing before the final conclusion though... but so far so good.

---

