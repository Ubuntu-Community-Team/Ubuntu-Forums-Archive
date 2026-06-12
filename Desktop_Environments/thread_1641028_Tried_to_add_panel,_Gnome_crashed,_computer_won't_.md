---
title: "Tried to add panel, Gnome crashed, computer won't boot correctly"
date: 2010-12-08
forum: Desktop Environments
---

### Post by robofreak on 2010-12-08
Hello all,

I have a desktop computer running Linux Mint 9 with the Gnome desktop (not sure what version -- though by default Mint 9 comes with Gnome 2.30).  Last night I tried adding a panel to the desktop by right-clicking on the existing bottom panel and selecting "New Panel".  Please note that I've already got another panel at the top of the desktop on the left side on autohide and no expand.

When I added another panel, it placed a normal panel on the right side of the screen without any problems.  When I right-clicked on the new right-side panel and selected "Properties", I changed the orientation to "top" (where there was already a panel, if you remember).  After that moment, it seemed like the entire desktop environment crashed.  Everything was completely unresponsive -- the only thing moving on the screen was the mouse.  I couldn't do anything with the gui, not even shut the computer down.

Since the gui shutdown wasn't working, I switched to a different tty screen, logged in, and ran a shutdown command with the option to reboot.  The computer shut down fine, and when it woke back up, the same problem was still there:  Nothing loaded on the screen except for the background image and the mouse, which was still able to move but nothing else.  I have the computer set up to automatically log me in, so I know it's not crashing before the user prefs are being loaded...

After restarting it again and getting the same result, I switched to a different tty screen, logged in, and tried messing around with stuff to no avail.  I did notice, however, that the computer was becoming evermore sluggish, and something printed on the screen stating that a program had been terminated because of "not enough memory".  It seemed like some process was consuming WAY too much RAM by itself or a program was accidentally forkbombing the computer.

...All because I added a panel...?

All help would be appreciated -- I've put a lot of work into this thing haha

Austin B

---

### Post by wojox on 2010-12-08
Run these two commands to reset the panel

```
gconftool --recursive-unset /apps/panel
pkill gnome-panel
```

---

### Post by robofreak on 2010-12-08
Wow, thanks wojox, that worked perfectly.  Thanks for the quick reply!

Austin

---

