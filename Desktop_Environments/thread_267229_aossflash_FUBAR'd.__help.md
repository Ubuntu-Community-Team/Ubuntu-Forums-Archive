---
title: "aoss/flash FUBAR'd.  help"
date: 2006-09-28
forum: Desktop Environments
---

### Post by jdunn on 2006-09-28
This problem started after I installed a new sound card (SB Live 24-bit) to replace my on-board sound.  Flash has no sound on Firefox and when I try to exit Firefox or switch to a new url, Firefox hangs. (Yes, I have ALSA-OSS installed and firefoxrc has FIREFOX_DSP="aoss").  It seems as though anything I run with aoss hangs and has no sound (ex:  teamspeak, games).  I even reinstalled ALSA-OSS and Flashplugin-free from the repostories.  Otherwise, arts works fine, sound in games is fine, amarok, kaffeine, etc.

BTW, I had to run alsamixer to boost capture feedback for my microphone.  Did that do something to my ALSA settings to screw up aoss?

So, what's the problem?  help.

---

### Post by jdunn on 2006-09-28
bump

---

### Post by ZipoTe on 2006-09-28
Yeeeah, i have the same problem :( i solved it running firefox by this way

"aoss firefox"

sometimes it crashes but is the only way i can get sound ](*,)

---

### Post by jdunn on 2006-09-28
> **ZipoTe said:**
> Yeeeah, i have the same problem :( i solved it running firefox by this way

"aoss firefox"

sometimes it crashes but is the only way i can get sound ](*,)

That doesn't work for me.  It behaves as if I had FIREFOX_DSP="aoss" in firefoxrc.  For now, I'm using FIREFOX_DSP="none".  There's sound in flash but its very choppy.  Flash works well enough in Konqueror so I think the problem is between aoss and my new sound card.

---

### Post by hernyman on 2006-10-18
I have the same exact problem as you (SB Live 24-bit and no sound with aoss). Time to fill a bug-report ;)

---

### Post by jdunn on 2006-10-28
> **hernyman said:**
> I have the same exact problem as you (SB Live 24-bit and no sound with aoss). Time to fill a bug-report ;)

SB Live 24-bit does not have hardware mixing.  I returned the SB Live 24-bit where I bought it because I found an old SB Live Value I had stored away a few years ago.  It works perfectly.

---

