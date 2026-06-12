---
title: "volume control missing from the notification area"
date: 2013-04-16
forum: Desktop Environments
---

### Post by coastwatcher on 2013-04-16
In Xubuntu 12.04, the volume control has disappeared from my top panel.  I uninstalled and reinstalled PulseAudio Volume Control, with no change.  I
also removed and re-added the Notification Area item in panel 1 (the upper panel), also with no change.

I can still control audio volume with Menu -> Multimedia -> PulseAudio Volume Control, or with the keyboard fn keys for volume-up, volume-down and mute, and a notification appears near the upper right of the screen when I do so, so I can get by.  However, I'd like the widget back in the upper panel if possible.

The notification area is definitely present: for example, I can see whether my wifi is up, whether there are updates waiting to be installed, etc.

Any suggestions?  Thank you.

--coastwatcher

---

### Post by Frogs Hair on 2013-04-16
If you right click the panel and drop-down to panel > + new items you can select audio mixer/ volume and add it . To move it right click and select move.

Note: I am using XFCE not Xubuntu so there may be differences .

---

### Post by coastwatcher on 2013-04-17
Thanks for the reply.

Unfortunately, that's not among the choices when I try to add a new item to the panel.  Since the available plugins are listed in collating sequence (except for Launch, which comes first), I can see that the only A's are "Action Buttons" and "Applications Menu", the only M is "Mail Watcher", and the only V is "Verve Command Line".  (This the same for the Xubuntu or the XFCE session, BTW.  I tried it both ways.)

As the King says in The King and I, "Is a puzzlement."

---

### Post by lightning slinger on 2013-04-17
The volume control is part of the 'Indicator Plugin' not the 'Notification Area'.

---

### Post by coastwatcher on 2013-04-21
That did the trick.  The network indicator and such were present, but adding the "indicator plugin" brought back the volume control without removing the other ones that were already there.  Thank you very much for the reply.

--Coastwatcher

---

