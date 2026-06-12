---
title: "Optiplex 960 dual-head problems"
date: 2011-07-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by AKADriver on 2011-07-26
I just installed Maverick on a Dell Optiplex 960.

During the install (presumably in VGA mode), things were working fine. Booting into ubuntu for the first time, though, the second monitor doesn't work. It's detected in the Monitors control, but the display turns off (no signal).

I previously used CentOS5 on this system and needed to endlessly tweak xorg.conf until I finally got something that sort of worked, and then failed again when I updated the kernel.

I gather that this is a "crappy nvidia drivers" problem but for some reason the "Additional Drivers" control won't open. I see a dialog box with a progress bar flash on the screen briefly then vanish.

---

### Post by AKADriver on 2011-07-26
Solved the dual-head issue myself by installing the NVidia proprietary driver from the console and disabling nouveau.

Though I still can't access the "Additional Drivers" menu. Ideas?

---

