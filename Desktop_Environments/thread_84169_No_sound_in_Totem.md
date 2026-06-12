---
title: "No sound in Totem"
date: 2005-10-30
forum: Desktop Environments
---

### Post by tit4tat on 2005-10-30
I'm trying to play .mp4 files but there isn't any sound. Sound card is fine because I can hear the splash sound and menu clicks.

Any idea what the problem is?

---

### Post by bryan986 on 2005-10-30
try totem-xine instead of totem-gstreamer

---

### Post by GTvulse on 2005-10-30
Did you install gstreamer0.8-faad? That would be located in the multiverse repositories, if I recall correctly.

---

### Post by tit4tat on 2005-10-30
Actually I had xine already so I switched to gstreamer and it works fine. Thanks for the prompt reply.

---

### Post by GTvulse on 2005-10-30
For the record, you can have totem-xine reproduce mp4 files, but you need the proper codecs (as in w32codecs) installed in your system... :smile:

---

