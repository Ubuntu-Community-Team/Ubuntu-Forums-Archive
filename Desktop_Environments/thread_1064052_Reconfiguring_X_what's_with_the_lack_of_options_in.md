---
title: "Reconfiguring X: what's with the lack of options in xorg.conf"
date: 2009-02-08
forum: Desktop Environments
---

### Post by marcthenarc on 2009-02-08
I just spent all morning trying to reconfigure X on my Hardy but couldn't get it to work. After reading many HOWTOs, on both with or without proprietary ATI drivers, I had this brilliant Idea ;) Why don't I just install Ibex on a new partition and take a peek at the xorg.org file there and learn something.

Kubuntu Ibex works well of the CD, even in 3D without proprietary drivers.
But there isn't  _anything_ really ground breaking in it's xorg.conf file

```

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Where are the drivers, the default screen resolution, the mouse definition, the font paths ? 

I tried copying the Ibex file into Hardy without results.
I've tried so many times sudo dpkg-reconfigure -phigh xserver-xorg.

Where is everything hidden now ?

Is the xorg.conf file useful any more?  Or will any change to it is simply been overridden by KDE or Gnome settings ?

---

### Post by warp99 on 2009-02-08
The xorg.conf in intrepid is not need by default since everything is probed and set by Xorg on the fly except screen resolution which is stored by gtk-display, but you can use one if you like and those values will be used instead. It you want to generate a fresh xorg.conf with all of the system information just run the following:

```
sudo Xorg -configure
```

Then you can further customize the file to your needs.

---

### Post by mjm1231 on 2009-02-08
> It you want to generate a fresh xorg.conf with all of the system information just run the following:

I just swapped out the monitor on an older PC that I have xubuntu 8.10 running on. How do I tell what the current system information is? How do I know whether the system has detected the monitor? One of the things I hate about Windows is the amount of information that is hidden or impossible to get at. Why is there no device manager equivalent (or devices installed listing at least) in xubuntu?


 The last several times I've installed ubuntu and xubuntu, I've been glad to see that everything just works. But when I replace the monitor (something I've done a few times because its an older system and when a better hand me down monitor becomes available, I swap it in) every time its the same. Getting the video resolution set up for the new monitor is such a pain that I end up opting for a reinstall. Invariably the monitor is detected correctly with the new install. I was hoping this time would be different.

While I have configured xorg files by hand a few times, its not something I really relish doing. Not that the config file is difficult, but researching and gathering all the information is the biggest time and energy drain. I'm running an older system, with an old nvidia (possibly a riva tnt. I don't care and don't feel like powering off the computer, opening the case, removing the card, and trying to find some part number or markings that will tell me what it is) and a dell monitor (again not certain of the model, and in its current location I would have to unhook it in order to read the model off the back, then google for the specs on the monitor to enter in the xorg.conf. Ugh). All I want is decent 2D graphics to work. I have no use for Compiz or Beryl or whatever or any 3D anything on this system. Why is changing out a monitor such a major chore?

---

### Post by ajgreeny on 2009-02-08
you can easily find all your hardware by running ```
sudo lshw -html > ~/hardware.html
```which will produce a file called hardware.html in your home folder which you can view in firefox or other web browser.  It will give you a mass of info about your hardware.  If you want a GUI to do it, get hardinfo from the repos which does the same job.

---

