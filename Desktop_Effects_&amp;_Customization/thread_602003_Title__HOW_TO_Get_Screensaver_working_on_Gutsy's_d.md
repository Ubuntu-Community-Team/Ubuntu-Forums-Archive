---
title: "Title:  HOW TO: Get Screensaver working on Gutsy's default compiz"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by scottDkoDer on 2007-11-03
Well, for those that are using Gutsy and would like to have the additional eyecandy plug-in 'Screensaver' working with Gutsy's default compiz-fusion, I'm presenting this guide.  This tutorial assumes that:

1) You have a fresh install of Gutsy.
2) You already have Gutsy's default compiz working.
3) You are running as user and not root.

NOTE: compiz-fusion is installed by default in Ubuntu Gutsy and will work as long as you have a video card with appropriate drivers and proper configuration.  This is beyond the scope of this tutorial, but there are a plethora of guides to configure your graphics card on Gutsy.

```
sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc x11proto-scrnsaver-dev libxss-dev
wget -O /tmp/screensaver.tar.gz 'http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f' mkdir -p  ~/compiz/
tar -xf '/tmp/screensaver.tar.gz' -C ~/compiz/
cd ~/compiz/screensaver
make
make install
```

If there are any problems, please check the prerequisites first, then ensure you have followed all instructions and typed all commands correctly.  Each should return without errors. If all is in order and there are any issues, then post any problems or suggested changes here.

Enjoy,

Scott

---

### Post by m3alnemer on 2008-03-25
i did install it. but where do i find its configurations to get it to work ?

---

### Post by LaaZ on 2008-03-25
Under "Extras" category of CCSM (System >> Preferences >> Advanced Desktop Effects Settings). I had to reboot to get it working properly, don't know why. But now its working fine, thanks scottDkoDer!
Good Look m3alnemer.

---

### Post by nowhere@cox.net on 2008-03-27
I compiled this but it's not quite working. First, I set it to 1 minute before automatically activating but it never starts. I when ahead and bound a key to it (ctrl-alt-shft-L) and the windows will take off flying then disappear leaving only the skydome background showing with no animation. Moving the mouse fades back to the desktop correctly.


EDIT: Btw, the windows are disappearing after the fade in duration. If I lengthen it from the default 3 seconds to 10 second, the windows are visible flying around for 10 seconds...
Any clues? And the rotating cube works fine...

Thanks,
Eric

---

### Post by saracen on 2008-04-03
Could someone provide a deb for the screensaver plugin?

---

