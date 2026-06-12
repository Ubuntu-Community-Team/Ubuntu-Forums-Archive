---
title: "able to remember windows size&amp;position"
date: 2011-10-23
forum: Desktop Environments
---

### Post by candleson on 2011-10-23
Hi,
I am a newbee in Linux. So, pls forgive me for an oversimple or to-you-annoying message from me. 
I recently installed xubuntu 11.10 and loved it.
I want xubuntu to remember windows size and positions I've opened.

Is it possible to enable it remember windows size and positions?

Thank you

---

### Post by Jose Catre-Vandis on 2011-10-23
If you resize a window and close it it should reopen at that size.

You can fiddle with placement a bit in the Settings Manager > Window Manager Tweaks > Placement, and snapping to borders and other windows in Settings Manager > Window Manager > Advanced

But you can define size and placement on startup by using a program called devilspie. You need to set up config files for specific windows or applications. This only works when you start the application / open the window, these no automagic remembering going on (unless you write a serious script!).

---

### Post by gsmanners on 2011-10-23
Window size and position are strictly controlled by gtk when anything (whether it's Gnome, Xfce, Openbox or whatever) uses it. The toolkit decides window position, generally. With Xfce, you can override that to a certain degree with the Window Tweaks, but the final decision on window position is really in the hands of the app itself. The app can then maximize or adjust the window position to wherever the app itself wants to go.

And devilspie is a nice, kludgy solution you might consider.

---

### Post by candleson on 2011-10-23
Window Manager Tweaks helped somewhat.

Thank you.

---

