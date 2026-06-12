---
title: "How I got Compiz to work on a Radeon HD2600XT and dual-head"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by dannns on 2007-11-08
Ok, I was finally able to get my ATI 2000 (2400, 2600, 2900) series card to work. This post is not an actual guide, but might be useful. Some of the steps might not be necessary like the XGL stuff, however those were steps I did take, so I didn't want to leave them out.

Throught the installation I was using partimage to make a full backup copy for every step. And I did not perform any update until everything was working.

I did a clean install of Ubuntu 7.10 64.

Installed the restricted drivers with the Restricted Driver Manager, then installed xserver-xgl, and restarted to a non working setup so X started in safe mode.

From there I downloaded Envy, and did the manual installation of ATI Driver 8.42.3. Now the display driver was working in X, however no acceleration yet, so I removed xserver-xgl, restarted. Then went to the ATI Control Center and setup my dual display as Big Desktop, rebooted, and it worked. However no Compiz yet.

Then I edited /etc/X11/xorg.conf and added the line   **Option "AIGLX" "True"**   under the "ServerLayout" section, and rebooted.

Up to now Compiz was not starting, so I decided to not use the compiz file modified by Envy, since it was giving an error about an open parenthesis on line 228. So I:

cd /usr/bin
sudo cp compiz compiz.bak
sudo cp compiz.envy compiz

Then I started Compiz from the Appearance Control Panel, and it worked!

I hope this helps. I didn want to write an actual guide, since I not sure if I forgot some of the steps.

Envy: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

