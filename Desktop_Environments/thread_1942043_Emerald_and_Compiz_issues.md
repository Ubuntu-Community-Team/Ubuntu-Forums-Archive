---
title: "Emerald and Compiz issues"
date: 2012-03-16
forum: Desktop Environments
---

### Post by Spewed on 2012-03-16
Hey guys, 

I'm having issues with Emerald Theme Manager and compiz config settings manager. 

First of all I have them both working harmoniously together(for the msot part). I can use both, but have to use "Emerald --replace" command, then log out and back in and I am using Emerald. Same goes for gtk-window-decorator --replace.

However, I decided not to use Emerald as I discovered GTK3 themes are better. So as I'm using Compiz and GTK3 as my windows decorated if I use my Desktop cube the windows borders disappear, and I have to run "gtk-window-decorator --replace" again, log out and back in to have my borders. 

Is there a way to fix this. Should I uninstall Emerald? If so, how can I completely remove it?

---

### Post by kazztan0325 on 2012-03-18
Hi Spewed,

Sorry, I also don't know how to fix your problem.

But if you would not mind to uninstall Emerald, you have only to remove two packages: **'emerald'** and **'libemeraldengine0'** to uninstall Emerald.

---

### Post by Frogs Hair on 2012-03-18
If you have the Synaptic Package Manager installed open it and remove Emerald and all associated packages and residual configuration . To remove the packages right click on the line where they appear and mark for complete removal and select apply. Use the search filter to locate Emerald.   

After that open your home folder and press Crtl + H and delete the .emerald folder if there is one. If you have installed Emerald via a PPA open the update manager and go to settings > other software and remove the sources. 

If it is a PPA there may be a purge command on page where you located the installation instructions.

---

