---
title: "Screen resolution right, image size wrong"
date: 2008-02-25
forum: Desktop Environments
---

### Post by mcsmith on 2008-02-25
I recently went through the process of installing Ubuntu onto a system, but am having problems with the display.  The monitor is an Envision 22" H22W LCD display, whose native resolution is 1680x1050.  I began the installation with a 7.04 live CD (which was all I had at the time).  When running from that CD, the screen was displayed at 1680x1050, and filled the monitor bezel to bezel.

I installed the Ubuntu to the hard drive, and rebooted.  When the system came up, the screen was still displayed at 1680x1050, and again filled the monitor bezel to bezel.

I then upgraded the distribution to 7.10.  The upgrade went smoothly, no error messages.  When I rebooted, the screen resolution was still 1680x1050, but the image was no longer filling the display.  The vertical size was approximately the same, but the vertical positioning was slightly off (maybe 10 pixels below where it should have been).  The horizontal size was about 80% of the width of the screen (and shifted to the right of the panel).  The system still reports that it's running at 1680x1050.

It's almost like the pixels got skinnier.  The amount of vertical adjustment is within the limits of the display to be manually adjusted, but the horizontal size cannot be compensated for with the on screen controls of the monitor.

I compared xorg.conf from the installed 7.10 image with what is produced when running with the live CD, and I didn't see any change.

Can anyone suggest a next step?

Thanks,

Mike

---

### Post by Sam Lars on 2008-02-25
Not totally sure it will solve it, but you can always try
```
sudo dpkg-reconfigure xserver-xorg
```
You might want to back up your xorg.conf in case you want to revert back.

---

### Post by mcsmith on 2008-03-27
I tried:

```

sudo dpkg-reconfigure xserver-xorg

```

to no avail.  This wasn't my primary system, and due to higher priority tasks, I just left it on my back burner.  Today, I decided to throw caution to the wind and upgrade to hoary beta.  The problem went away.

Thanks to all, expecially the hoary team!

Mike

---

### Post by Browser_ice on 2008-03-27
I have the same problem. I reconfigured my xconf.org with that command but only to accept all default values (except I added more available resolutions). 

It didn't change a thing.

Aren't there any manual control to increase the horizontal size of the screen until it visualy matches the monitor's width ???

---

