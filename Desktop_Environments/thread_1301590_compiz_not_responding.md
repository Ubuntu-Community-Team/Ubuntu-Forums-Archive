---
title: "compiz not responding"
date: 2009-10-26
forum: Desktop Environments
---

### Post by yanvolking on 2009-10-26
Hello Community,

I have just bought a new flatscreen because my old cathode ray screen could not handle the NVIDIA drivers of my nuew computer's video card.  I installed the new screen, installed the NVIDIA driver and nothing happens.  Compiz is installed (I installed it via synaptic installing just about every line that carried the name "compiz".  In the Compiz Config Settings manager, I have checked the boxes for "cube" and "rotate cube" but this does nothing.  The only clue I have to what may be wrong is the screen that appears when I click on 
DISPLAY->PREFERENCES (see attachement - I dont know how to paste an image onto this page).  It is an NVIDIA X server settings menu.  I'm afraid I have no idea what to do with this menu nor whether this is in fact the solution to my problem.  This menu also comes up when I press "SYSTEM->ADMINISTRATION->HARDWARE DRIVERS"  and then "NO" to a message saying :
"It appears that your graphics driver does not support the necessary extention to use this tool. Do you want to use your graphics vendor's tool instead?".

I just spend 150 EUR on the flat screen to enjoy compiz 3D graphics and now this. 

Note that the installation steps I followed for compiz are exactly the same as the ones I took to install compiz on my DELL  Latitude D610 laptop, and there the 3D rotating cube effect came immediately.

my laptop's video card is :
 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

The video card on my desktop is:
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)

Please help if you can.

Thanks in advance

---

### Post by Giblet5 on 2009-10-26
So, why did you answer "no" to the question? It told you that your existing driver won't work, offered to fix it, and you answered "no"...

Install the nvidia driver.

Reboot. (Or just restart gdm)

Turn on compiz from System/Prefs/Appearance by selecting the Effects tab, and select "Extra".



Note: your post is very confusing. Compiz doesn't care what monitor you have and what does your laptop have to do with anything?

When you have a question about X, don't include what you had for breakfast and the length of your cat's claws.

We all drink too much coffee and have the attention span of goldfish. :)

---

### Post by yanvolking on 2009-10-27
Hi,

i did : System/Prefs/Appearance by selecting the Effects tab, and select "Extra".  and it worked.

Thanks

---

