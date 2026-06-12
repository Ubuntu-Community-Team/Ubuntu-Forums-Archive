---
title: "Visual Effects?"
date: 2007-11-23
forum: Desktop Effects &amp; Customization
---

### Post by bbrff on 2007-11-23
When trying to get extra visual effects the screen pops up "composite index not available".
Is there a fix for this? Thanks

---

### Post by daimaru on 2007-11-23
> **bbrff said:**
> When trying to get extra visual effects the screen pops up "composite index not available".
Is there a fix for this? Thanks

you might have composite "0" in xorg.conf 
post your /etc/X11/xorg.conf file

and you have to have restricted drivers installed, so do that if you haven't already. 

please include what system your running and a brief description of your hardware. you can edit your profile to include if your running dapper feisty or gutsy etc in the User CP menu (of this forum). and in your signature you could give some general idea of your computer hardware like graphics card sound card wifi-card and motherboard. 

that makes troubleshooting way easier.
thank you

---

### Post by Ub1476 on 2007-11-23
If you have an ATI card with drivers from the Restricted Driver Manager (System>Admin) make sure xserver-xgl is installed. You can find it in synaptic (System>Admin>Synaptic packagemanager).

---

