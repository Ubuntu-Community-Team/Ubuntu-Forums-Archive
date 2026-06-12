---
title: "Windows load slowly in Hardy--Compiz problem?"
date: 2008-04-30
forum: Desktop Environments
---

### Post by kirk ammon on 2008-04-30
On Gutsy, my windows loaded perfectly. Now in Hardy (for example, when opening or maximizing Evolution) windows load slowly with black boxes where the unloaded parts are. It is very annoying, and Gutsy did not have this problem. Does anyone know how to fix this?

Please let me know what you need and I will post specs or files.

---

### Post by warp99 on 2008-04-30
> **kirk ammon said:**
> On Gutsy, my windows loaded perfectly. Now in Hardy (for example, when opening or maximizing Evolution) windows load slowly with black boxes where the unloaded parts are. It is very annoying, and Gutsy did not have this problem. Does anyone know how to fix this?

Please let me know what you need and I will post specs or files.

Did you install the restricted drivers for your video card or are you running the open source ones? It does make a difference on performance depending on your make and model of video card.

---

### Post by kirk ammon on 2008-04-30
I have an nVidia graphics card and am using the driver "nvidia-glx-new". It appears in my "Hardware Drivers" window which at the top says "Proprietary drivers are being used...etc", so I guess it is the proprietary driver. Should I be using a different one?

---

### Post by warp99 on 2008-04-30
> **kirk ammon said:**
> I have an nVidia graphics card and am using the driver "nvidia-glx-new". It appears in my "Hardware Drivers" window which at the top says "Proprietary drivers are being used...etc", so I guess it is the proprietary driver. Should I be using a different one?

Well it depends, what's the model of your card and is it AGP, PCI, or PCI-E?

---

### Post by kirk ammon on 2008-04-30
according to NVIDIA X-server settings manager, it is AGP:

GeForce 6800 XT, 256 MB, AGP 8X

---

### Post by warp99 on 2008-04-30
> **kirk ammon said:**
> according to NVIDIA X-server settings manager, it is AGP:

GeForce 6800 XT, 256 MB, AGP 8X

That card is pretty well supported. I have a 6200 series which is basically the same thing running the restricted drivers without incident. I would check your /var/log/Xorg.0.log to see if there are any errors. At the top of the file there is a legend:
> Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.


Just follow the legend for any errors or even warnings. It may be that you have to add one or more options to your xorg.conf file in the device section. Nvidia does have a manual on possible problems including AGP driver conflicts:

[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-08.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-08.html)

It could also be that with Gutsy 7.10 there were various options that could be placed inside your xorg.conf file while with Hardy 8.04 the developers moved to a minimalist xorg.conf file using what they call 'Bulletproof-X' that has been a problem with a few users. 

If you still have you're older Gutsy 7.10 xorg.conf file available replace the current xorg.conf file with the older one. If you've upgraded from 7.10 to 8.04 the older file should still be in your /etc/X11 directory as a backup file. I currently run my 8.04 install with the older 7.10 xorg.conf file without any problems. Hope this points you in the right direction.

Edit:

You can also set some options by running 'gksudo nvidia-settings' making any modifications then use the 'Save to X Configuration File' to make the changes permanent.

---

### Post by kirk ammon on 2008-04-30
Unfortunately, there was no backup xorg file that I could find (even in hidden files), and the log file you told me to examine had no errors. There were two "WW" warnings, one for not finding a certain font, another for not detecting a mouse. Neither of these sound related to my problem.

Also, I ran dpkg-reconfigure xserver-xorg (which almost by magic solves most display problems I encounter), re-enabled my driver, and restarted. It did nothing =(. Actually, it never even entered the part where it reconfigures the display settings like usual. It just reconfigured my keyboard and then quit.

I'm not sure if there is anything more you can do, but I really appreciate your help so far. Thank you!

---

### Post by warp99 on 2008-04-30
> **kirk ammon said:**
> Unfortunately, there was no backup xorg file that I could find (even in hidden files), and the log file you told me to examine had no errors. There were two "WW" warnings, one for not finding a certain font, another for not detecting a mouse. Neither of these sound related to my problem.

Also, I ran dpkg-reconfigure xserver-xorg (which almost by magic solves most display problems I encounter), re-enabled my driver, and restarted. It did nothing =(. Actually, it never even entered the part where it reconfigures the display settings like usual. It just reconfigured my keyboard and then quit.

I'm not sure if there is anything more you can do, but I really appreciate your help so far. Thank you!

Well here is some more information from CompizFusion about working with Nvidia hardware:

[http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA)

One of the problems I had with blanking windows was solved when I enabled Sync to VBlank in the nvidia-settings dialog for both OpenGL and XV. You may want to try this. This was a problem in Feisty with my card, so it may be a regressive bug.

The open nv driver also works with Compiz, but on some systems, including mine, the performance is slower than with the restricted drivers. Now on other systems the performance is better with the open drivers. You should disable the nvidia driver and see how the open drivers work, you may be surprised.

---

