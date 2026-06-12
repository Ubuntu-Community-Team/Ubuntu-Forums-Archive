---
title: "battstat-applet doesn't work after update to breezy"
date: 2005-10-17
forum: Desktop Environments
---

### Post by dakira on 2005-10-17
Hi,

I don't know why this happens but after I updated from Hoary to Breezy I don't get the battery status anymore. I can assure you there is no problem with my DSDT. I am in the lucky position to have a working DSDT in my Bios. My guess is there is either something broken with Breezys ACPI or with the new version of battstat-applet-2.

The applet always shows that I'm connected to the power cable. No matter whether that's true or not.

I tried to recompile it using these directions:
[http://www.ttwhy.org/home/blog/2005/09/09/battstat-ubuntu-and-you/](http://www.ttwhy.org/home/blog/2005/09/09/battstat-ubuntu-and-you/)

Now it recognized that I pull the plug but doesn't recognize when I put it back in nor does it know the battery state. Does anyone know what's wrong or how I should approach this?

---

### Post by dakira on 2005-10-22
I'm not sure why, but my battery status works again. What I did was this: I installed kubuntu-desktop to show a friend that Ubuntu works with KDE, too and possibly make him switch over from Mandrake (because I was tired of fixing his problems). Anyway, after I showed him KDE I uninstalled all the 141 packages which where installed as a result of installing kubuntu-desktop to get rid of KDE.

Now the battery-status strangely works again. Is it possible that this happened because an already installed package has been reconfigured?

---

