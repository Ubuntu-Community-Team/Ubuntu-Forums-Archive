---
title: "Unstable Desktop and GDM"
date: 2007-05-09
forum: Desktop Environments
---

### Post by Corgan on 2007-05-09
I've grazed over the forums without any luck finding my exact scenario so I figured I'd post.

I've ecounteed a problem on both a 6.10 and 7.04 install on two different machines in the same location. When switching between user accounts via the GDM, either the GDM or the new desktop itself will "glitch," seemingly when the mouse goes out of bounds onf the screen. The result is the desktop shifting, for example, to the upper left hand of my screen revealing 3/4 of the screen filled with cached data - information from PREVIOUS logons. Browser grabs, IM conversations, open apps - a capture of previos activity is there.

A simple move of the house will shift the screen back into it's proper place, so it's not a crippling issue, but I'm very concerned about this in terms of security and privacy, as it literally gives users on the same machine a glimpse of what everyone is doing.

Is this a known problem and is there a fix?

---

### Post by Kobalt on 2007-05-09
Could be linked to a small glintch in Xserver : what graphic card do you have ? did you install drivers for this ?

---

### Post by Corgan on 2007-05-09
Thanks for the response.

It's happened on a variety of machines.

One NVIDIA TNT2. I do not use the legacy driver.

One onboard video, Intel driven I believe.

Another NVIDIA whose model I forget. In all honesty it may have been a TNT2 as well.

Never considered that. heh. Anyway. I've experienced it multiple times and I'll admit it's unnerving. Otherwise, the X seems to run fine.

---

### Post by Corgan on 2007-07-10
An update on this, just in case anyone is having a similar problem. About a month or so ago, I officially moved over to the Legacy NVIDIA driver, hoping it would help.

Thus far: It has not. I still get the same occasional screen distortion with cached screengrabs, which is a bit unnerving.

If anyone has encountered this or has a fix. Please let me know.

---

