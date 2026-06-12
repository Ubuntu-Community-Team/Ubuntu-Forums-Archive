---
title: "CF Corruption"
date: 2009-01-06
forum: General Help
---

### Post by mat429 on 2009-01-06
Hi, 

after copying files to a 32gb compact flash card in ubuntu, i disconnected without first unmounting the drive.....  ooops

i did wait to make sure it had finished  - however - now the card is not recognised in ubuntu - or in windows.

it is not a case of losing data as it is all backed up and i would be happy to reformat the card, but just cannot get access to it.

what is the likely cause of this corruption? and is there any way of accessing / formatting it that i may not be aware of?

thanks for any help..

mat

---

### Post by caljohnsmith on 2009-01-06
While you have your CF card connected, how about posting:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

