---
title: "Trouble executing qbus commands that only work under specific circumstances"
date: 2017-10-27
forum: Desktop Environments
---

### Post by accounts0 on 2017-10-27
I'm on Ubuntu Server 16.04.3 with kubuntu installed. Using KDE's System Settings Autostart section, I run a number of bash scripts at logon.

My original script [1] which used to work on KDE Neon Git DevStable, returns apparently unrecoverable errors [2] between starting amarok & the first qdbus command. Somehow the commands that fail in the script run fine when pasted into a terminal alone one after the other. This lead me to spend some time on paths, which ended up being a useless effort.

To achieve the desired result I've had to split the necessary commands into 2 separate bash scripts, the first of which [3] calls the second [4], which sleeps a bit so that it executes in order.

I spent far more time tinkering with this than I like to admit. Tried most everything Google threw at me, provided I didn't need to know python or whatever else was going on when others encountered something similar. I would like to learn where I went wrong, however for now I'm happy it works, regardless of it being a less than ideal solution.

Maybe it's obvious to someone here & I could be enlightened...



[1]
[http://sebsauvage.net/paste/?b4249c72144e2bd3#iuJWCmzP+UD57U2SbA+3Dr12tWiMloqcQgs73taJD3Q=](http://sebsauvage.net/paste/?b4249c72144e2bd3#iuJWCmzP+UD57U2SbA+3Dr12tWiMloqcQgs73taJD3Q=)


[2]
[http://sebsauvage.net/paste/?4fdc69591197b9cd#Lw3DbxX0gs51Fs1QhSYXeUBp0Dct8xAxEkkWBL+H4wo=](http://sebsauvage.net/paste/?4fdc69591197b9cd#Lw3DbxX0gs51Fs1QhSYXeUBp0Dct8xAxEkkWBL+H4wo=)


[3]
[http://sebsauvage.net/paste/?577b6456af61cc36#G0koVPDCvZiMOgSDiw+RbQMpAZd5wXpJ5UxodNYMyRQ=](http://sebsauvage.net/paste/?577b6456af61cc36#G0koVPDCvZiMOgSDiw+RbQMpAZd5wXpJ5UxodNYMyRQ=)


[4]
[http://sebsauvage.net/paste/?aff4e8f0c430caaa#jZ1GsIxMvz/M/Z/vwJ6rijb8joonvkahvkT/U7rDrlY=](http://sebsauvage.net/paste/?aff4e8f0c430caaa#jZ1GsIxMvz/M/Z/vwJ6rijb8joonvkahvkT/U7rDrlY=)

---

### Post by accounts0 on 2017-11-05
bump

---

### Post by accounts0 on 2017-12-01
bump

---

