---
title: "How to make a backup or a restore point?"
date: 2006-09-02
forum: Desktop Environments
---

### Post by rodrigo666 on 2006-09-02
Greetings,

I'm having some bad luck related problems when trying to configure my ATI Radeon 9600 PRO 256mb with XGL+Compiz.

I mean: I get all right, but eventually something like a blackout or another accident crashs up my system and I have to format it and install all again.

Right now, I've just finished to install all of my favorites codecs, softwares, themes etc.

So, before I try to configure my videocard and install XGL+Compiz again, I would like to know if there is a way to create a backup or restore point of my actual system, so if something goes wrong again, I don't have to format and install all my stuff again.

Thanks to all of you.

---

### Post by reacocard on 2006-09-02
```
sudo apt-get install partimage
```

---

### Post by rodrigo666 on 2006-09-02
Problem solved.

Partimage could not help me because it can't create a image of a mouted partition.

But I found this wiki (in portuguese) that teach step by step how to do that.

[http://www.guiaubuntupt.org/wiki/index.php/Backup_&_Restaurar_o_sistema](http://www.guiaubuntupt.org/wiki/index.php/Backup_&_Restaurar_o_sistema)

Thanks anyway.

---

### Post by aysiu on 2006-09-02
PartImage needs to be run from a live CD:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by rodrigo666 on 2006-09-02
Yeah, I got that.

Still, the instructions I mentioned on that wiki is more easy and do the job.

Thanks for the reply, people on this forum are very kind.

---

