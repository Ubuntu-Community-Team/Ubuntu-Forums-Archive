---
title: "Tweak Xubuntu (and Xfce) to run fast with only 64MB memory?"
date: 2006-07-16
forum: Desktop Environments
---

### Post by treesize on 2006-07-16
How do I tweak a stock Xubuntu 6.06 install to be as responsive as possible on a Celeron 466MHz with 64MB of memory and onboard graphics? The default install is usable, but it does tend to swap on occasion.

*The machine is to be used for regular websurfing in Firefox and that’s it*. Nothing fancier than that.

I don’t need any effects, the ability to game and use 3D or the ability to print or anything like that, so daemons that take care of these areas are fair game for tweaking.

I'd like to stay with Xfce as the user needs something nice and easy that resembles Windows. Other desktop environments and window managers are out of the question.

How do I proceed from here (other than the obvious of putting more memory in the machine)?

---

### Post by treesize on 2006-07-16
I removed the background image and CUPS, but there has to be more that can be done.

---

### Post by shawnrgr on 2006-07-16
check this out first: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

also if you don't have a printer you can turn of hplip.
Make sure to change your theme to the most minimalistic, somthing very simple.

If your not getting the preformace your looking for after all that.. i suggest you use something like Blackbox or Fluxbox.

Extremely lightweight window managers

Blackbox:
[http://blackboxwm.sourceforge.net/](http://blackboxwm.sourceforge.net/)
[http://ubuntuforums.org/showthread.php?t=125084](http://ubuntuforums.org/showthread.php?t=125084)

FluxBox:
[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)


Also make sure that you have the proper kernel package for your system, i have an AMD64 3700+ so i use the K7 kernel. I would use a 64bit kernel but id rather wait for all the programs to be 64bit compatible. If you have a high end pentium i would suggest the i686 kernel.

If somthing goes wrong you can still just boot from the original kernel so don't be worried to install a new kernel.

system>synaptic-package-manager

make sure you install the correct package. you will see alot of things such as linux-image-2.6.15-26-k7, you want to make sure you install the package "linux-k7" (for amd) or "linux-686" (for faster pentiums)

For more about finding the right kernel for your system I suggest you check out this thread [http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713)

---

