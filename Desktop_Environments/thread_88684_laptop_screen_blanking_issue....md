---
title: "laptop screen blanking issue..."
date: 2005-11-10
forum: Desktop Environments
---

### Post by fluffy on 2005-11-10
does anyone know how i can tell x not to blank my screen every so many minutes ... i did the xset thing but it still does it ... i made sure no screensavers are enabled ... im running on a laptop if that makes any difference
thnx
:)

---

### Post by 23meg on 2005-11-10
What exactly did you do with xset? I have the same problem, but it only starts to happen after closing and reopening the lid.

---

### Post by fluffy on 2005-11-10
hi :)

i was typing my reply and my machine completely froze dead ... had to hard-reset :(
ok so i did xset -dpms and i also commented the dpms line out of the xorg.conf file

any ideas what else i should do?
thnx
:)

---

### Post by dmwit on 2005-11-10
Are you sure it's X?  That sounds like something ACPI might do.

---

### Post by 23meg on 2005-11-10
Can you verify that it won't happen if you haven't closed the lid at least once in a session? This seems to be the case for me, and I've heard the same complaint from others. Plus, I tested the Breezy development release for quite a while on this machine and I'm absolutely sure this problem didn't occur there.

---

### Post by jpkotta on 2005-11-10
[QUOTE=23meg]What exactly did you do with xset? I have the same problem, but it only starts to happen after closing and reopening the lid.[/QUOTE]
Try playing with /etc/acpi/lid.sh.  That script is run everytime you open/close the lid.  You'll want to comment out the xscreensaver line.

You can run xscreensaver-demo to configure the screensaver.  I'm not sure how to stop it from starting, but if you do a ```
xscreensaver-command -exit
``` the screensaver daemon will be exorcised.

```
xset dmps force off
``` will turn off the monitor, but it doesn't work on my laptop either.

---

### Post by 23meg on 2005-11-10
I've played around with lid.sh quite a bit but don't remember if I commented out xscreensaver; I'll try that.

Here's something weird that might further narrow down this problem: once my screen is blanked, if I hit ctrl+alt+f1 to switch to a virtual terminal (btw, virtual terminals don't work for me at all) and then ctrl+alt+f7 to go back to x, the screen comes back. fluffy, can you test this to see if this is the case for you as well?

---

### Post by fluffy on 2005-11-11
23meg ... i havnt closed the lid at all and it blanks ... i can look in the acpi stuff but im not 100% what im looking for?

once the screen blanks i just move the mouse to get display back and all seems fine (apart from the hard lockups randomly)

---

### Post by 23meg on 2005-11-15
Commenting out DPMS in xorg.conf seems to have fixed things for me; no random blackouts since doing it, thank you. Did you manage to find a solution?

---

