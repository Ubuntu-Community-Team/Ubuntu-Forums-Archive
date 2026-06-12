---
title: "xmms problem"
date: 2006-03-19
forum: Desktop Environments
---

### Post by Tomlin on 2006-03-19
If I start xmms from the menu bar (Applications/Sound and Video/XMMS), while logged in as a normal user, and there is a file already loaded from the previous time I played it, and I doubleclick the file OR click the "play" icon, I receive this "couldn't open audio" pop-up window:

[IMG]http://phase1.com/images/audio.png[/IMG]

If I click OK, and try again, everything is fine and the song plays normally.

However, if I start xmms from a terminal window, everything works fine and I don't get the error. Annoying to say the least. AmoroK works fine from the Applications menu as does Rhythmbox.

Any ideas?

---

### Post by navilon on 2006-03-19
Do youo get the same message if you use Beep Media Player?

---

### Post by Tomlin on 2006-03-19
Yup.

[IMG]http://phase1.com/images/beep.png[/IMG]

---

### Post by Super King on 2006-03-19
Not sure how much this helps but I had the same issue with my Thinkpad laptop (same error message in XMMS, would play fine after clicking OK, no problems in Rhythmbox). The issue would (and still does) occur when my volume was at 0%. When I raised it above that I would not encounter the problems. Again, this may not relate to your situation at all.

---

### Post by Tomlin on 2006-03-19
Well, changing the output plugin from:

OSS Driver 1.2.10

to:

ALSA 1.2.10 output plugin

worked.

Thanks for your reponses.

Tomlin

---

