---
title: "xgl to xserver"
date: 2007-10-21
forum: Desktop Environments
---

### Post by tynen on 2007-10-21
I installed XGL and made it run instead of Xserver. Is there a way to do this in reverse? I want to run a program that requires direct rendering, I am running a GeForce 7900gs and I have the most current driver for it. 

I'm hoping Xserver will do direct rendering because XGL isn't.

---

### Post by ubuntu dave on 2007-10-21
Just uninstall XGL.
I'm guessing you don't need XGL anyway...
XGL and xserver 'do' direct rendering though...
Are you sure you installed your graphics card drivers correctly? If so, what makes you think XGL isn't allowing/doing direct rendering? (iirc 'glxinfo' returns 'disabled' for direct rendering in XGL even when that's not the case).

---

### Post by n-alexander on 2008-02-06
Here is what is says right after installation:

The Xgl server will now be started automatically next time you login.  It is no longer necessary to use any special X session to start Xgl, and such sessions will likely fail to work properly.  Please select a regular session from your session manager next time you log in.  To disable Xgl autostart for this user, create a file named ~/.config/xserver-xgl/disable

Hope it helps.

Alex

---

