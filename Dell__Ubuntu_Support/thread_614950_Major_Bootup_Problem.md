---
title: "Major Bootup Problem"
date: 2007-11-16
forum: Dell  Ubuntu Support
---

### Post by iflanery on 2007-11-16
For some reason, Kubuntu 7.04 has decided not to take me to the login screen when booting up. I get the Kubuntu status bar (to indicate that it's loading), then I get an empty status bar (as if it's preparing to shut down), then I just get a blank screen with a text cursor. I type "start x" or "startx", but it does nothing.

I'm running a Dell Inspiron 530N, with Kubuntu Feisty, but at this time I'm about to say "screw it" and go with Debian.

---

### Post by Martin Witte on 2007-11-16
has it been working? if not it might be the video driver, vesa is a safe choice

---

### Post by iflanery on 2007-11-16
It was working perfectly yesterday.

---

### Post by tinycamp on 2007-11-16
could you post the output of dmesg ?, does it work ?

---

### Post by iflanery on 2007-11-16
That's the thing; there was NO dmesg.

---

### Post by saru411 on 2007-11-17
i've run into this type of issue before....i believe your hdd is checking itself. fsck does a scan of your files every 25 or so reboots. when it does this the screen turns black and seems not to respond. i would recommend rebooting into safe graphics mode and seeing if it does a fsck check. if it does, let it go through the check and then restart the laptop.

hope this works for ya =)

---

### Post by iflanery on 2007-11-17
It wasn't doing an fsck HDD check; it just got me to a blank screen, kind of a command prompt without an actual prompt.

---

### Post by saru411 on 2007-11-18
im describing the same thing. it would run through the bios hardware check...load kernel...and then go to a blank screen. it seems to just be hanging so i rebooted in safe graphics mode and it started a fsck on my hdd. have you even tried my suggestion?

---

