---
title: "HELP!!! User theme change completely broke Gnome Shell! Stuck in command line!!"
date: 2015-12-24
forum: Desktop Environments
---

### Post by The Bright Side on 2015-12-24
Hey guys!

I wanted to try some new themes in Ubuntu GNOME 15.10, so I downloaded the "Vertex" Gnome Shell theme, installed it by using the browse button in Gnome-Tweak-Tool and selecting the ZIP file, and then my desktop froze and after a while quit to the command line.

Now, every time I reboot, I land in the command line!!

I'm freaking out. How can I reset the theme to get my GNOME Shell back?!

Please help! :-(

---

### Post by The Bright Side on 2015-12-24
Fixed it.

sudo apt-get remove gnome-tweak-tool

Afterwards, I can reboot and then reinstall the Tweak Tool. The "User Themes" extension is now broken though. Every time I activate it, my GNOME Shell completely breaks again and I'm back in the command line. I tried resetting the GNOME Tweak Tool's setting to defaults, to no avail. Guess that's ****ed now. Oh well.

---

