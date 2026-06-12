---
title: "Xsession starting error - 8.04"
date: 2008-05-01
forum: Desktop Environments
---

### Post by rslrdx on 2008-05-01
I started to see this error on my box, i dont know what caused it as i did lots of updates on my box (just apt-get update && upgrade, no settings tweaking) 

anyone else seeing this problem?


Thanks,
Rodrigo.


PS: tried to post the message here, but the forum system kept telling me that i had over 15 images in the code! (?????) So the complete error is in the attachment



/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found
Setting IM through im-switch for locale=pt_BR.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/Alpha:/tmp/.ICE-unix/10437
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Warning:          Duplicate shape name "RTRN"
                  Using last definition
Warning:          Duplicate shape name "RTSH"
                  Using last definition
Warning:          Don't know how to merge sections yet
Warning:          Don't know how to merge sections yet
Warning:          Don't know how to merge sections yet
Warning:          Don't know how to merge sections yet
expected keysym, got XF86KbdLightOnOff: line 70 of pc
last scanned symbol is: XF86KbdLightOnOff
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
last scanned symbol is: XF86KbdBrightnessDown
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
last scanned symbol is: XF86KbdBrightnessUp
Warning:          Type "PC_RALT_LEVEL2" has 2 levels, but <LALT> has 3 symbols
                  Ignoring extra symbols

---

### Post by rslrdx on 2008-05-04
Solved, found the solution here

[http://ubuntuforums.org/showpost.php?p=3476789&postcount=2](http://ubuntuforums.org/showpost.php?p=3476789&postcount=2)

---

