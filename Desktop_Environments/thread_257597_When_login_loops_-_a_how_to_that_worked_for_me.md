---
title: "When login loops - a how to that worked for me"
date: 2006-09-14
forum: Desktop Environments
---

### Post by johnbl on 2006-09-14
Had a weeks worth of pain when my system refused login for no apparent, to me, reason. Login simply looped.

Now working again after much loss of hair so here's what worked for me.

* I Did have a root password enabled. Not sure how critical this point is.I simply didn't like the idea of there being some default one.

Anyway;

Power on > Esc [ before any Ubuntu boot shows ]
Select Recovery Mode [ lots of lines as a boot runs ]
on Password request - {root password }

This gives a cursor as root@{yoursystem}

type ' startx ' > [ Enter ] - { fires up GUI - yes it is still there! }

Selected:  Places > Search for Files > Name contains [ type in *.ful ]
Look In Folders >select= { File System }

This will reveal backups which are in date name directories.

Delete oldest few
Empty Trash

Quit [ Turn off - on mine this meant a hard reboot nb hold down the power button! ]

Worked for me, hope it works for you!

John

---

### Post by mssever on 2006-09-19
Glad it worked for you. A couple of points, though:

There is no default root password, so enabling one doesn't gain anything from a security standpoint. In the default setup, with no root password, that means that it's impossible for root to log in.

You didn't actually need a hard reboot. If the GUI buttons don't work for whatever reason, typing reboot (or sudo reboot) will do the trick.

---

