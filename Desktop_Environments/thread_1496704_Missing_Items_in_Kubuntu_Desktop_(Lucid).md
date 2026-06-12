---
title: "Missing Items in Kubuntu Desktop (Lucid)"
date: 2010-05-29
forum: Desktop Environments
---

### Post by todd1049 on 2010-05-29
I installed ubuntu 10.04 recently, and downloaded the KDE desktop to use as an alternate work environment.  I had done this previously with 8.04, without any problems.  In the new version, I have downloaded plasma-desktop and kubuntu-desktop to install KDE, and KDE works fine (mostly) on my system. Two things, however, are missing.  First, when I go to the "Leave" screen, I can hibernate, log out, etc., but there is no "shut down" setting available.  Does anyone know how I can fix this? 

The other thing I am lacking is the icon in the bottom right corner which allows me to connect to a network.  I have searched and searched the widgets, but can not the item that should do this job.  Again, any suggestions on how to fix this would be welcome.

---

### Post by ninfalara on 2010-05-30
Hi

Regarding the missing "shut down" button, you should check your session settings in System Settings.

In the "advanced" tab, go to session manager and you should have the following options checked:

In "general": 

- confirm logout (*adviced, not mandatory*)
- Offer Shutdown options

In "Default Leave Option":

- Turn Off Computer

In "On Login":

- Start with an empty session (*adviced, not mandatory*)

---

### Post by ankspo71 on 2010-05-30
Hi,
First, see if the package "knm-runtime" is installed. Then try using the command "knetworkmanager" to start the network manager. If it starts, then make a start up application entry for it. I think it is possible to use gnome's network manager too, which I think the command is nm-applet. [http://jeffhoogland.blogspot.com/2010/04/howto-use-gnome-network-manager-in.html](http://jeffhoogland.blogspot.com/2010/04/howto-use-gnome-network-manager-in.html) (just in case :) )

---

### Post by todd1049 on 2010-08-31
Ninfalara, thanks for the tip -- that worked great.  Ankspo71, I tried your suggestion, but had no luck.  The command line told me that plasma was not installed (grr), so something must have been wrong with my original installation.  I have tried installing KDE with lucid via both the ubuntu software center and via Synaptic, with limited success.  I think I will be better off if I just install via the command line.  Can you recommend the command-line options I should use to install, if I want to try loading it via the command line?  Thanks again for the help!

---

### Post by ankspo71 on 2010-08-31
Hi,
Is the 'system tray' widget added to you panel? This is where the network manager for KDE is supposed to appear.

To install kubuntu-desktop from the terminal you can use:
```
sudo apt-get install kubuntu-desktop
```
If it reports kubuntu-desktop as already installed, you might be able to install any missing components (if any) by using the reinstall option:
```
sudo apt-get install --reinstall kubuntu-desktop
```

---

