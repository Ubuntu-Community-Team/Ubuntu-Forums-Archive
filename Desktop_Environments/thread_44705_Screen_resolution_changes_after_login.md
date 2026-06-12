---
title: "Screen resolution changes after login"
date: 2005-06-27
forum: Desktop Environments
---

### Post by cronholio on 2005-06-27
After the installation, everything was fine. My login screen as well as the desktop were displayed at 1024x768.

Then I installed VMware and ever since the screen resolution changes to 640x480 after the login. I can change it back from the menu but this is unconvenient to say the least.

I deleted 640x480 from xorg.conf which doesn't help. I checked my X11 directory for changed files and couldn't find any. I checked the init script vmware runs at boot time and couldn't see anything suspicious.

Any hints? :roll:

---

### Post by intangible on 2005-06-27
In VMWARE goto **Edit->Preferences->Display** and monkey with the display settings there, in particular the "Resize Host" option. 

Hope that works for you.

---

### Post by cronholio on 2005-06-28
I checked the "Don't resize" box in VMware and it didn't work out... :???: Thanks for your help though.

Any other ideas? The problem may not even be VMware-related.

---

### Post by cronholio on 2005-06-28
Solved. I changed some setting in the Configuration Editor.

---

