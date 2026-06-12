---
title: "funny problem with fglrx in 3d apps"
date: 2008-02-29
forum: Desktop Effects &amp; Customization
---

### Post by filibuster on 2008-02-29
Hi there,
I recently updated my fglrx-driver to version 8.2 and when i now try to run a 3d application i get a really funny distortion of the application-window, looks a little bit like a mosaic.
I uploaded a screenshot to rapidshare:
  [http://rapidshare.de/files/38710577/screenshot.png.html](http://rapidshare.de/files/38710577/screenshot.png.html)
This one is taken with glxgears, you probably know what it normally should look like.
If anybody has seen something like that before and has any idea what causes it, please help!

---

### Post by bixejo on 2008-03-02
I've found elsewhere (sorry I cannot remember exactly where) that this is a common known problem in fglrx 8.02. Hope the next release shall fix this but (if at some point I can give you more -any- references on this, I will post them right here.)

8.02 fixed many things in my box compared to 8.01, but that one goes worse now.

---

### Post by filibuster on 2008-03-05
Thanks for your reply, nice to hear that i'm not the only one with mosaic-like 3d apps.
so maybe it'll be the best to use the previous version of fglrx and wait 'til they cleaned out this problem, as there's probably no way of editing the sources...

---

### Post by bixejo on 2008-03-05
> **filibuster said:**
> 
[...]
so maybe it'll be the best to use the previous version of fglrx
[...]


Good luck. If 8.01 worked ok for you, then definitely you should not have upgraded. My personal policy with respect to these things is "if something works, best not touch it."

The last driver that worked reasonably well for me was 7.11. I was forced to upgrade to 8.01 because 7.11 stopped working after a system update that included some kernel files. But then I had to face the problem that I couldn't log out, switch user, nor restart X-server without getting an ugly system hang. After trying with about one dozen of non-solutions I found across the Internet, I resigned to be forced to shutdown or reboot any time I logged in. 8.02 fixed this, thank goodness, but now I get the mosaic-like 3D windows...

Seems to me that one should run away as far&fast as possible from ATI video cards if one plans to install any non-Windows OS...  *sob*

---

### Post by bixejo on 2008-03-12
Ok, here you may find it:

[https://bugs.edge.launchpad.net/ubuntu/+bug/192550](https://bugs.edge.launchpad.net/ubuntu/+bug/192550)

---

### Post by bixejo on 2008-03-12
I've just updated to 8.03 and seems that this problem has been solved. It persists however some other of the "classic" topics of fglrx, like blinking video playback image with Xv/OpenGL extensions, but looks like that bug's much deeper roots and it's not that easy to fix...

Apart from the above, 8.03 compared to 8.02:[LIST]
[*]glxgears: 30% FPS faster
[*]fgl_glxgears: 10% FPS faster (lost frame window when enabled compiz desktop effects)
[*]desktop cube rotation: much faster (cannot tell exactly how much, but it's sensibly faster)[/LIST]

---

