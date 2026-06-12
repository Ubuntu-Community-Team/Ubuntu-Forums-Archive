---
title: "Sound issue"
date: 2006-07-14
forum: Desktop Environments
---

### Post by IndigoMontoya on 2006-07-14
Sometimes when I am listening to Pandora the music stops after a little bit.  To fix the problem I usually find that evince is using /dev/dsp ( I do this by typing " lsof |grep dsp" and get the output "evince    6559     spruce   45u      CHR       14,3                8789 /dev/dsp".  

When I kill evince the problem typically fixes itself.  Anybody know why this is happening or better yet how to prevent it?

Thanks!

---

