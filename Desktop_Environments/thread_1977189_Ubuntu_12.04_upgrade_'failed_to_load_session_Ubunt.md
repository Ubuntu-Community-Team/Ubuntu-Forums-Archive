---
title: "Ubuntu 12.04 upgrade 'failed to load session Ubuntu'"
date: 2012-05-09
forum: Desktop Environments
---

### Post by MatNewman on 2012-05-09
Upgraded Ubuntu x32 10.10 to 12.04

Unity originally working ok, compiz effects hacks applied to get rotate cube, wobbly windows, etc running.

Installed Kubuntu and Lubuntu, switched between desktop environments OK, ran up and configured GDM, KDE and LightDM fine.

Switched back to LightDM and attempt to log in using "Ubuntu" (this *WAS* the Unity option) receiving error 'Failed to load session "Ubuntu"'.  Forced to log out.  Now this happens when attempting to access 'Ubuntu' for all three desktop environments log-in screens.

Can still use Gnome, Gnome Classic, KDE Plasma and Lubuntu desktop environments ok.

Gnome has also now lost all Compiz effects originally applied.

Running 'compiz --replace' sort of works, but generates a large number of errors in the terminal including:

"Fatal:No valid GL extension string found"

NVidia drivers installed and activated, running fine, and able to use nvidia-settings to successfully manage multiple monitors, projectors, etc.

NVidia driver 295.40

Linux kernel 12.04 LTS, 3.2.0-24-generic

Also getting 'BadWindow (invalid window parameter)'  and '(Details: serial 305 error_code 3 request_code 137 minor_code 4)'  when attempting to access the nvidia-settings "OpenGL/GLX" tab, which results in nvidia-settings panel crashing.

Speculating there is something wrong with the driver since the upgrade, which is why Unity won't load.

Posting here to see if anyone else has the same issue, have seen numerous posts referencing the same error on the interweb, but no concrete resolution yet for 'failed to load session "Ubuntu"'.

---

### Post by MatNewman on 2012-05-10
Solved my problem.

Opened Synaptics while logged into Gnome, removed the installed NVidia drivers, rebooted, back into Gnome session, Loaded jockey-gtk, it suggested the current NVidia driver, downloaded and installed, rebooted, all working fine now, including Compiz effects in Unity.

---

