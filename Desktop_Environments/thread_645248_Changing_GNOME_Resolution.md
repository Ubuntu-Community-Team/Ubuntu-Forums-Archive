---
title: "Changing GNOME Resolution"
date: 2007-12-19
forum: Desktop Environments
---

### Post by makemeegg on 2007-12-19
Hello,

I just installed Ubuntu 7.04 server and after applying all updates I installed GNOME via $sudo apt-get install ubuntu-desktop.  The install went fine and when I got the the resolution part of the install I chose to install 1280x 1024x 800x 600x.  It said that is will use the top resolution be default.  I don't think my monitor can handle the top resolution because when I $startx or do a fresh reboot I only get a black screen.  I know it boots into GNOME because I get the drum rolls at the login prompt.  Does anyone know how to fix this problem or to maybe eliminate a couple of the resolutions I picked durning setup?

Thanks.

---

### Post by jken146 on 2007-12-19
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by makemeegg on 2007-12-19
thanx for the quick reply but now I feel really dumb..........I tried the box on a newer lcd monitor I have and had the same problem.........I was thinking that it was the video card so I was going to throw in a spare agp card I have only to determine that this old box only has onboard video and I am assuming its 16bit.........There are also no agp slots so I can't throw in one of my spares........Can someone please confirm that my crappy onboard video was causing a black screen or vertical colorful lines when Ubuntu booted into GNOME........I should mention that command line works fine with the onboard video.....

Thanks!

---

