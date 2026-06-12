---
title: "How to &quot;unlock&quot; Right-Click on Desktop?"
date: 2008-02-21
forum: Desktop Environments
---

### Post by AmazingBlair on 2008-02-21
My Desktop is locked, for want of a better term. Specifically, there is **no response** to **RIGHT-CLICK**, so I can't create a launcher or change the desktop background. How can I "unlock" the desktop? (and how did it get locked in the first place?) In all other respects it's fine.        

Note:  This was an Ubuntu server install, and then I used "sudo apt-get install ubuntu-desktop" to give me the Gnome GUI.  I don't know if that's relevant, but my laptop which has Ubuntu installed the normal way (without the server) has no problem with the desktop. Both are version 7.10.  Thanks for any help!        

-Amazing Blair

---

### Post by em3raldxiii on 2008-02-22
Since no one has answered in the last hour, I'll post my two cents.  It sounds like you have something about your mouse set up incorrectly, and this might be related to the way you installed Gnome.  I assume you never went through any mouse-configuration during setup?  If this is the case, then perhaps the hardware configuration defaulted with giving you a "one button mouse".  If this is the case, then I believe there is something you can do in your /etc/X11/xorg.conf file to tell the system that you have a multibutton mouse.

Also, there might be a configuration under your system menu.

Unfortunately, I am at work and not on a Linux system :( ...

Good luck!

---

### Post by AmazingBlair on 2008-02-23
> It sounds like you have something about your mouse set up incorrectly, and this might be related to the way you installed Gnome. I assume you never went through any mouse-configuration during setup?

Thanks, e8!

Actually, I should have mentioned that the right-click works fine in every other situation except for the bare desktop, so that seems to exclude the mouse as the problem. 

(By the way, I saw your profile photo:  your alt-rock wife is a babe!  No disrespect intended.)

-Amazing Blair

---

### Post by neonprophet on 2008-02-24
I have the same problem with XGL/Compiz. A restart usually fixes it.

---

### Post by AmazingBlair on 2008-02-24
> **neonprophet said:**
> I have the same problem with XGL/Compiz. A restart usually fixes it.

I wish! No such luck, however; the non-functional right-click on the desktop has survived several reboots and power-downs. Thanks for your input. 

I'm wondering if there isn't a **property of the desktop** that has been set to limit user control. If so, then there must be a way to reset it back to normal. Anybody have any thoughts in that direction? 

-Amazing Blair

---

