---
title: "bypassing emerald?"
date: 2007-12-31
forum: Desktop Effects &amp; Customization
---

### Post by pikaia on 2007-12-31
I've been swapping out themes like crazy since I made the switch to Ubuntu about 3 months ago.  I downloaded Emerald and installed a few themes, and been using one exclusively now for a few weeks now, but I downloaded a few NON-emerald themes that I'd like to implement but they won't take effect.  Sometimes the Panel bar will change but never the window border.  I go through System-> Preference-> Appearance and try to change the theme there but it no longer takes place.  Is there a way to bypass Emerald, or disable it so that I can get other themes to work?

Also is there a way to change the colors used by these NON emerald themes that don't have the color palette available for configuration (grayed out)?

Thanks

---

### Post by pikaia on 2007-12-31
I guess its the Compiz themes that no longer seem to function properly.  Is there anyone who has any ideas?

Also when I Right-click the panel and click Properties.  It give the error "error accessing file Midnightblack/gtk2.0/.../menubar" not found"  I am not using that theme and no matter which theme I switch to I always get that error.  (And yes the file actually DOES exist in the folder where it is looking.

Again, any help is greatly appreciated.

---

### Post by pikaia on 2007-12-31
Okay, I think I figured out the Emerald overriding Compiz issue.  But I shouldn't have to disable all effects to get compiz to work over emerald should I?  I just turned off 'Visual Effects.'  As far as the error I mentioned before, it is still present so any insight...

Thanks.

---

### Post by FuturePilot on 2008-01-01
Either uninstall Emerald or create this file
```
gedit .config/compiz/compiz-manager
```
It's normal if it's blank.
Add this line to it.
```
USE_EMERALD="no"
```
Now the next time you login Compiz will use the gtk-window-decorator instead of Emerald.

---

