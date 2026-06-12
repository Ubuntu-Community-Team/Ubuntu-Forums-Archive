---
title: "Can only play one sound source at the time..."
date: 2006-01-17
forum: General Help
---

### Post by WhizCas on 2006-01-17
Hi All :),

I have a on-board soundcard and I'm using Alsa. The problem is I can only play one sound source at the time. Like when I have Skype on I can't listen to music from XMMS. It says the soundcard is busy... Anyone an idea howto fix this?

Tnx for ur reactions...

---

### Post by mishranurag on 2006-01-17
Skype is a crappy program and will keep on doing like that, until skype people themsleves go ahead and fix the bug in their linux version. There is a hack available somewhere in the forum that can fix the problem of skype with redialing and that's about it.
Anurag

[quote=WhizCas]Hi All :),

I have a on-board soundcard and I'm using Alsa. The problem is I can only play one sound source at the time. Like when I have Skype on I can't listen to music from XMMS. It says the soundcard is busy... Anyone an idea howto fix this?

Tnx for ur reactions...[/quote]

---

### Post by WhizCas on 2006-01-19
Well it was an example, the point of my thread is not that I can't Skype ;).

I can't play two sound programms at once, only one will play!

---

### Post by LordBug on 2006-01-19
If you're having a problem with any combination of sound programs, I'd suggest re-configuring things to use a sound server (like ESD).  ALSA tries to use the card's hardware mixer if I remember right and it sounds like yours doesn't have said mixer.

---

### Post by WhizCas on 2006-01-19
[quote=LordBug]If you're having a problem with any combination of sound programs, I'd suggest re-configuring things to use a sound server (like ESD).  ALSA tries to use the card's hardware mixer if I remember right and it sounds like yours doesn't have said mixer.[/quote]

And how do I do that? (n00b I know)

---

