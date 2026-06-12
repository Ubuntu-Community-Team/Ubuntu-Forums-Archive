---
title: "[SOLVED] Finding compizconfig-settings-manager"
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by Living2007 on 2008-03-19
How and where do I find compizconfig-settings-manager. I'm having trouble finding it in the package manager

P.S; I have not updated Ubuntu at all

---

### Post by PurposeOfReason on 2008-03-19
sudo aptitude update && sudo aptitude install compizconfig-settings-manager

---

### Post by Living2007 on 2008-03-19
Is this under terminal or package manager

---

### Post by PurposeOfReason on 2008-03-19
This is in a terminal.

---

### Post by Living2007 on 2008-03-19
I also need help understanding why standard desktop effect don't work.

I enable normal effect but it says that could not find "nvidia - glx" what does this mean?

---

### Post by Cresho on 2008-03-19
well, you just installed a new operating system right?  Now you need to configure your video card.  Nvidia supports linux with proprietary drivers.  what you need to do is tell us what video card you have.  If you have an nvidia besides the 8800gt, you can install the latest driver from settings->administrator->hardware drivers.  click and approve and reboot.  then you can enable the desktop effects.  advanced desktop effects will not be shown in that panel you look at.  you need to install it through synaptic.

NOTE: if you see pink halo around your window and not a dark one, then most likely the driver has not been updated.  There is a bug and they are working on it.  If you are a more of an advanced user, you can install a previous version which will fix the pink halo problem.

happy hunting.

---

### Post by Living2007 on 2008-03-19
Thanks, I'll come back if the problem has been fixed

---

### Post by Living2007 on 2008-03-19
PS forgot to say it was an nVidia GForce4 MX 4000 card

---

### Post by PurposeOfReason on 2008-03-19
Go to the settings menu, go to admin, then restricted drivers. Enable that and restart X (ctrl+alt+backspace).

---

### Post by Living2007 on 2008-03-27
I need to fix the "nvidia-glx" problem ([http://ubuntuforums.org/showthread.php?t=728621]("http://ubuntuforums.org/showthread.php?t=728621"))

---

