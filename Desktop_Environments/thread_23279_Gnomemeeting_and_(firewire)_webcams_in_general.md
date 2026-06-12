---
title: "Gnomemeeting and (firewire) webcams in general"
date: 2005-04-01
forum: Desktop Environments
---

### Post by Liau on 2005-04-01
Hi all

I have an Orange Micro iBot firewire webcam, and it doesn't seem to be working too well in Hoary : /

Right now I'm using Coriander ([http://www.tele.ucl.ac.be/PEOPLE/DOUXCHAMPS/ieee1394/coriander/](http://www.tele.ucl.ac.be/PEOPLE/DOUXCHAMPS/ieee1394/coriander/)) as a control panel to start / stop / redirect the feed from the iBot - I can get a live feed from the webcam, and I can save a stream of images to disk, but I can't seem to get it working with Gnomemeeting!

Basically, using Coriander I attempted to redirect the video feed to /dev/video0 so the feed would have been usable by software which uses video4linux (such as gnomemeeting) right? I'm a little unclear on this point being new to linux.

However, /dev/video0 doesn't seem to exist, and I don't know how to *make* it exist :) Can anyone offer any suggestions please?

thanks!

---

### Post by Liau on 2005-04-01
:( Nobody has any idea?

---

### Post by anil_robo on 2005-12-17
First, check your /dev directory in file manager. Check for files named video, video0 or video1. Whichever exists, is your video output.

---

