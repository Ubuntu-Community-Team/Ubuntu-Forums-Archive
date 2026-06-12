---
title: "Mixed-mode CDs"
date: 2006-01-02
forum: Desktop Environments
---

### Post by Zalbor on 2006-01-02
Normally when I put one in, it would ask me if I want to mount it or just play the audio tracks. Being stupid, at some point I set it on playing the audio without asking, and now if I want to access the data I need to mount it through a terminal.
I can't find the option to set it back to asking, and I don't know how to do it through a terminal. Could someone direct me?
Thank you.

---

### Post by ysse on 2006-01-02
Disclamer: I can't verify this, because I can't find any mixed-mode CD.

Try Applications/System Tools/Configuration Editor, navigate to /desktop/gnome/volume_manager/prompts and set the value for "cdrom_mixed" to 0.

/Anders

---

### Post by Zalbor on 2006-01-02
Yes, that was it. Thank you!

---

