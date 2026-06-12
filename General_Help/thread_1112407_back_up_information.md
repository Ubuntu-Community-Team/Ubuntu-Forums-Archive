---
title: "back up information?"
date: 2009-03-31
forum: General Help
---

### Post by SanctusMessor on 2009-03-31
I am not sure how to go about this, but this would be the goal.

I want to be able to sync certain folders across my network, right now it is just windows based but I have a secondary PC that I might make into a server with Ubuntu. For example, I do 3D Modeling with Maya on my Vista based laptop (I run vista on it for gaming), I would like to sync a folder of my Maya projects so I have multiple, up to date, back ups when ever I connect to the network. Likewise if I do some work on my at home Desktop I want to sync that work with my laptop just by turning it on (and joining the network.) Syncing with the most recently modified version. Same is true for Game saves so I can carry my game progress with me. Anyone got a suggestion?

Thanks so much for the help guys! I really appreciate it :)

---

### Post by SanctusMessor on 2009-04-02
No one knows? Is there not a piece of software I can throw on Ubuntu/Kubuntu that commands it to

Start
On network recognition
Sync
DESKTOP\documents\game saves | LAPTOP\documents\game saves
DESKTOP\Maya\Projects | LAPTOP\Maya\Projects
DESKTOP\Photoshop\Projects | LAPTOP\Photoshop\Projects
End

---

### Post by ptn107 on 2009-04-02
You could write a rsync script and set it to run certain times throughout the day using crontab maybe?

#!/bin/bash
rsync -rv --delete --progress --size-only Desktop\Documents\game/ saves\ Laptop\Documents\game/ saves\
rsync -rv --delete --progress --size-only Desktop\Maya\Projects\ Laptop\Maya\Projects\
rsync -rv --delete --progress --size-only Desktop\Photoshop\Projects\ Laptop\Photoshop\Projects\
exit $?

Of course hostnames/ip's will need to be used instead.

---

### Post by amac777 on 2009-04-02
Unison can be used for directory syncing (works between windows and linux):

[https://help.ubuntu.com/community/Unison](https://help.ubuntu.com/community/Unison)

---

