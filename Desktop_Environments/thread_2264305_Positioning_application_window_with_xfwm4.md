---
title: "Positioning application window with xfwm4"
date: 2015-02-06
forum: Desktop Environments
---

### Post by cjsmall on 2015-02-06
xubuntu 14.10
xfce4 4.10
xfwm 4.11.2
vlc 2.2.0


When launching the VLC Media Player, the xfwm4 window manager determines its location.  This application does not support the X11 --geometry option, nor does it have any other positioning option.  Is there any other method I can use to force the resulting VLC window to a open at a specific screen position?  Thanks.

---

### Post by Bucky Ball on 2015-02-07
If I open VLC, move the window to where I want it, then choose 'Quit' from the drop-down menu, then reopen it, it opens where I closed it, if that makes sense. I am using xfwm 4.11.1 and VLC 2.1.4. Unsure if things have changed from there to what you are using.

No changing code required. Most windows do this in my experience. Using a 14.04 LTS minimal install with xfce4 as desktop environment.

---

### Post by cjsmall on 2015-02-21
I apologize for the long delay in getting back to this thread.

I do not observe the same thing that Bucky Balls indicates.  Whether I launch Vlc from the desktop or from another program, what i observe is that every instantiation of the Vlc window is located about 10 pixles lower and maybe 3 pixels to the right of where the previous Vlc window was located.  This creep becomes very noticable with a script that I use which repeatedly kills and relaunches Vlc as it iterates over a series of music files.

I checked my Window Manager Tweeks and under the Placement tab, the default placement is "Under mouse pointer".  If I change this to "At the screen center" it has no effect on the Vlc window placement.

I'm really looking for a way to specify absolute positioning from the command line.  I'm really surprised that all linux tools are not honoring the -geometry switch.

---

