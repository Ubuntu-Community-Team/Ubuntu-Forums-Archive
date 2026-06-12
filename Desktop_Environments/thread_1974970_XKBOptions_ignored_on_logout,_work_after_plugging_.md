---
title: "XKBOptions ignored on logout, work after plugging keyboard out/in"
date: 2012-05-06
forum: Desktop Environments
---

### Post by quantheory on 2012-05-06
In my new Precise install, anything related to layout that's determined by XKBOptions seem to be lost when I reboot or logout. (This includes change of caps lock behavior, layout-switching keys, number pad options I have related to programmer's dvorak.) The display manager doesn't give me access to these. When I log back in, the settings are still not respected until I unplug the keyboard and number pad and plug them back in (they are separate and use two USB ports, because the number pad is also a USB hub.)

Some Googling suggested that changes to /etc/default/console-setup and /etc/default/keyboard (followed by setupcon or a reboot) might help, but these had no effect. I'd like to change the settings in LightDM, but it's more important to me to not have to unplug my keyboard and plug it back in every time I log in. Not like it's that arduous to use the number keys instead of the pad for login password, but my keyboard is plugged in in an awkward spot. I just don't know what component of the desktop environment is causing this problem.

---

### Post by quantheory on 2012-05-07
An update on some of the issues here:

I also have been having trouble with changing my keyboard when this bug occurs. I can avoid *actually* un/replugging the keyboard by adding the options to /etc/default/keyboard and then doing this:

```
sudo udevadm trigger --subsystem-match=input --action=change
```

However, there are still three problems here:

-This is using a global, not a user-specific change.

-The above command has to be run every time I log out and back in.

-These things cannot be changed through the GUI (gnome) interface, except for toggling keyboards. Also, for some reason, I can turn the numberpad remapping off through the GUI, but I can't turn it back on without re-running the udevadm trigger command.

---

