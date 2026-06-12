---
title: "Lost 5.1 Sound in Some Applications"
date: 2009-07-09
forum: Desktop Environments
---

### Post by izizzle on 2009-07-09
I'm running Kubuntu 9.04 64-Bit. Urban terror was running perfectly fine until recently when 5.1 sound stopped working in the game. 

EDIT: Ok, this is a bit weird. I just noticed that 5.1 doesn't work in VLC or Firefox (flash video) either, but is DOES work in Amarok. I am using ALSA if that helps. Any ideas?

Thanks.

---

### Post by izizzle on 2009-07-10
Bump!

---

### Post by izizzle on 2009-07-10
Bump. Still only have sound coming out of two speakers in Urban Terror, VLC, AND Firefox 3.5.

---

### Post by izizzle on 2009-07-10
I ran ```
speaker-test -Dplug:surround51 -c6 -l1 -twav
``` and I am getting sound from all my speakers, so the issue must be software related (?). Please help!

---

### Post by izizzle on 2009-07-10
Fixed. Went to the multimedia section in System settings and selected PulseAudio as default for all the sections listed.

---

### Post by izizzle on 2009-07-10
EDIT: I didn't fix it. It was working, but then I rebooted and the problem is back. Please Help!!

---

