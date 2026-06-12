---
title: "[SOLVED] Have media auto exec a script when mounted?"
date: 2008-12-21
forum: General Help
---

### Post by jerome1232 on 2008-12-21
This idea just sprung on me yesterday, you know how when you insert cd's they have this auto run feature.

> This medium contains software intended to be automatically started. Would you like to run it?

The software will run directly from the medium "X1APFPP_EN". You should never run software that you don't trust.

If in doubt, press Cancel.

Well I use rsync to backup ~/ and /opt to my external hard drive, is it possible for me to put some scripts on the backup drive that automatically run my backups when the backup drive get's mounted?

---

### Post by jerome1232 on 2008-12-21
I actually got this figured out now :)

In case anyone is interested you just create an (believe it or not) autorun script (I used autorun.sh, supposedly can be .autorun or autorun, it failed for me as .autorun.sh and I didn't feel like experimenting with the other names.)

This is the contents of my script; 

---edited---- Ended up changing my script to open a gnome terminal and execute the commands in it so I have a visual cue as to what's going on.
```
#!/bin/bash
# an autorun backup script
gnome-terminal -x rsync -avh --delete --exclude=.gvfs ~/ /media/Backup/Jeremy; rsync -avh --delete /opt /media/Backup

```

---

