---
title: "Kubuntu Sound Problem"
date: 2005-06-04
forum: Desktop Environments
---

### Post by loki on 2005-06-04
Hello all,

Very odd sound problem with Kubuntu. When using Kaffeine or any other sound application for the first time sound will not start. The only solution is to use KSCD to  start playing a CD and then sound will work in any application. 

I currently have two sound cards configured on my system, the first one is an onboard sis sound card and the other is a soundblaster live 5.1. Kubuntu has assigned the onboard sis card as defualt although I have switched off all input & output to that card in Kmix. This appears to work ok once I have started KSCD. (I cannot dissable the sis sound in the bios  :|  ) 

restarting ALSA seems to have no effect on this.

Any ideas would be most welcome.

Loki

---

### Post by dave9191 on 2005-06-04
Try starting 'artsd' and see if that solves the problem. 

Dave

---

### Post by loki on 2005-06-06
Cheers dave,

This could have been the missing piece I've been looking for, It still needs more testing though. I'll post my findings as soon as.

Cheers.

---

