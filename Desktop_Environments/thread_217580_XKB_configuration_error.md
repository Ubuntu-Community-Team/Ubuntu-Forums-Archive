---
title: "XKB configuration error"
date: 2006-07-17
forum: Desktop Environments
---

### Post by dannythomas13 on 2006-07-17
hi, i receive the following error message when i start ubuntu, it has appeared ever since i have tried to change my keyboard settig because i was unable to get the pound sterling symbol to appear.

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

i have a microsoft wireless keyboard and mouse, if anyone could help i would be very grateful
thanks
Daniel =)

---

### Post by Sharpeee on 2006-09-14
I had the same problem. I fixed it by deleting the "kbdvariant" line in the /etc/X11/xorg.conf file. In the same file I changed the "kbdlayout" to pc102.
After I restarted the xserver and logged in, I got a dialog box asking if I wanted to use Gnome preferences og xorg. I chose xorg and told it to never ask me again.

---

### Post by fbollens on 2007-01-20
Hello Daniel, I have the same error for several weeks now, I posted on several forums but dit get no answer. My solution as long ther is no proper one:
Open a terminal seesion as administrator and type the following command:
xmodmap /usr/share/xmodmap/xmodmap.XX
where XX is your country code.
mvg, fb

---

### Post by SweVoyager on 2007-03-05
> **Sharpeee said:**
> I had the same problem. I fixed it by deleting the "kbdvariant" line in the /etc/X11/xorg.conf file. In the same file I changed the "kbdlayout" to pc102.
After I restarted the xserver and logged in, I got a dialog box asking if I wanted to use Gnome preferences og xorg. I chose xorg and told it to never ask me again.

This worked for me as well. Delete the kbdvariant entry, restart the xserver and log in. I didn't get any dialog box, but the standard gnome keyboard preferences started working again after I did that. The xmodmap /usr/share/xmodmap/xmodmap.XX worked as well, but only for one session.

I have a swedish pc105 keyboard.

---

### Post by Mancman on 2007-04-09
I've had the same problem and have just cured it by changing /etc/X11/xorg.conf as follows:  change "XkbLayout" "uk" ...to... "XkbLayout" "gb".

That stopped the error message at boot-up, and I can now type a pound sign:   £   :)

---

