---
title: "Keyboard volume keys not working after working for years."
date: 2021-01-06
forum: Desktop Environments
---

### Post by dkolars on 2021-01-06
Weird problem just happened...  Ubuntu 18.04, been using Ub since 9.x...  Today I attempted to do a Google Duo call, and the person could not hear me... so, I opened the PulseAudio Vol Control to check things, and never did get it to work.  But, after that, the keyboard volume control keys quit working!  The pop-up box appears, and shows that I'm muted, raising or lowering volume, etc, just as always, but it has NO effect on the sound output.  And, then the audio quit completely, even tho' the bars in the PA Control showed changes in volume.  So, checked, and yes, the batteries in the keyboard are still good!!

Internet, ho!!  Found lots of posts about this, attempted some "fixes", nope.  Uninstalled ALSA and PulseAudio, reinstalled, and now I have sound from the speakers again, and the keyboard volume control keys appear to work, according to the pop-up box, but still have NO effect on the system volume.

I've never liked the way Linux handles audio, and now like it even less!!  Grrr... Any ideas about what could be causing this?  I see nowhere to adjust the keyboard settings for this, and no reference to the keyboard in any sound-related files or settings.  TIA  DK

---

### Post by ActionParsnip on 2021-01-07
Does the keyboard have a make and model?
Does the system have a make and model?

---

### Post by CelticWarrior on 2021-01-07
> **ActionParsnip said:**
> Does the keyboard have a make and model?
Does the system have a make and model?

+1
Please always provide hardware specifications when asking questions about hardware.

That said, I think the hardware isn't to blame here. What probably happened was the software you were using changed or didn't pick the audio device set system wide. When such glitches happen the multimedia keys are kept tied to an audio output that isn't actually being used at the moment but more often than not toggling the audio output in system settings get it back on track.

Now, what you did likely made things worse, in a peculiar insane way.

---

### Post by dkolars on 2021-01-07
OK, keyboard is Logitech K270, using it for about 3 yrs now.  System is one I built about 5 yrs ago.  

Update - SOLVED...

Found the culprit, but why it became the culprit, I have no clue...  a FIFINE USB Podcast Microphone! Not had a problem with it before, but when I unplugged it, the keyboard keys work again.  Plugging it back in disables the keyboard keys. Is plug and play, so no settings to adjust on it.  I attempted to use it during the Duo call, but have used it on Zoom calls with no effects in the past.

Thanks.

---

