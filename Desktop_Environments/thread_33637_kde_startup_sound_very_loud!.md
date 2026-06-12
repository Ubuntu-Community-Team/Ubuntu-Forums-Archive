---
title: "kde startup sound very loud!"
date: 2005-05-11
forum: Desktop Environments
---

### Post by tardis_junkie on 2005-05-11
Hi,

When kde starts the startup sound starts at a normal volume then goes very lod and distorts, once kde has loaded the souns are at there normal volume.

Any help it keeps making me jump.

---

### Post by Kurse on 2005-05-11
Just guessing here, but it sounds like the sound lowers to the proper level once the Kmix takes over. Perhaps adjusting the volume lower with alsamixer, or another command line mixer app will fix this for you.

---

### Post by Xian on 2005-05-11
Try this procedure:

Open the KDE Control Center and goto Sound & Multimedia > System Notifications.

Then click on 'Player Settings'.
Tick the box 'Use an External Player'.

Paste this into the dialogue box where is says 'Player': /usr/bin/artsplay
Click okay.

Now login again. Any change?

---

