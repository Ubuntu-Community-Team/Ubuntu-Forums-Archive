---
title: "compiz error - don't know what to do ::unsure if duplicate::"
date: 2008-01-29
forum: Desktop Effects &amp; Customization
---

### Post by rpzatkof on 2008-01-29
I'm running on a Dell Latitude D830 
4 GB RAM
intel 965 express chipset family


I'm trying to get compiz to work and I added intel to the whitelist and removed it from the blacklist (followed directions on another forum topic - said it was better than SKIP_CHECKS=yes)  not sure how to get it running/whether I can

help?

~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0




~$ glxinfo | grep directdirect rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)



is there anyway that I can get direct rendering/get compiz to work???

---

