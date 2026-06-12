---
title: "nVidia closed source drivers with a new GeForce 560 Ti"
date: 2011-09-18
forum: Desktop Environments
---

### Post by Drone4four on 2011-09-18
I just installed me new graphics card.  It's an nVidia GeForce GTX 560 Ti 2GB manufactured by EVGA.  However I foolishly didn't uninstall the old binary drivers for my 9600 GT.  At any rate, upon booting Ubuntu for the first time with my new gfx card and old nVidia driver, it reverted to nouveau.  So my system runs, just without proprietary 3D acceleration, without compiz.  So I use the Additional Drivers GUI utility that comes with Ubuntu to uninstall the proprietary nVidia drivers.  I reinstall them.  It asks me to reboot.  I do; but nouveau is still in use.  I open my xorg.conf with the intent to change the driver entry from nouveau to nv, but my xorg.conf is practically empty.   Here is what my new xorg.conf looks like:  

```

Section "Device"
   Identifier    "Default Device"
   Option    "NoLogo"    "True"
EndSection

```

And here is the output of compiz-check courtesy of compiz developer Forlong:
```

daniel@natty:~/Desktop$ bash compiz-check

Gathering information about your system...

Distribution:          Ubuntu 11.04
Desktop environment:   Xfce
Graphics chip:         nVidia Corporation GF110 [GeForce GTX 560 Ti] (rev a1)
Driver in use:         nouveau
Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap...               [ OK ]
Checking for non power of two support...          [ OK ]
Checking for composite extension...               [ OK ]
Checking for FBConfig...                          [ OK ]
Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
Warning: Detected driver is not on the whitelist.

Would you like to know more? (Y/n)

Your driver is not widely known to work with Compiz and thus may be
blacklisted on certain distributions.

You can skip this blacklist -- but keep in mind that you did so.
Do not complain if you encounter any problems with Compiz afterwards.

Do you want to skip blacklist checks by Compiz? (y/N) n
daniel@natty:~/Desktop$


```

I am running Ubuntu Natty 64bit.```
daniel@natty:~$ uname -a
Linux natty 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
daniel@natty:~$ 

```

---

### Post by Krytarik on 2011-09-18
Create a proper new "xorg.conf" with this command:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```Then reboot/relogin.

Hope it works!

---

### Post by Drone4four on 2011-09-18
Thanks, Krytarik: that did the trick.  How did you know that command would work?  I ask in the interests of self-reliance.  I want to know how you arrived at that solution so I can do it myself next time.  What Google search query did you use? What guide did you read where you came across that solution?

---

### Post by Krytarik on 2011-09-18
Well, that's just cumulated experience, plus I, myself, have an Nvidia card, too. Eventually, I just c&p'd the command from a text file I saved a while ago, when I started working at the UF.

However, if you are interested in the complete man page of "nvidia-xconfig" (this is from Lucid 10.04, there are no newer ones in the official [Ubuntu Manpages]("http://manpages.ubuntu.com/")):

[http://manpages.ubuntu.com/manpages/lucid/en/man1/nvidia-xconfig.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/nvidia-xconfig.1.html)

Greetings.

---

