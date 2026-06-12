---
title: "Can't get AWESOME to work anymore!"
date: 2014-04-17
forum: Desktop Environments
---

### Post by sniffysniper on 2014-04-17
I used awesome and was liking it

Then i screwed up some config files, so I removed awesome and reinstalled it.

Now when I load up an awesome session it gives an error, how do I resolve this :O?

The error in tty is ending with Connection to the X server has los.


this is in my xorg log

[  1044.200] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1073.124] (II) Open ACPI successful (/var/run/acpid.socket)
[  1073.124] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1073.124] (II) intel(0): switch to mode 1280x800@60.2 on pipe 0 using LVDS1, position (0, 0), rotation normal
[  1073.140] (II) intel(0): EDID vendor "APP", prod id 40135
[  1073.140] (II) intel(0): Printing DDC gathered Modelines:
[  1073.140] (II) intel(0): Modeline "1280x800"x0.0   72.50  1280 1328 1360 1423  800 803 809 846 -hsync -vsync (50.9 kHz eP)
[  1073.158] (--) synaptics: bcm5974: touchpad found
[  1073.340] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[  1073.357] (II) XKB: reuse xkmfile /var/lib/xkb/server-F3B3D0528E01F59A3E408E2FE9E155615221B085.xkm
[  1073.366] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[  1073.373] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[  1073.383] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[  1073.391] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[  1073.408] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[  1073.411] (II) XKB: reuse xkmfile /var/lib/xkb/server-F3B3D0528E01F59A3E408E2FE9E155615221B085.xkm
[  1073.417] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[  1073.445] (II) XKB: reuse xkmfile /var/lib/xkb/server-F3B3D0528E01F59A3E408E2FE9E155615221B085.xkm
[  1073.472] (II) XKB: reuse xkmfile /var/lib/xkb/server-F3B3D0528E01F59A3E408E2FE9E155615221B085.xkm
[  1073.499] (II) XKB: reuse xkmfile /var/lib/xkb/server-F3B3D0528E01F59A3E408E2FE9E155615221B085.xkm
[  1073.527] (II) XKB: reuse xkmfile /var/lib/xkb/server-F3B3D0528E01F59A3E408E2FE9E155615221B085.xkm
[  1073.561] (II) XKB: reuse xkmfile /var/lib/xkb/server-F3B3D0528E01F59A3E408E2FE9E155615221B085.xkm
[  1073.595] (II) XKB: reuse xkmfile /var/lib/xkb/server-F3B3D0528E01F59A3E408E2FE9E155615221B085.xkm

---

### Post by Frogs Hair on 2014-04-17
If Awesome has a configuration folder in home hidden folders then removing it and reinstalling will create a new configuration, but you will have to set it up from scratch again. Some window managers have such a folder but not all and it may be inside of the .config folder.

---

