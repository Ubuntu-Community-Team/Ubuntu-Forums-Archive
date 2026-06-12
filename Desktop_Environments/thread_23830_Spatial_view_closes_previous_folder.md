---
title: "Spatial view closes previous folder"
date: 2005-04-04
forum: Desktop Environments
---

### Post by Curinir on 2005-04-04
I am using the spatial view (as in /apps/nautilus/preferences/always_use_browser not set) in Gnome. This has been working perfect for me since it was released. But a couple of days ago, something strange happened. After a reboot (and I had run a apt-get upgrade during my last session), my nautilus started to behave strange.

When I have one folder open, let's say /home/curinir, and when I from this folder open /home/curinir/workspace, it opens the folder /home/curinir/workspace the place it is supposed to and activates this window. But the thing that bugs me is that in the same time, it closes the /home/curinir window!

I have looked in gconf-editor to try to locate something that enables/disables this, but have come up with nothing.

Any suggestions?

---

### Post by erik21d on 2005-04-04
I've been having the exact same problem (also happened a couple days ago) so I moved on to browser view. There is a setting in gconf-editor (/apps/nautilus/preferences/window_always_new) that I think should solve this problem but it seems to be broken. Anyone out there know?

---

### Post by mcfly on 2005-04-04
Same problem here. It gets pretty annoying to work with after a while, so I switched to browser mode. I'd love to have it back to its old behaviour though.

Edit: Just realized there's quite a bit of discussion about it here: [http://ubuntuforums.org/showthread.php?t=23610](http://ubuntuforums.org/showthread.php?t=23610)

---

### Post by LongTooth on 2005-04-04
I noticed the change to. Though I don't see it as a bug. It's somewhere between spatial and browser view. If you notice, one can move back to the previous folder via the button on the lower left hand corner. Can't say if this will stay as it is but I'm working with it. If you still want to open a separate window just use the scroll wheel. Works for me.

---

### Post by Spark* on 2005-04-04
Well, it's supposed to be a feature...
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8516](https://bugzilla.ubuntu.com/show_bug.cgi?id=8516)

Also see various threads in this forum. It made me a very unhappy ubuntu-user, especially the way how this was decided. It is immensely frustrating to me that a huge bunch of GNOME users will get a totally wrong impression of spatial Nautilus.

---

### Post by rolfpal on 2005-04-06
You can have the proper gnome behaviour if you want.

You can change this behaviour in Applications>System Tools>Configuration Editor

Put a checkmark on apps>Nautilus>preferences>no_ubuntu_spatial

I found it really irritating.  I had just got used to spacial browsing and got my shortcuts organzed and they go and change the whole freakin scheme again.

It is really confusing to people who come to my house and use my media box.

---

### Post by lindkvis on 2005-04-06
I also agree that this was a bad decision, especially given that it is a Ubuntu only feature and thus not documented elsewhere.

Making a decision and **sticking** to it is sometimes just as important as the decision in the first place.

---

