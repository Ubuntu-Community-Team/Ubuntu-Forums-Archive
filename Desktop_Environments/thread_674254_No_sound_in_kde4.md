---
title: "No sound in kde4"
date: 2008-01-21
forum: Desktop Environments
---

### Post by benerivo on 2008-01-21
I'm trying kde4, but have been unable to get any sound working at all. I have never had any problem getting sound in gnome or any other desktop environment, so i don't think it's the soundcard that's the problem. I have gome through the system settings and kmix, trying different options but nothing has worked. Is there anything else i could try, or that i have missed?

---

### Post by PurposeOfReason on 2008-01-21
Do you have sound if you go into a different DE?

---

### Post by benerivo on 2008-01-21
Yes. I can log out and go in to any application, in any other desktop environment and have no problem playing music files, music streams, videos, etc..

---

### Post by Deathknell on 2008-01-24
I'm having the same problem.  All sound works in KDE 3.5.

---

### Post by OldGaf on 2008-01-29
Same here, I have sound on the other OS's on this machine (Debian and XP), but nothing in KDE4. Sound card is detected properly and Amarok does not complain...... just no sound. 

Now in KDE3 I had the same problem but was able to fix it:

"Theres two tabs, Playback and Switches. Goto switches. Uncheck "Audigy Analog/Digital Output Jack". Booya! It worked for me, I hope it does for you!"

But I see that kmix in KDE4 has no Switchs tab..........

---

### Post by OldGaf on 2008-01-29
uninstalled kmix-kde4 and installed kmix. Then the following is possable.

Theres two tabs, Playback and Switches. Goto switches. Uncheck "Audigy Analog/Digital Output Jack.

Now I have sound. Not sure what I am missing from the KDE4 version, but at least I can use my Amarok while playing with the other KDE4 "stuff"

---

### Post by mkb137 on 2008-02-24
I had the same problem and it turned out that KDE 4's KMix had everything muted and at 0  volume by default.  Starting up KDE 4's KMix, unmuting the channels and raising the volume fixed it.

---

