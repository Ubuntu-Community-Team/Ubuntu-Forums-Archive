---
title: "Wine 0.9.22 mcop error"
date: 2006-10-02
forum: Gaming &amp; Leisure
---

### Post by mongrol on 2006-10-02
Hi folks,
Since the upgrade to wine 0.9.22 i can no longer run anything with audio enabled, including winecfg.

Open terminal, run winecfg, click on audio tab and I get this error.
```

fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
Creating link /home/mongrol/.kde/socket-smile.
can't create mcop directory

```

Winecfg then crashes. Why is trying to create a .kde/socket-smile file? I don't even have kde installed. Anyone else getting this?

---

### Post by haxer on 2006-10-02
hmmm :confused:

---

### Post by nu2this on 2006-10-02
I tried renaming the usr/lib/wine/winearts.drv.so to usr/lib/wine/winearts1.drv.so  that worked!

---

