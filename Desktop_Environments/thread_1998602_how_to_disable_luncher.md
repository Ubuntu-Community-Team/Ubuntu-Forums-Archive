---
title: "how to disable luncher?"
date: 2012-06-07
forum: Desktop Environments
---

### Post by westsunwestern on 2012-06-07
Hi friends
I installed a dock and i want to disable the luncher in unity desktop and use the dock.
i want a way to do that i can undo.
thank you

---

### Post by zombifier25 on 2012-06-07
There's a dirty hack to do this. Install ccsm first:
```
sudo apt-get install compizconfig-settings-manager
```
Then open it, choose Ubuntu Unity Plugin, choose Behavior tab first and set to autohide. Then, choose the Experimental tab. Be careful on this one, I suggest you DON'T use your middle mouse wheel to scroll, since it may screw up some settings. Decrease "Launcher Reveal Edge Responsiveness" and/or increase "Launcher Reveal Pressure" until there's no way you can make the launcher show again.

If you wish to undo your settings, on the right of each settings there are reset buttons.

---

### Post by black veils on 2012-06-09
as you have probably already seen, the unity launcher will still show when some actions are happening. i would recommend installing the xfce desktop environment, then choosing no or specific panels, then using your dock!

```
sudo apt-get install xubuntu-desktop
``` then restart.

when at the login screen, click the little icon at the top-right of your sign-in section, and choose xubuntu. it will remember your setting, and take you to the xfce desktop environment, all your normal applications will remain. if you dont like it, you can choose the unity desktop again.

---

