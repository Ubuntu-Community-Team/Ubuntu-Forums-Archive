---
title: "Beryl/Emerald crashes upon its startup"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by Sephoroth on 2007-08-14
I'm not sure why this problem started, since Beryl had been running perfectly for a few days, but now every time I attempt to select Beryl via "Beryl Manager" as the primary window manager, it instantly reloads metacity.  Originally I believed the problem may have been due to a Nvidia driver reinstallation or screen resolution change, but after attempting to uninstall/reinstall the driver via Envy and Automatix, reverting to the old resolution, and ensuring direct rendering is working, I'm pretty sure the problem is elsewhere.

In addition, selecting System -> Preferences -> Desktop Effects opens a window containing the error "The Composite extension is not available."

So far I have tried a complete uninstallation of everything related to Beryl through Synaptics Package Manager (everything that was returned in the search query for "Beryl") and then reinstalled it as I had done when I first installed Ubuntu but nothing has worked.

Does anyone have any idea why Beryl is acting this way or more importantly, how to fix it?

---

### Post by EXCiD3 on 2007-08-15
It could possibly be a problem with Beryl's settings itself. I have had problems like this before, and i found that going through Synaptic, and "Completely Removing" every package related to Beryl and reinstall all of them fixed it.
> The Composite extension is not available. sounds to me like it is not enabled in your xorg.conf file. Try enabling compositing in your xorg.conf by doing this:
1) Open terminal
2) Type this:
```
sudo gedit /etc/X11/xorg.conf
```
3) Add the following lines to the very bottom of the file:
```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```
4) Press Ctrl-Alt-Backspace to restart Gnome, and try running Beryl now.

I also recommend this site: [http://compiz.org/NVidia]("http://compiz.org/NVidia") as it has all the information for configuring your xorg.conf file for Compiz/Beryl. Read through it and make sure you have done everything it says if the above steps do not work.

Good luck!

---

### Post by Sephoroth on 2007-08-15
Thank you!  Both your advice (involving compositing) and the guide helped a lot! and it finally seems to work (even if in the process I almost threw my computer out the window ;).  I ended up switching to compiz since I figured I might as well get used to it since Beryl is discontinued.  Once again, thanks!

---

