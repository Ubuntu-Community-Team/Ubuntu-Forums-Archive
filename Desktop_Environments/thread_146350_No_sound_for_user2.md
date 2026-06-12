---
title: "No sound for user2"
date: 2006-03-18
forum: Desktop Environments
---

### Post by anandam on 2006-03-18
Hi everyone,

While installing ubuntu , I had made user1 account and after installation I made user2 account. Now user1 is having sound, but there is no sound for user2. Alsamixer says "Permission Denied". But if I change the permissions of files controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D1p  seq  timer
 in /dev/snd/  for others, user2 is also having sound.

But when I reboot the machine, again the permissions are lost and so no sound for user2.

What should I do?  And yes, I am a newbie!

---

### Post by Swab on 2006-03-18
The new user needs to be a member of the audio group.. you can do that from the users and groups option in system > administration

---

### Post by anandam on 2006-03-18
Such a quick reply!!! I am impressed!

Thanks Swab.

---

### Post by ericsp on 2006-04-22
Same problem in Dapper Beta. I would consider this as a bug, if you want to humanize linux... BTW, there is no group called 'audio' under Dapper. Any suggestion?

---

### Post by Swab on 2006-04-22
[QUOTE=ericsp]Same problem in Dapper Beta. I would consider this as a bug, if you want to humanize linux... BTW, there is no group called 'audio' under Dapper. Any suggestion?[/QUOTE]

Strange, I have an audio group in Dapper.

Edit: Have you checked "Show all users and groups" ?

---

