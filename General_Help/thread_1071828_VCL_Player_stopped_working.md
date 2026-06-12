---
title: "VCL Player stopped working"
date: 2009-02-16
forum: General Help
---

### Post by MyFathersSon on 2009-02-16
I was fiddling with the VLC interface selection and obviously picked the wrong interface.  The thing stopped working.  I tried doing a total uninstall but that didn't work.  So there must be some crumbs left that the uninstall didn't get.

I want to get it all out of the system and reinstall it.  How do I do it?

---

### Post by hansdown on 2009-02-16
Hi MyFathersSon.

Go to synaptic, find vlc, click on it. If it is still installed, you will get an option to```
 mark for complete removal
```. You can re-install after that.

---

### Post by mc4man on 2009-02-16
You didn't mention what version of vlc you're using.
In vlc 0.8.6 the config. files are in home folder -> .vlc (hidden folder
In 0.9.x they're in home folder -> .config/vlc

Instead of deleting just do this first, from a terminal

```
vlc --reset-config
```

---

