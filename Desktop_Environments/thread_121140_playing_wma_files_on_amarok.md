---
title: "playing wma files on amarok"
date: 2006-01-24
forum: Desktop Environments
---

### Post by krait on 2006-01-24
as the subject suggests, is there anyway of accomplishin this.

cheers

---

### Post by endersshadow on 2006-01-24
Do you have w32codecs installed?

---

### Post by krait on 2006-01-25
ya i do hav w32 codecs installed, checked n synaptic. the strange thing is im able to view wmv files, but wma files dont play on any player, not only amarok.

cheers

---

### Post by RAOF on 2006-01-25
[QUOTE=krait]ya i do hav w32 codecs installed, checked n synaptic. the strange thing is im able to view wmv files, but wma files dont play on any player, not only amarok.

cheers[/QUOTE]
Are they protected (DRM'd) in any way?  Do you have gstreamer-plugins-multiverse installed - that should include gstreamer-pitfdll, which can use the win32 binary codecs.

---

