---
title: "wine sound errors"
date: 2006-09-17
forum: Desktop Environments
---

### Post by NiksaVel on 2006-09-17
Hey all, 

I have succesfully installed wine from the repos, but I keep getting errors in my console whenever I click on the audio tab:

> ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
/bin/sh: /usr/bin/esd: No such file or directory
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory


can anyone help me with this, because this whole area is all very new to me.


thanks!

---

### Post by Fixxxer on 2006-09-17
Try ```
sudo modprobe snd-seq
```And then access the audio tab. If that works then ```
sudo gedit /etc/modules
``` and add snd-seq to the file. Hope that helps...

---

### Post by NiksaVel on 2006-09-17
okay, I did that and I'm down to one error:

> niksavel@darth-kubuntu:~$ winecfg
/bin/sh: /usr/bin/esd: No such file or directory
niksavel@darth-kubuntu:~$    

---

### Post by Fixxxer on 2006-09-18
Sorry don't know how to fix that, but I'll look around for a solution.

---

### Post by NiksaVel on 2006-09-18
I just managed to launch half-life 2 deathmatch via wine and sound worked fine, so I guess you don't need to bother as it works fine even though the error shows in winecfg...

thank you very much for you help!

---

### Post by Fixxxer on 2006-09-18
No problem...

---

