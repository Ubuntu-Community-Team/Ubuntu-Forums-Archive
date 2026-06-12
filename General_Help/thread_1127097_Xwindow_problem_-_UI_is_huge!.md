---
title: "Xwindow problem - UI is huge!"
date: 2009-04-16
forum: General Help
---

### Post by GaryVivo on 2009-04-16
I am using Xwindows (X11) to launch a browser, when I connect to my monitor and run in 1280x1024 everything works fine, however when I connect to my TV and set to 720p firefox launches with a massive UI, the font and icons are huge in the centre of the screen, my xorg.conf appears not to be used as it is default and I am using xrandr -s to set the resolution. 
  
 If I run Opera, everything is rendering perfectly, however with Firefox (and any other program) the screen looks like it is displaying only the middle part of a massive resolution. 
  
 When I use xrandr -s "1280x720", the TV reports that it is set into 720p resolution, and opera is appearing in 720p. I have googled for hours with no help, so any advice would be awesome!

---

### Post by GaryVivo on 2009-04-16
Ok, slight progress.

It appears that the TV is not passing some information when probed like the monitor is. I generated a new xorg.conf file using 

# Xorg -configure


and it created a new xorg.conf that had the correct intel driver installed. I then added the 720p mode and a DisplaySize which I found on a wiki for MythBuntu. startx now boots into 720p without using the xrandr command so it's definitely taking the config changes.

I'm tearing my hair out here!

Attached below are my xorg.conf and xorg.0.log files...

---

