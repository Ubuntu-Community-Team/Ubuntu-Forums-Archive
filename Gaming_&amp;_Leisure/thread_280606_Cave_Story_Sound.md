---
title: "Cave Story Sound?"
date: 2006-10-19
forum: Gaming &amp; Leisure
---

### Post by Seantiago on 2006-10-19
Are you guys familiar with Cave Story?

[http://agtp.romhack.net/doukutsu.html](http://agtp.romhack.net/doukutsu.html)

It's a free-as-in-beer platformer that kicks ***.  There's no native Linux version that I know of, but it works pretty well under wine...with one problem: sound doesn't work at all.  Everything else is fine, but I can't get a peep out of it: no music/sfx/nada.  Soundwise, I have no other problems on my system.

Any suggestions?

---

### Post by encompass on 2006-10-20
have you run winecfg?
Additionally, you coude disable esd sound...(turn off the sounds in gnome) and see if that helps.  Lastly, for the heck of it, you can try..> aoss wine blabla

---

### Post by Seantiago on 2006-10-20
Yeah, winecfg did the trick.  I just had to run it and switch the sound driver to alsa.  Thanks.

---

### Post by el mariachi on 2007-03-27
I had the same issue and using Hardware emulation worked (ALSA didn't)

---

### Post by BigBananaMan on 2010-01-22
There is finally a [native version]("http://www.miraigamer.net/cavestory/downloads_1.php") though it's poorly ported and tends to have sound/freezing issues with me.

---

