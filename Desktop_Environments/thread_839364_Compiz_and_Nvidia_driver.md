---
title: "Compiz and Nvidia driver"
date: 2008-06-24
forum: Desktop Environments
---

### Post by notlim_hardy on 2008-06-24
Hello all. I'm under Ubuntu 8.04 and I have a Nvidia 6 series card on my pc. Nvidia driver was working like heaven here, I was able to use NV X server settings, everything was perfect until last night, when during the automatic updates a program named Compiz was installed. After the reboot the system can't save the video configuration anymore, and all I get is 640x480 under a "vesa or compatible" driver. What should I do? Thanks.

---

### Post by jualin on 2008-06-24
Compiz is a composite window manager. Is what gives Linux the 3D effects that Vista and Leopard have. So that should not be the problem. Did you try installing the latest nvidia driver. It should be nvidia-new or nvidia-legacy new, depending on your Video Card. You can do that from Synaptic Package Manager. 
Another approach can be reconfiguring your X (Graphical User Interface that Ubuntu uses). To do this type in the terminal > sudo dpkg-reconfigure xserver-xorg . Tell me how that goes.

---

### Post by notlim_hardy on 2008-06-24
Didn't work. The problem is, when I run > gksu displayconfig-gtk I get this error: 

> on_button_test_config_clicked()
xauth:  creating new authority file /tmp/dcg-rN-3wT7157/xauthority
Got pid 7177
(0, 0)
checkpoint 1
None
False
Sorry, this configuration video card driver
and monitor doesn't appear to work:

Messages from the X server:
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:


Any ideas?

---

### Post by jualin on 2008-06-24
Did you run the command I gave you?

---

### Post by notlim_hardy on 2008-06-24
Yes, I did. I got this back: > xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20080624125014

---

### Post by Zorael on 2008-06-24
I'd do this. All-in-one-line edition, for your copy/paste pleasure.
```
$ sudo aptitude purge ~nnvidia-glx; sudo aptitude install nvidia-glx-new; sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```

---

### Post by blazercist on 2008-06-24
kernel update? perhaps he was using a proprietary driver? if so you must recompile and reinstall the driver.

---

### Post by jonathan.gardner04 on 2008-06-24
You might try using something like EnvyNG.  I have found that when I update the kernal I also update the video drivers.

---

### Post by notlim_hardy on 2008-06-24
I reinstalled nvidia driver, but when the session starts the monitor goes out of sync. what do I do?

---

### Post by notlim_hardy on 2008-06-24
Ok, it's solved. I enterd the Kernel safe-mode and repaired the x server through there. It's all working like a charm again. What I want to know now is how to use this compiz stuff. Thanks

---

### Post by sdennie on 2008-06-24
Out of curiosity, were you using drivers that you downloaded and installed from the nvidia website?  If so, you will consistently run into problems like this after kernel updates unless you setup the drivers to update after each new kernel install.  A guide to do that can be found here: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

### Post by notlim_hardy on 2008-06-24
Vor, as a matter of fact I am indeed using the drivers from Nvidia website, and the problem I've just been through happened exactly because a kernel update. Like I said, starting on safe-mode solved my problem, as the system could repair the x server from there. I really appreciate your link, if only I knew of it before lots of time would be saved. Thank you and everyone who helped me on this topic.

---

### Post by jualin on 2008-06-24
Now to get the Compiz working you just need to go to System, Preferences and Appearance and then click on the Visual Effects Tab and enable one such as "Normal". To have more options like the desktop spinning cube you need to install compiz-settings-manager from Synaptic.

---

### Post by notlim_hardy on 2008-06-24
I did that, Jualin. What should I do next?

---

### Post by jualin on 2008-06-25
If you did not get any errors when you enable the Visual Effects then you are all set. Try changing from Virtual Desktop to check if you see an effect or try ALT-TAB and check if something looks different. You can enable other effects by going to System, Preferences, Advanced Appearance or Advanced Effects (sorry out of memory). You can enable plugins such as the "Rotate Cube" plugin in which you have a spinning 3D Cube. Tell me how that goes.

---

### Post by notlim_hardy on 2008-06-25
JUalin, it all worked alright, I even have the desktop cube now! One more question, i have a .cgwdtheme file which is a Mac OS X theme. How do I install it?

---

### Post by jualin on 2008-06-26
After you install "emerald" from Synaptic try what is suggested in this post [http://ubuntuforums.org/showthread.php?t=514192]("http://ubuntuforums.org/showthread.php?t=514192") Apparently you need to rename the theme to the emerald extension ".emerald" instead of the CGWD extension ".cgwdtheme". 
P.S. If you want to get all Mac OS like system take a look at the docks available for Linux. Two of the most popular are Avant Window Navigator (AWN) and Cairo-dock (This one you can get from Synaptic). If you want to install [AWN]("http://thegabfather.wordpress.com/2008/05/29/71/") I reccomend you to install it from their own repositories since the one found in Ubuntu's repositories doesn't have "Launchers". Good luck and I am glad that you got everything working now.

---

