---
title: "missin 30GB!!!"
date: 2009-04-04
forum: General Help
---

### Post by ellwood00 on 2009-04-04
ok so ive installed ubuntu using the install inside windows option many times and had never ahd a problem. so i went to do it today and i hade a problem with ubuntu that i didnt feal like looking up how to fix so i was just gunna reinstall. but when i uninstalled using windows i never got back my 30gb. i have no idea where it is. im runnin xp professional sp3. can some one help me please.

---

### Post by bertolo on 2009-04-04
i suppose install inside it's using a virtual machine... i am correct you should search for the ubuntu partition that is somewhere in the virtual machine directories, delete it mannually.

---

### Post by ellwood00 on 2009-04-04
no i think its called wubi that it used. and it dosent make its own partition because i checked

---

### Post by bertolo on 2009-04-05
run pc with gparted or partition magic to resto the missing 30gb

---

### Post by ellwood00 on 2009-04-05
i ran gparted through the ubunut live cd and there was only my 220gb and 10gb partitionhs that i made myself when i installed windows.

---

### Post by lisati on 2009-04-05
Forget gparted for now: the handful of times I've used wubi to install "within" windows it has set up a folder c:\ubuntu

---

### Post by ellwood00 on 2009-04-05
yea the folder was 0 bites and i deleted it and i still dont have my space back
imm thinking of just formating my hdd

---

### Post by lisati on 2009-04-05
> **ellwood00 said:**
> yea the folder was 0 bites and i deleted it and i still dont have my space back
imm thinking of just formating my hdd

And emptied the recycle bin?

I'm off to cook lunch now: good luck.

---

### Post by bertolo on 2009-04-05
> **lisati said:**
> And emptied the recycle bin?

I'm off to cook lunch now: good luck.

big files don't even go to reciclage bin.

---

### Post by ellwood00 on 2009-04-05
yea my recyle bin is empty i hgave no idea where it went

---

### Post by ellwood00 on 2009-04-06
so i talked to my programing teacher today. he said that i may have a hardware problem because it created an un writable sector when it uninstalled.

---

### Post by kanikilu on 2009-04-06
> **ellwood00 said:**
> so i talked to my programing teacher today. he said that i may have a hardware problem because it created an un writable sector when it uninstalled. Run **chkdsk c: /r** from a command prompt to schedule a check-disk the next time Windows starts.

---

### Post by ellwood00 on 2009-04-06
i already ran a check disk and a defrag and a disk wiper. nothing gets the memory back

SO problem fixed. i was browsing my hdd on my dad's computer thru the network and i found thsi folder called found.000 that i couldn't see when i browsed my hdd with my computer. so this weekend at my internet less grandmas house with the most update computer being a gateway color book running windows 3.11, i decided to use windr to see if i could find a file using the space, an there was the folder using 30gb of disk space. it was ubuntu.disk.

---

