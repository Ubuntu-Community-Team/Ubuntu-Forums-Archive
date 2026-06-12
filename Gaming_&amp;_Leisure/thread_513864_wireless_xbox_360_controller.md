---
title: "wireless xbox 360 controller"
date: 2007-07-31
forum: Gaming &amp; Leisure
---

### Post by alalusim on 2007-07-31
does anyone know if the (official) wireless xbox 360 controller with the wireless gaming receiver ([http://www.gamestop.com/product.asp?product%5Fid=802337](http://www.gamestop.com/product.asp?product%5Fid=802337)) works in ubuntu?

if so, is it usable with most emulators (ie. zsnes, mupen64, vba)?

on a side note, does anyone know of any way to connect an original playstation (not ps2) controller to a usb port (preferably costing less than $20).  it would have to have the same emulator support that im looking for with the 360 controller

thanks

---

### Post by alalusim on 2007-07-31
can anybody see if xpadder ([www.xpadder.com](www.xpadder.com)) works in ubuntu under wine or something? it seems like its a solution for the wireless 360 controller

---

### Post by KingHanco on 2007-07-31
Get a Radioshack psx/ps2 usb cable with software. But you don't have to install the software to use the usb.

I have no problem with this one. The problem that I have is that Ubuntu doesn't install the usb rumble support driver. Because the cd software is for windows only.

I don't think they make any rumble support software for Linux version.

[http://www.radioshack.com/product/index.jsp?productId=2348187&cp=&sr=1&origkw=psx&kw=psx&parentPage=search](http://www.radioshack.com/product/index.jsp?productId=2348187&cp=&sr=1&origkw=psx&kw=psx&parentPage=search)

---

### Post by WastingBody on 2007-07-31
I don't know about the wireless one, but I have seen a guide for the wired controller for Edgy.

---

### Post by alalusim on 2007-07-31
yeah ive seen that too but the only wired controller i have is the one for guitar hero

i doubt i could play ocarina of time on a guitar lol

---

### Post by alalusim on 2007-08-01
has anybody seen anything else?

---

### Post by alalusim on 2007-08-07
i went out and bought one and sure enough it doesnt work in ubuntu

i tried installing the driver from the cd through wine but it tells me that it will only install on a computer with windows xp sp1 or higher

im dual booting so i installed it on my xp partition and it works great for emulation with xpadder (which i have successfully installed in wine)

does anyone know if there is a way to trick wine into thinking that its installing the driver on an xp partition or if the check for windows can be bypassed altogether?

---

### Post by Bohlio on 2007-09-17
I just recieved one of the Xbox Wireless controller and reciever bundle for free from club.live.com , and this thing is the greatest.

I also have it working in windows with the official drivers and Xpadder.
The PC drivers won't do anything, they are meant to work with windows, and will not work with Ubuntu at all, its not a matter of tricking Wine into installing them.

And even if you do get Xpadder to work in wine, you need to have drivers installed for the controller, Xpadder isn't drivers, its just a button mapping program (I think :D )

I really really do want to get the controller working in Ubuntu, just because the controller is the greatest :D If anyone knows how to get it working, or has information about if it is even possible or not, please tell.
and remember, this is the wireless, not wired.
[http://www.microsoft.com/hardware/gaming/productdetails.aspx?pid=090](http://www.microsoft.com/hardware/gaming/productdetails.aspx?pid=090)

---

### Post by spoonie on 2007-09-18
They have a guide  to get one working under gentoo check it out

[http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux) :)

---

### Post by Bohlio on 2007-09-18
So it Can work in Linux, but there's not a guide to installing it in Ubuntu yet?

Is there a big difference between Gentoo and Ubuntu? I dont know anything about Gentoo...

---

### Post by ebaniz on 2007-09-20
Just to confirm, I have the wireless xbox360 remote going in Ubuntu (kernel 2.6.22).  Basically you can download the archive from: 

[http://ubuntuforums.org/showpost.php?p=2512158&postcount=6](http://ubuntuforums.org/showpost.php?p=2512158&postcount=6)

Extract it and replace the xpad.c and xpad.h with the ones from the gentoo howto: ([http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux))

Then proceeded by following this guide
(starting at "Now Your going to add the xpad360 "driver" into the /usb/inputs"):
[http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+controller](http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+controller)

Rebooted the box, trained the controller with the dongle (goes from fast to slow blink, the green leds on the controller will keep blinking but thats ok) and was able to use jscalibrator and test using emulators.

Works great and thanks to the authors of the code and above mentioned howtos.

---

### Post by alalusim on 2007-12-15
hey thanks i got it to work, but how do i get emulators to recognize it (ie mupen64)?

---

### Post by Moonfrost on 2007-12-17
> **ebaniz said:**
> Just to confirm, I have the wireless xbox360 remote going in Ubuntu (kernel 2.6.22).  Basically you can download the archive from: 

[http://ubuntuforums.org/showpost.php?p=2512158&postcount=6](http://ubuntuforums.org/showpost.php?p=2512158&postcount=6)

Extract it and replace the xpad.c and xpad.h with the ones from the gentoo howto: ([http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux))

Then proceeded by following this guide
(starting at "Now Your going to add the xpad360 "driver" into the /usb/inputs"):
[http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+controller](http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+controller)

Rebooted the box, trained the controller with the dongle (goes from fast to slow blink, the green leds on the controller will keep blinking but thats ok) and was able to use jscalibrator and test using emulators.

Works great and thanks to the authors of the code and above mentioned howtos.

Hey...which specific file I get from the guide? also, that guide is mostly for Gentoo so the download commands are different...how did you get them? the only thing I miss from Windows was playing all of my ten emulators with the wireless controller with no xpad or anything since all emulators detected it...

---

### Post by Moonfrost on 2007-12-18
> **ebaniz said:**
> Just to confirm, I have the wireless xbox360 remote going in Ubuntu (kernel 2.6.22).  Basically you can download the archive from: 

[http://ubuntuforums.org/showpost.php?p=2512158&postcount=6](http://ubuntuforums.org/showpost.php?p=2512158&postcount=6)

Extract it and replace the xpad.c and xpad.h with the ones from the gentoo howto: ([http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux))

Then proceeded by following this guide
(starting at "Now Your going to add the xpad360 "driver" into the /usb/inputs"):
[http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+controller](http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+controller)

Rebooted the box, trained the controller with the dongle (goes from fast to slow blink, the green leds on the controller will keep blinking but thats ok) and was able to use jscalibrator and test using emulators.

Works great and thanks to the authors of the code and above mentioned howtos.

Which one am I supposed to download? the one that says for both Wired and wireless controllers? because I downloaded that one but now I have no idea to where it saved!!!

---

### Post by mickyt1992 on 2007-12-30
Hi,
   just one question.  I have a wireless controller that came with my xbox.  I also have a play and charge kit for it.  However i don't have the dongle that was mentioned. I was wondering is there anyway to get the controller to work liked a wired one with the play&charge kit, if yes do i just the regular drivers or do i need to download some special one?  I really don't want to go out and but a dongle, as i will rarely use it.  I only want it for a few select games.  

Ok, thats more than one question, and a bit cryptic, but any help with be appreciated.

---

### Post by kaytaro on 2007-12-30
> **mickyt1992 said:**
>  is there anyway to get the controller to work liked a wired one with the play&charge kit,

nope, that cable can only be used to charge the unit, it doesnt have the ability to act as a wired controller. It would be be nice if it did, but i am sure you can see that would kinda be a useless feature for a "wireless" remote to have a "Wired" mode lol ^^

As far as getting your controller to work you can buy that wireless adapter from ms for about $20 as seen here [http://www.newegg.com/Product/Product.aspx?Item=N82E16874103054]("http://www.newegg.com/Product/Product.aspx?Item=N82E16874103054")

But your best bet is prolly to go buy a wired one seeing as they tend to have a higher success rate of people getting them to work in Ubuntu in the end, imo. 

gl mate!

---

