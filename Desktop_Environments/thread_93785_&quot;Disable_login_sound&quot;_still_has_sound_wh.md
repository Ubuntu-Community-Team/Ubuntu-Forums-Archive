---
title: "&quot;Disable login sound&quot; still has sound when login"
date: 2005-11-22
forum: Desktop Environments
---

### Post by Huike on 2005-11-22
Hi folks

Installed Ubuntu 5.10 on an old Acer Travelmate 525TE laptop with pci=noacpi option (otherwise it will stuck at the %86 ide=ide-cd screen and stays forever). The installation was pretty smooth. 

Disabled the login sound in the System -> Preferences -> Sound -> Sound Events, reboot, login and the login sound is still there. But the logout sound is gone.

Checked the System -> Administration -> Login Screen Setup -> Accessibility the login sound is not ticked.

Tried to install Ubuntu 5.10 on another Acer Travelmate 521T but it had the same problem.

Have searched the whole forum and tried all the things mentioned there with no luck.

Anybody has any ideas? Is there a configure file I can edit to disable it? Thanks.

---

### Post by Xian on 2005-11-22
[QUOTE=Huike]Disabled the login sound in the System -> Preferences -> Sound -> Sound Events, reboot, login and the login sound is still there. But the logout sound is gone.[/QUOTE]
Remove the wav file associated with the login.
Check for:

/usr/share/sounds/startup3.wav
/usr/share/sounds/startup.wav

---

