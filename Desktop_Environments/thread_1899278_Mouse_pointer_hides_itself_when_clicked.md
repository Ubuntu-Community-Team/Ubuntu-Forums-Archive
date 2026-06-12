---
title: "Mouse pointer hides itself when clicked?"
date: 2011-12-23
forum: Desktop Environments
---

### Post by javajames97 on 2011-12-23
When using Unity ubuntu in my VM the mouse pointer seems to randomly hide itself and also does this when i right-click. Does anyone know of any fix for this? Its a virtual box VM.

---

### Post by sikander3786 on 2011-12-23
Did you install the Guest Additions? If not, start your VM and go to Devices > Install Guest Additions.

Once installed, Press <Host Key> (It is <Right Ctrl> by default unless you change it) + I to toggle mouse integration.

That is the best solution that comes to my mind however I have myself experience some odd pointer behaviour whenever mouse integration is disabled with Natty and Oneiric in VM.

---

### Post by javajames97 on 2011-12-23
Yes i have installed guest additions and tried toggling mouse integration, also tried enabling and disabling different 2D/3D acceleration. I think its a problem with unity as it happens in parrallels desktop too, (mac host btw) and used to happen on my netbook and servers so i figure its a problem related to weaker graphics :/

---

### Post by javajames97 on 2011-12-23
and i did not have this problem when i had ubuntu installed on this same machine.

Furthur worth noting that parallels has a download for ubuntu which does not have this problem, but i ignored it because it is not the latest version, and now i have removed it :/

---

