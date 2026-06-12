---
title: "Music won't play"
date: 2005-09-04
forum: Desktop Environments
---

### Post by Curlydave on 2005-09-04
Music used to play for me in Ubuntu, but now it won't. It works in ESD mode, but not alsa and oss, and when I try to test them it says they won't build. Arg.

---

### Post by mcmuffy on 2005-09-04
What has changed in your system since music last played? Have you added or changed any major software or hardware?

---

### Post by Curlydave on 2005-09-05
[QUOTE=mcmuffy]What has changed in your system since music last played? Have you added or changed any major software or hardware?[/QUOTE]

Nothing's changed.

---

### Post by rdwtux on 2005-09-05
try killing ESD and then playing again in the play of your choice. 

oss/alsa can't get exclusive lock on /dev/dsp if esd has it. 

just a thought.

---

