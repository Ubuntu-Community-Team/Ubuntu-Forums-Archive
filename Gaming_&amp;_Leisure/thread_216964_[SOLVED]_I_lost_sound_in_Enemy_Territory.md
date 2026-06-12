---
title: "[SOLVED] I lost sound in Enemy Territory"
date: 2006-07-16
forum: Gaming &amp; Leisure
---

### Post by Xzallion on 2006-07-16
Yesterday I installed Castle Wolfenstein: Enemy Territory and True Combat: Elite, had both working, and had sound.  Now today I no longer have sound when I try to play either one.  I tried a quick search on the ubuntu forums, but only found one thread about sound in enemy territory, and it didn't help.

I tried a suggestion in that thread about using the code ```
sudo et
``` to run it, but that didn't fix it either.  When I ran that from the terminal, I found this in the terminal ```
------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------
```

I don't know why my sound is busy, I don't have any music or anything playing.  But I can open amarok and play music, so I do have sound working on my machine.

Any help or advice would be appreciated.

I'm still pretty new to ubuntu so I could just be missing something simple.

Edit:  I still don't know what the problem is, but I have sound in other games like Tremulous.  this is really confusing me.

---

### Post by B0rsuk on 2006-07-16
Do you use OSS or ALSA ? 
If you use alsa (better overall), try ```
killall artsd;et
```


The 'device is busy' problem sounds like you're using OSS. Try switching to ALSA, you do it in KDE Control Center, assuming you use KDE, of course.

by the way: **Running apps as root is bad idea from security point of view.** Don't do it.

---

### Post by ELD on 2006-07-16
I actually don't get any sound at all from ET, anyone know how i can get it on?

---

### Post by Xzallion on 2006-07-16
> **B0rsuk said:**
> Do you use OSS or ALSA ? 
If you use alsa (better overall), try ```
killall artsd;et
```


The 'device is busy' problem sounds like you're using OSS. Try switching to ALSA, you do it in KDE Control Center, assuming you use KDE, of course.

by the way: **Running apps as root is bad idea from security point of view.** Don't do it.

I tried that and still had no sound.  I think im using OSS, but I can't figure out how to change that to ALSA in Gnome.

---

### Post by Xzallion on 2006-07-16
Nevermind, I rebooted and for some reason sound now works in both enemy territory and true combat elite.  thanks for the suggestions.

---

