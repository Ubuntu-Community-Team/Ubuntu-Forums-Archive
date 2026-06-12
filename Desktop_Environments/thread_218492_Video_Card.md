---
title: "Video Card"
date: 2006-07-18
forum: Desktop Environments
---

### Post by RexInTheCity on 2006-07-18
I'm trying to do two things: Get dual screens (extend desktop to second screen) and get 3D desktop working.

I've done some googling to try and figure out how to get the desktop to extend to the other monitor instead of just mirroring it but I've gotten nowhere. I'm using an ATI Radeon 9800Pro

When I run 3Ddesktop I get this:
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.

So does anyone know of a good step by step guide on extending desktops or know how to get 3D Desktop working?

---

### Post by s_p_a_r_k_y on 2006-07-18
> **RexInTheCity said:**
> I'm trying to do two things: Get dual screens (extend desktop to second screen) and get 3D desktop working.

I've done some googling to try and figure out how to get the desktop to extend to the other monitor instead of just mirroring it but I've gotten nowhere. I'm using an ATI Radeon 9800Pro

When I run 3Ddesktop I get this:
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.

So does anyone know of a good step by step guide on extending desktops or know how to get 3D Desktop working?

Hi, so are you trying to use Xinerama to add (extend) the 2nd screen? If so, I think xinerama turns off 3d acceleration. If you want 3d accelleration you need to turn off xinerama and setup 2 separate desktops. I did this not to far back and may still have the config files if you want em for example purposes

---

### Post by RudolfMDLT on 2006-07-18
Hi,

Enter 
> fglrxinfo


into the terminal and tell me what it says? The fact that it can't render Direct 3D may mean that your card is not configured correctly? I have an Ati 9600 Pro and got mostly the same result when I was still running MESA drivers.

---

### Post by RexInTheCity on 2006-07-18
> **RudolfMDLT said:**
> Hi,

Enter 


into the terminal and tell me what it says? The fact that it can't render Direct 3D may mean that your card is not configured correctly? I have an Ati 9600 Pro and got mostly the same result when I was still running MESA drivers.

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Looks like I'm still running MESA drivers, how do I switch over to better ones?

Edit: I did some more searching and found the ATI driver setup guide and got 3ddesk working.

---

### Post by RexInTheCity on 2006-07-18
> **s_p_a_r_k_y said:**
> Hi, so are you trying to use Xinerama to add (extend) the 2nd screen? If so, I think xinerama turns off 3d acceleration. If you want 3d accelleration you need to turn off xinerama and setup 2 separate desktops. I did this not to far back and may still have the config files if you want em for example purposes

Can you show me the config files and any guide you may have followed?

---

### Post by RexInTheCity on 2006-07-18
bump

---

### Post by RudolfMDLT on 2006-07-19
Hi RexInTheCity,

Your MESA... The output should have been something along the line of:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

You need to get the correct 3d driver running before you can start doing advanced stuff(i think;) ).

Anyway, you paid for your card's 3d ability so I would think you might want to get it working. Running an ATI card can be a big pain in the neck. This is how I got mine to work:

[http://www.ubuntuforums.org/showthread.php?t=195845](http://www.ubuntuforums.org/showthread.php?t=195845)

I think after this you might be able to run clone and extended desktops!

---

### Post by s_p_a_r_k_y on 2006-08-09
Sorry I was traveling for the last 3 weeks through europe and didn't have my lappy with me. I attached 2 config files I have used in the past.

---

