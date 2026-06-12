---
title: "problems loading ubuntu after installing kubuntu-desktop"
date: 2007-10-01
forum: Desktop Environments
---

### Post by dougmorin on 2007-10-01
After installing kubuntu-desktop and restarting into the KDE desktop environment I went into display and modified the monitors to try and set up my duel monitors.  This seems to have caused a problem because when i restarted XServer ubuntu would not load.  It went through the first screen (the loading ubuntu... now kubuntu) and then went to the second set of loading screens and seemed to freeze up.  Is there a way I can reset my monitor information to when i first loaded the kubuntu-desktop or have i lost the os... or is there a way i can manually change the config files for the monitors.

please help... windows is making me sick :)

---

### Post by dougmorin on 2007-10-01
I forgot to mention that when the screen froze up I was able to hit ctrl+alt+f1 and load the command line

---

### Post by VSpike on 2007-10-01
Try (at the console):

sudo dpkg-reconfigure xserver-xorg

---

### Post by dougmorin on 2007-10-01
Thanks VSpike, I will go ahead and try that ASAP.

--Doug

---

### Post by dougmorin on 2007-10-02
That worked to reset the monitors.  Thanks for the help...

One of my monitors is all set, although my right monitors display is all messed up.... multi colored,  blocks, etc... and i can configure this one monitor all right but when I go to set up the duel monitors in the display manager that KDE has i get the same problems again.  

my video card is a NVIDIA GeForce FX5200 256mb with duel monitor and s-video support.

good thing i backed up my xorg.conf file this time.... was easier than going through the reconfigure procedure :-/

---

