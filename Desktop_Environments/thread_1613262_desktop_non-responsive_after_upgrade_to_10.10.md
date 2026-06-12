---
title: "desktop non-responsive after upgrade to 10.10"
date: 2010-11-04
forum: Desktop Environments
---

### Post by Tehut on 2010-11-04
Hi,

I updated my Kubuntu 64-bit 10.04 to 10.10 yesterday.
Since then, the desktop and taskbar have been unresponsive most of the time. Specifically, moving the mouse works, and so does clicking in programs that automatically open after logging in (ktorrent, for example). Switching through programs with alt+tab does not work and so does clicking on anything in the taskbar/systray or on the desktop (meaning I can't open any new programs or even logout without alt+strg+backspace). There's a flickering off-white bar in the space between the taskbar and the edge of the screen, about 4/3 the height of the taskbar.
Also, only the black&white icons show in the systray (like klipper) and some of them are missing (I noticed the one for sound is missing), but not, for example, ktorrent's icon.
After rebooting often, it sometimes worked, mostly using the old .32-25 kernel. In those cases, there was a rectangular edge on the background image; when it didn't work, that edge was missing (as it should).
When it did work, the problem reappeared after a few hours. Also, viewing anything in fullscreen (images for example) produced a flickering of the whole screen (same white color as that bar on the side of the taskbar I mentioned earlier). That flickering got worse after a while and eventually, I ended up with the same unresponsiveness.
The last ~10 reboots didn't get it to work anymore.
I tried aptitude update&&safe-upgrade and dpkg repair in recovery mode, both didn't produce any results or errors.

Any ideas how to fix this / what might have caused this?
If so: Thank you very much.

---

### Post by Tehut on 2010-11-04
Screenshot of the taskbar with Firefox and Ksnapshot opened:
[img]http://sadpanda.us/images/267784-WPZZKD5.jpg[/img]

Opening Ksnapshot via print-key and then opening Firefox via 'open with' works.
System gets nearly completely unresponsive very quickly if I do that. Ctr+alt+backspace still works, though.

---

### Post by Tehut on 2010-11-05
bump

---

### Post by Tehut on 2010-11-05
Tried killing the plasma-desktop process and then restarting it via konsole. Afterwards, the currently running programs were correctly shown, but desktop was still completely unresponsive.
After that, logging out and in again resulted in a normally working desktop except for that flickering bar.
Then tried removing the i-hate-the-cashew plasmoid. After restarting, the problem appears to be gone - no flickering bar and the desktop works normally again. No idea what exactly fixed it, but at least it does seem to be fixed.

---

