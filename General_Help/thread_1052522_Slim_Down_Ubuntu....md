---
title: "Slim Down Ubuntu..."
date: 2009-01-27
forum: General Help
---

### Post by icanfly0307 on 2009-01-27
I know that many of you will tell me to go and get a lighter distro or go with xubuntu. However, Ubuntu runs very fast on my old 1Ghz P3, 256MB RAM Vaio laptop. I'm currently stripping it down so that things will be a bit smoother. The main thing that I use this computer for is to listen to music and browse the internet. I've gotten rid of nautilus and replaced it with pcmanfm already. I've also replaced gedit with leafpad, and firefox with epiphany. Any other tips on how to speed up my computer? Thanks! :)

---

### Post by damis648 on 2009-01-27
If you are going for really light, you can try out some *boxes like OpenBox or Fluxbox. They are specifically window managers, but can be used like desktop environments.

---

### Post by icanfly0307 on 2009-01-27
I seriously need to stick with GNOME because I need it for work. Any other thoughts?

---

### Post by adamlau on 2009-01-27
A good many of us also use our boxes for work and do not use GNOME. Reconsider your prejudices and give Xubuntu a shot. Anything that can be done in GNOME can be worked around in other environments :) . Offhand, you are on the right path. Replacing applications with lightweight equivalents is the first step. The next step is to reduce environmental dependency on GNOME libraries with an alternative DE.

---

### Post by jerome1232 on 2009-01-27
On that note I use iceWM on a few of my computers and I love it, looks great with the right themes. It's just a matter of learning how to properly configure the window manager to your liking.

Gnome is just... slow compared to the slew of lightweight window managers out there.

---

### Post by icanfly0307 on 2009-01-27
I'm not prejudiced against any other DEs, I just need GNOME for work. Everything depends on it. I was just wondering if there were general system-wide hacks that would speed up my computer. And trust me, GNOME is lightening quick on this computer. My login time from GDM to my desktop is 4 seconds!!! However, it takes a long time to load applications.

---

### Post by mb_webguy on 2009-01-28
If you have a decent amount of memory (upwards of 512MB, preferably >1GB) then you can get a minor speed boost by reducing how often the system writes to swap, since memory is a couple of orders of magnitude faster than your hard drive.  In the terminal, enter the command "gksu gedit /etc/sysctl.conf", add the line "vm.swappiness=10" at the end of the file, then save and exit.  This value can range from 0 to 100, and the higher the number, the more your system will tend to write to swap instead of using available memory.  A value of 0 means that swap will not be used.  The default is 60.  I think 10 is a good setting, and I certainly wouldn't suggest going all the way to 0 unless you have an overabundance of memory, but feel free to experiment.

If you have a multi-core processor or one that supports hyperthreading, you can get a significant boost to startup by enabling concurrency.  Enter the command "gksu gedit /etc/init.d/rc" in the terminal, and look for the line "CONCURRENCY=none".  Change this to "CONCURRENCY=shell", then save and exit.

You may find some websites advising you to speed up your hard drives by changing some of the mount options in /etc/fstab, but I highly advise you to ignore them.  The options used by default by Ubuntu were not chosen arbitrarily.  The potential speed increase offered by these proposed tweaks is negligible at best, and certainly not worth the risks involved.

You can also go to System->Preferences->Sessions and System->Administration->Services and disable anything you don't use.  I personally disable Tracker and the Tracker applet, since I don't use it enough to warrant the performance hit when it is indexing my system.   You obviously will want to disable the Bluetooth services if you don't have Bluetooth on your computer.

Another thing that may or may not be obvious...  If you're using Gnome, don't use applications made for KDE, and vice-versa.  Your system has to load extra libraries for applications that were not developed for use with your desktop environment, so you'll take a performance hit when using one, especially when you first start the app.

---

### Post by blazemore on 2009-01-28
Compile your own kernel

---

### Post by icanfly0307 on 2009-01-28
Thanks a lot guys! I applied those tweaks and my system is significantly faster!!! BTW, I only have 256MB of RAM, but I couldn't find the "vm.swappiness" line in sysctl.conf, so I added it on my own and set it to 5.

---

### Post by Carl H on 2009-01-28
I use Xubuntu because I fancied a change from GNOME. 

GNOME apps work perfectly fine under XFCE.

---

### Post by meborc on 2009-01-28
if you need a bit more speed, you can play around with different themes and theme engines... you will find an interesting correlation between the ugliness of the theme and the speed :D

it all comes down to how much are you willing to sacrifice for speed

an old fix like this could also help - [http://www.marksanborn.net/linux/speed-up-the-gnome-menu-and-fix-the-annoying-icon-delay/](http://www.marksanborn.net/linux/speed-up-the-gnome-menu-and-fix-the-annoying-icon-delay/)

---

### Post by mb_webguy on 2009-01-28
You can also speed up Nautilus a bit by disabling thumbnails.  In Nautilus, go to Edit->Preferences and click the Preview tab.  Set everything to "Never".

Or, you could try another file browser altogether, like Thunar.  It doesn't quite have all of the features of Nautilus, but it's designed for the Xcfe desktop and has a much smaller memory footprint than Nautilus.  I still prefer Nautilus, but Thunar is admittedly quicker.

The same is true of other applications.  Remember that Linux apps will run under any desktop, even if designed for a different desktop than the one you're using.  Using apps designed for a full-featured desktop environment (like Gnome or KDE) on a different desktop environment generally means a slight decrease in performance for that app versus similar apps designed for the desktop environment in use.  Using apps designed for a lightweight desktop environment, on the other hand, almost always results in better performance.  But because these apps are designed to be smaller, they generally aren't as full-featured.  It just depends on how much you value performace versus features.

To take this one step further...  Many Linux apps can be run from the command line without a GUI.  Since the GUI uses additional system resources, you'll get slightly better performance by using the command line instead.  And not only will you not lose and functionality, you may be able to access features not made available by the GUI.  The downside is that you have to type out potentially long commands, which probably involves doing a little research to figure out what options you need, in order to do what you want.

---

### Post by xc1024 on 2009-01-28
if you truly want more speed, you can try installing ubuntu from minimal cd. you will probably need a clean install, but worth trying.

---

### Post by avtolle on 2009-01-28
> **xc1024 said:**
> if you truly want more speed, you can try installing ubuntu from minimal cd. you will probably need a clean install, but worth trying.
Be aware, however, should you decide  to go this route, you will need to carefully consider which apps you want and make sure to install them, along with dependencies, so you have an operable system. [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) will give an overview of things to consider when pursuing this course of action.

---

### Post by icanfly0307 on 2009-01-28
@mbwebguy: I've already replaced Nautilus with PCManFM and I love it! :)

@xc1024 and avtolle: I didn't install this system from the LiveCD... It was a minimal network install and then, I added stuff that I wanted.

---

