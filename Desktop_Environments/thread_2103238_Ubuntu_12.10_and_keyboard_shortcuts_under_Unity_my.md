---
title: "Ubuntu 12.10 and keyboard shortcuts under Unity mystiques"
date: 2013-01-09
forum: Desktop Environments
---

### Post by detl_ on 2013-01-09
Hi,
I upgraded to Ubuntu 12.10 some time ago. And I never had the need to modify the default keyboard shortcuts. But now I work within an Application that makes use of some shortcuts that are already used by Unity/Ubuntu.

I want to disable the following keyboard shortcuts :
1: ALT-F1 (current behaviour: Focus on the Dash starter)
2: ALT-F7 (move window)
3: ALT-F8 (scale window)
4: STRG-ALT-left/right/up/down (workspace switcher)

I found the definition of the shortcuts in the keyboard settings for 2, 3 and 4. Not for 1 though.

Here comes the mystique: When disabling them they get set again after reboot - but only sometimes. Even during a running session it happens that the shortcuts are enabled again.
I tought this is the case, because I used Gnome as DisplayManager before Unity jumped into the default. But I dont know which gnome configuration files I can delete.

I would be very happy if somebody can answer me:
A: how can I disable ALT-F1 keyboard shortcut persistently ?
B: make the disabled keyboard shortcuts persistently disabled ?

Thanks,
detlef

---

### Post by DimeDroll on 2013-01-21
Hello,
I'm upvoting this as I'm having similar problem.

My Ubuntu 12.10 unity uses "gnome-screensaver-command -lock" command to lock system screen. Hotkey for lock is "Super+L".
It works when I set it in Keyboard - > Shortcuts -> System ->  "Lock Screen".
However when I reboot system it stops working despite the fact it's still set correctly in Keyboard -> Shortcuts...
I need to go back there and re-set it, then it works back again.

So I need to reset this hotkey every time I boot my system or place crontab script that will do this for me, both ways are hack which is no good.

Please advise.

Regards,
Dima

---

### Post by mabtifro2 on 2013-02-18
I too have this problem. Every couple times i reboot, the my personalized shortcut keys get reset to default. And it's not just with alt keys. for example, i set F10 to minimize a window, and i set one other key which acts as a 'right click' as my show desktop button, but those get reset too. help would be great

---

### Post by klaus7 on 2013-02-26
Same problem here. Each time I reboot I have to delete the keybindings for "navigation - switch to workspace up/below), because I use them in Eclipse.

---

### Post by kenmcd on 2013-02-28
One more voice in the wilderness ... keyboard shortcuts getting reset to defaults apparently randomly after rebooting ... happening on multiple Ubuntu systems I have (32-bit and 64-bit, intel and amd, real h/w and VMs), so this seems to be a generic brain failure.

---

### Post by Wopple on 2013-03-19
Similar, perhaps same, problem here. It has for the past dozen or so reboots been every other reboot where all my System Settings -> Keyboard -> Shortcuts -> Windows keyboard shortcuts are reset. The shortcuts under the other sections are unaffected. Does anyone have a work around I can use? I'm fine with a hack that works if I only have to do it once.

---

