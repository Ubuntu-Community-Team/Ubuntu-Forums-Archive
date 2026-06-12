---
title: "NVIDIA / Monitor Resolution Issue"
date: 2008-08-31
forum: Desktop Environments
---

### Post by raywood on 2008-08-31
I'm running Hardy in a dual-monitor setup.  I had my resolutions working right and then, through one or more errors on my part, they vanished.  The best resolution I can get on a 1280 x 1024 monitor is now 800 x 600.  Having uninstalled and reinstalled drivers, packages, etc. for a number of hours now, I am wondering whether there might be a way to start over -- short of reformatting the hard drive and beginning from complete scratch.

Or maybe starting from scratch wouldn't be horrible.  In Windows, it means reinstalling and reconfiguring all those programs after doing the Windows updates etc.  Is it possible to reinstall Ubuntu without having to reinstall all the programs that came after?

Thanks!

---

### Post by Cato2 on 2008-08-31
On dual-monitor, here are a few URLs that may help:

[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html) - a little old but some good Nvidia tips - see nvidia-settings program

[http://ubuntuforums.org/showthread.php?t=826717](http://ubuntuforums.org/showthread.php?t=826717) - quite a good thread including HOWTO

Assuming you have LCD monitors, try reducing your refresh rate to 60 Hz - this is fine with LCDs and might help bump up resolution.  Also check what your card is capable of with dual monitors - can you get this resolution in Windows?

On re-installing, normally you lose all the apps, so what I would do is:

1. Back up your Home directory and any /etc/ config files you would like to keep, just for reference.  /etc is not too large, so you can back up both this and /home/youruser onto a USB stick quite easily.  Use a backup program so permissions are correct.

2. Back up the list of apps you installed, assuming all were from Ubuntu repositories etc.  This is what you do - dpkg is the tool underlying Synaptic and apt-get/aptitude, which actually does the installation of a package: ```
dpkg --get-selections >installed-packages.txt
```.  Then copy this file onto your USB stick.

Here's a good thread about using dpkg --get-selections: [http://ubuntuforums.org/showthread.php?t=169062](http://ubuntuforums.org/showthread.php?t=169062) - once you have done a full re-install of Ubuntu, you can then use dpkg again to install any missing packages.  Any package config would have to be hand restored from the /etc backup, or you can redo it via GUI tools etc.

---

