---
title: "I think my HD is starting to go. . ."
date: 2006-06-25
forum: Desktop Environments
---

### Post by RavenOfOdin on 2006-06-25
Hey, I just got a few strange errors in Ubuntu after logging out of a default GNOME session to change menus back with Alacarte.  

The thing is. . .Doing so made the cursor stay on screen while the rest of the screen went black. The log out music (or rather, a shred of it) played on loop, like a broken record.  I absolutely couldn't get out of it. . .After trying all Ctrl-Alt shortcuts (F keys through BkSp and Delete) then Ctrl-Esc just for S&G, I did a hard shutdown and restarted when the drive quit spinning.

Upon start, I got the shock of my Ubuntu existence.
The console boot scroll went crazy with random errors (/sbin/udevd, illegal pid, etc.) and /dev/dazuko as well as /dev/mem seemed to vanish into nowhere.  It then stopped at "running local boot scripts" and wouldn't go any further until I shut down again.

So I went into recovery mode and Dazuko/mem/udevd were fine. No PID warnings either.  I set it to reboot with:

```

shutdown -r -F now

```

and the resulting fsck came back . . . clean.

I can now boot/use the system - and everything is listed fine but an error remains in kern.log which says "Buffer read error in /dev/hdc, logical block 6"; the same error directly after it lists 7 instead.

fsck on /dev/hdc came back with error code 2, and after a reboot with the same errors, I'm now thinking I may want to use -- this is a ST380020A -- the Seagate drive checker utility.

Should I be concerned that this is going to happen more and more in the future, as a sign of a drive going down the toilet, or just write this off as an isolated incident?

---

### Post by hippy4life on 2006-06-25
i had a drive die on me after something similar,

back up anything important now is my advice.  you can never be too carefull.

---

