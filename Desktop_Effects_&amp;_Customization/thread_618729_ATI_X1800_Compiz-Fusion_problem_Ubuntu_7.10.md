---
title: "ATI X1800 Compiz-Fusion problem Ubuntu 7.10"
date: 2007-11-20
forum: Desktop Effects &amp; Customization
---

### Post by melenor on 2007-11-20
I have an ATI X1800 and ubuntu 7.10 i tried installing the restricted drivers and enableing the compiz-fusion but it says that "composite extension failed" and then without the restricted driver enabled it says "Desktop Effects could not be enabled" i don't use ubuntu for 3D gaming so i really just want to find a way to get compiz-fusion to work

---

### Post by melenor on 2007-11-21
I have tried using the old method with no luck and was unable to find a guide to help me if anyone know of a guide or know how to help that would be very helpful thank you.

---

### Post by amadeus266 on 2007-11-21
Try this: [https://launchpad.net/envy](https://launchpad.net/envy)

---

### Post by RDV on 2007-11-21
I have an ATI X1800 graphics card and Compiz working on Gutsy 7.10

I suspect the issues you have revolve around the version of the ATI restricted drivers you are using. If you are using drivers earlier than 8.42.3 then you will need to install. additional software. 

This is due to a lack of AIGLX support in ATI drivers prior to 8.42.3. My recommendation is to upgrade to the latest ATI drivers. Be warned that there seems to be a significant memory leak. in the 8.42.3 drivers when executing Open GL apps (e.g. run fgl_glxgears) (see reference [http://www.phoronix.com/forums/showthread.php?t=6438](http://www.phoronix.com/forums/showthread.php?t=6438) )

The recommendation in the previous reply ([https://launchpad.net/envy](https://launchpad.net/envy)) of using Envy to install the latet ATI drivers is a good idea or follow the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) which even has information on getting Compiz working (see # 3.2 3D desktop effects)

Be sure you uninstall your current ATI restricted drivers before using Envy. Envy's uninstall only works when Envy installed the drivers in the first place.

Good luck.

---

### Post by melenor on 2007-11-21
how do i update my ATI driver i tried to update no luck i tried uninstalling then reinstalling than updateing but it was always 8.37 and i need to get 8.4 or above

---

### Post by patryk77 on 2007-11-21
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

I had a lot of problems getting it to run on my X1600...

Using this guide I finally got everything to run.
Make sure you do NOT install the xserver-xgl package, as that seems to fubar rendering on my ATI 

"glxinfo | grep render" showed "rendering: No" and renderer as Mesa until I uninstalled xgl.

Uninstalling it seems to make it use AIGLX, which makes Compiz and Everything else work.

Still getting some minor issues sometimes, but I guess all in all it is to be expected as most of these features are brand new, and still being developed.

As for using Envy, I personally don't recommend it... seems more trouble than it's worth and at least if you use the guide you have a better understanding of what actually happens.

---

### Post by melenor on 2007-11-21
i followed everything on the wiki ati installs and my fgrlxinfo it says
            display: :0.0  screen: 0
            OpenGL vendor string: ATI Technologies Inc.
            OpenGL renderer string: Radeon X1800 Series
            OpenGL version string: 2.0.6958 Release
but when i try to enable the visual effects it says "The Composite extension is not available"
what can i do to fix that?

---

### Post by Forlong on 2007-11-22
See the last step [here](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support)

---

### Post by melenor on 2007-11-22
I followed the blog's last step and this came up 

Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 1002:7100 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
/usr/bin/compiz.real (core) - Fatal: No composite extension

(gtk-window-decorator:6078): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

(gtk-window-decorator:6078): Gdk-WARNING **: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap

I have no idea what this means but compiz-fusion no start

---

### Post by Forlong on 2007-11-23
```
Checking for Composite extension: not present.
```
Check out step 10 of the same guide mentioned above.

---

