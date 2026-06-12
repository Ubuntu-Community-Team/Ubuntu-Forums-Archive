---
title: "[SOLVED] changed sound in wine, now i have no sound AT ALL"
date: 2008-12-08
forum: General Help
---

### Post by rudeboyskunk on 2008-12-08
So, sound in WoW was being really choppy, so I went into wineconfig and changed the sound from ALSA to OSS (in this installation this was the first time I'd even gone into the sound settings).  This made it to where there was no sound in WoW (even after restarting), and no sound in Ubuntu at all!  So, I changed it back to ALSA, and still no sound in WoW or Ubuntu at all!

What do I do???

---

### Post by kostkon on 2008-12-08
> **rudeboyskunk said:**
> So, sound in WoW was being really choppy, so I went into wineconfig and changed the sound from ALSA to OSS (in this installation this was the first time I'd even gone into the sound settings).  This made it to where there was no sound in WoW (even after restarting), and no sound in Ubuntu at all!  So, I changed it back to ALSA, and still no sound in WoW or Ubuntu at all!

What do I do???
Check your volume levels. The same happened to me when trying to use OSS with padsp instead of ALSA in Wine. In my case, the PCM volume changed to 0 for some reason...

---

### Post by rudeboyskunk on 2008-12-10
Kostkon,

This is actually exactly what happened.  Glad I wasn't the only one.

---

