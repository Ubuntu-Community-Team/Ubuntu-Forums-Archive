---
title: "Gnome-Terminal"
date: 2011-05-16
forum: Desktop Environments
---

### Post by Polar Humenn on 2011-05-16
I have an interesting problem with using Gnome-Terminal in my KDE environment on Natty. Anytime I either stretch the Gnome Terminal window or Zoom In, it blanks the whole screen (double display) and a lot of the menu graphics get sheered when it comes back on all Gnome Terminals. Strange. Do this enough, and KDM restarts.

I know, I know, why am I runnning Gnome Terminal when I should be running Konsole, because I can't get konsole to work correctly. (If you're interested, It won't keep a ssh window alive running alpine in a profile start).

I have a GeoFordce 7200 and running the proprietary NVidia drivers. Nouveau was just too slow, memory hungry, and my desktop effects kept quitting. I believe I still had the same problem with using Gnome-Terminal. 

Tell me how to make a Konsole Profile work with a startup command of "ssh name@localhost -X -t alpine"
and I won't use Gnome-Terminal, but it always exits.

But I thought, it was interesting that the Zoom-In functionality of Gnome-Terminal, which I thought was should just enlarge the font, or stretching the window, would cause the whole display to blank. Any ideas? The screen blanking doesn't happen when stretching other windows, just the Gnome-Terminal.

---

### Post by wildmanne39 on 2011-05-16
> **Polar Humenn said:**
> I have an interesting problem with using Gnome-Terminal in my KDE environment on Natty. Anytime I either stretch the Gnome Terminal window or Zoom In, it blanks the whole screen (double display) and a lot of the menu graphics get sheered when it comes back on all Gnome Terminals. Strange. Do this enough, and KDM restarts.

I know, I know, why am I runnning Gnome Terminal when I should be running Konsole, because I can't get konsole to work correctly. (If you're interested, It won't keep a ssh window alive running alpine in a profile start).

I have a GeoFordce 7200 and running the proprietary NVidia drivers. Nouveau was just too slow, memory hungry, and my desktop effects kept quitting. I believe I still had the same problem with using Gnome-Terminal. 

Tell me how to make a Konsole Profile work with a startup command of "ssh name@localhost -X -t alpine"
and I won't use Gnome-Terminal, but it always exits.

But I thought, it was interesting that the Zoom-In functionality of Gnome-Terminal, which I thought was should just enlarge the font, or stretching the window, would cause the whole display to blank. Any ideas? The screen blanking doesn't happen when stretching other windows, just the Gnome-Terminal.

It is most likely a bug in the nvidia driver you can check bug report to make sure, I have nvidia and I have to run the 173 driver instead of the current one, or I had the same problem,also I see people are using the experimental 3d driver, almost all nvidia cards have a bug with the recommended driver.:)

---

