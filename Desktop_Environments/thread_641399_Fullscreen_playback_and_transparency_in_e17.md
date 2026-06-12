---
title: "Fullscreen playback and transparency in e17"
date: 2007-12-15
forum: Desktop Environments
---

### Post by mrblondeisback on 2007-12-15
So I have a Gutsy command line install and i've put e17 on there.  I'm very happy with Enlightenment, except that transparencies aren't working (cairo clock and aterm) and when I play back full screen video the desktop it was on just goes black when I close it down.  the other desktops are fine, and I can switch between the black desktop and the others freely.  I have an nvidia gforce 7600 with the nv driver, and I'm using vlc for playback.  I know it worked when I had gnome, so I assume it's an issue with Enlightenment.  Anyone got e17 and experienced the same problems?  Anyone know how to fix it?

---

### Post by smartboyathome on 2007-12-15
You have to have a compositing manager to use transparencies. Try installing xcompmgr and using that with these settings:

xcompmgr -cCfF -r7 -o.65 -l-10 -t-8 -D7 &

---

