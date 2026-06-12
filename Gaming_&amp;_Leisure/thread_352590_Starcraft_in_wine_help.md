---
title: "Starcraft in wine help"
date: 2007-02-03
forum: Gaming &amp; Leisure
---

### Post by mechel on 2007-02-03
Hi, im sorry if there is another thread on this, but I've looked for a while and have found nothing. I installed Starcraft and it has seemed to work good so far except for one thing, whenever I try to make a new id it says that I dont have permission to write to that disk... I am really new to linux and dont really know how to fix that.

Any help would be great and thanks in advance.

---

### Post by mechel on 2007-02-03
well i searched up on it some more and kind of figured it out, i am trying the chmod comand, but im having some trouble. When i type chmod 777 (filedir) it doesnt change it to read write exe for everyone. In fact it doesnt do that for anyone and i really dont know what the problem is other then im doing the command wrong and i dont think i am... Any help would be  great, Thanks.

---

### Post by slimdog360 on 2007-02-03
sudo chmod -R 777 /filedirectory

---

### Post by mechel on 2007-02-03
Hmm... I tried it out and I still cant access my starcraft directory, but I can access everything else in my program files directory. (I did sudo chmod -R 777 /root/.wine/drive_c/Program\ Files/  and the Starcraft Directory is in program files)

---

