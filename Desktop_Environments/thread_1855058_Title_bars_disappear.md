---
title: "Title bars disappear"
date: 2011-10-05
forum: Desktop Environments
---

### Post by Cpt Vimes on 2011-10-05
When I use window decoration themes that aren't standard like oxygen or air, the title bars disappear. Now I found two solutions for this on Google, but they don't work, although the problem is definitely related to the fact that I have an nVidia graphics card.

Solution 1: Get compiz-config, enable "window decoration".

I've done that, doesn't do anything.

Solution 2: Change color depth to <24 in /etc/X11/xorg.conf.

I don't have the file. I ran "nvidia-xconfig" and it screwed things up. My laptop would automatically start in console mode, I had to run "rm /etc/X11/xorg.conf" to get stuff working again.

Can anyone help me?

---

### Post by lcman on 2011-10-05
> **Cpt Vimes said:**
> When I use window decoration themes that aren't standard like oxygen or air, the title bars disappear. Now I found two solutions for this on Google, but they don't work, although the problem is definitely related to the fact that I have an nVidia graphics card.

Solution 1: Get compiz-config, enable "window decoration".

I've done that, doesn't do anything.

Solution 2: Change color depth to <24 in /etc/X11/xorg.conf.

I don't have the file. I ran "nvidia-xconfig" and it screwed things up. My laptop would automatically start in console mode, I had to run "rm /etc/X11/xorg.conf" to get stuff working again.

Can anyone help me?

This is a compiz problem. Try to make your settings like the one in the pics. Then log out and log in again to see if it works.

---

### Post by Cpt Vimes on 2011-10-05
My settings were already set like that. My Compiz Settings Manager also looks quite different from that, too.

---

