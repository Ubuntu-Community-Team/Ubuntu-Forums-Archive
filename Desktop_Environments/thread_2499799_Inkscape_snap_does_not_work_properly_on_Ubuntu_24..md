---
title: "Inkscape snap does not work properly on Ubuntu 24.04"
date: 2024-08-11
forum: Desktop Environments
---

### Post by garethjenkinsuk on 2024-08-11
It seems the Inkscape snap does not work properly.

For some years I have been using Inkscape 0.92, running under Ubuntu 18.04, to drive my Liyu SC631 vinyl cutter using the Export/Plot extension.

I have put off upgrading for several years, as I was expecting some problems, but have finally upgraded to Ubuntu 24.04 and Inkscape 1.3.2, with Inkscape installed as a snap.

However, I could not get my cutter to work, getting the message "Could not open serial port.  Please check your device is running, connected and the settings are correct".  

I was using the same settings as under 18.04 and I knew the plotter did work with Inkscape 1.3.2 as running it under Windows 11 it worked fine (my new computer is dual boot) .
After my experience getting Inkscape to run 18.04 I assumed this was an issue with permissions or groups and spent a lot of time fiddling around trying to sort it out that way.

I finally uninstalled the snap, installed Inkscape using apt and the plotter started working fine.

Conclusion: the Inkscape snap, in particular the Export/Plot extension, does not work properly.

---

