---
title: "Counter-Strike 1.6 Choppy after Feisty Upgrade"
date: 2007-04-25
forum: Gaming &amp; Leisure
---

### Post by Spatulas on 2007-04-25
Hello there,

The title pretty much says it all.  I had wine installed in Edgy (0.9.33), and wine'd CS 1.6 was running smoothly.  However, when I upgraded to Feisty, the entire game started to become really choppy (sound and video).  For lack of anything to try (had latest version from the ubuntu repo, and had tried reinstalling) I compiled the latest from the official wine repo (0.9.35) and tried that.  While it didn't fix the problem, it did make it much better relative to before.

It seems to be sound related (more sounds seem to slow it down more), so I've tried changing the sound engine from OSS to ALSA, but it seems that CS will not run with anything other than OSS running.  Any help would be greatly appreciated.

---

### Post by buttons on 2007-04-25
Are you having [this issue]("http://ubuntuforums.org/showthread.php?p=2536488")?

---

### Post by Spatulas on 2007-04-25
No, it's not freezing, only being choppy.

Thanks for the reply.

---

### Post by 007Bond on 2007-04-25
Did you reinstall the proper driver for your videocard for Feisty?

---

### Post by Spatulas on 2007-04-25
Yeppers.

---

### Post by buttons on 2007-04-26
> **Spatulas said:**
> Yeppers.

Terminal output?  Without WINEDEBUG.

---

### Post by Spatulas on 2007-04-26
[http://pastebin.ca/458530](http://pastebin.ca/458530)
That's at startup.
Thanks for the reply.

---

### Post by buttons on 2007-04-26
Try downgrading libspeex1 to 1.1.12-3 and downgrading wine to 0.9.32.  The deb is available [here]("http://wine.budgetdedicated.com/archive/index.html").

---

### Post by Spatulas on 2007-04-26
> **buttons said:**
> Try downgrading libspeex1 to 1.1.12-3 and downgrading wine to 0.9.32.  The deb is available [here]("http://wine.budgetdedicated.com/archive/index.html").

You mean the version for Edgy?

---

### Post by buttons on 2007-04-26
> **Spatulas said:**
> You mean the version for Edgy?

The speex version 1.1.12-3 is feisty, actually.  Edgy is 1.1.12-2.  I had choppiness as well as nb_ctl errors like you're getting, and it turned out (maybe) to be the libspeex1 package that came with a certain repo I had picked up online for things like ekiga.

---

### Post by Spatulas on 2007-04-26
> **buttons said:**
> The speex version 1.1.12-3 is feisty, actually.  Edgy is 1.1.12-2.  I had choppiness as well as nb_ctl errors like you're getting, and it turned out (maybe) to be the libspeex1 package that came with a certain repo I had picked up online for things like ekiga.

Hm, I don't think it's that then.  Aside from wine I only have the default repos enabled, so I shouldn't have picked up a bad version of speex.  Should I try anyways?

---

### Post by buttons on 2007-04-26
> **Spatulas said:**
> Hm, I don't think it's that then.  Aside from wine I only have the default repos enabled, so I shouldn't have picked up a bad version of speex.  Should I try anyways?

Couldn't hurt.  Try downgrading (wine) as well.

Worked for me, YMMV, unfortunately.

---

