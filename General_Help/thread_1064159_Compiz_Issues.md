---
title: "Compiz Issues"
date: 2009-02-08
forum: General Help
---

### Post by supernova1 on 2009-02-08
Ubuntu 64 8.10

I installed the Compiz settings manager, I played around with the settings and had a lot of cool features enabled, however my CTRL key quit working, but it was still working to do compiz related stuff, such as CTRL+ALT to rotate the cube, but in firefox for instance CTRL+F would not open up the find bar.  Someone recommended uninstalling compiz, so I used apt-get to remove compiz, and then I did an apt-get to re-install all of the compiz stuff.  I tried to re-enable desktop cube, and other settings, but now none of them are features are working when I enable them in the compiz settings manager.  Do I have to enable compiz somewhere?

Thanks.

---

### Post by drs305 on 2009-02-08
> **supernova1 said:**
> Do I have to enable compiz somewhere?
You can run this to start compiz (Note some windows may close, including your browser. Reboot if necessary):
```
compiz --replace &
```

Or System > Preferences > Appearance > Visual Effects

---

