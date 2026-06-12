---
title: "reinstall xp w/ dual boot"
date: 2009-01-07
forum: General Help
---

### Post by cybo on 2009-01-07
i have Ubuntu and XP installed on my laptop. XP started giving a lot of problems and i want to reinstall it. the way i usually did it (before i had ubuntu) is i just formated the hard drive and reinstalled xp. does anyone know if i can do it the same way or there is something extra i have to do?

thnx

---

### Post by Julius1988 on 2009-01-07
do you want to do a complete format or u want to recover ubuntu after installing xp?

---

### Post by thedarkwinter on 2009-01-07
Hi

Have you installed them in separate partitions, or the same partition (using Wubi - which i have no experience with)?

Wubi - formatting will kill them both.

If they are in separate partitions, then yes you can format the C: during the windows install, and carry on as normal. (just be careful not to format the linux partition :)

The problem comes in when XP overwrites GRUB, so you wont have the boot menu any more. You will need to then boot of the ubuntu live cd, and install grub again. May need to ask for more help on that as i can't remember off hand how easy that part is...

cheers,
Michael

---

### Post by cybo on 2009-01-07
i want to recover ubuntu after formating. both os are installed on the same partition.

---

### Post by theozzlives on 2009-01-07
> **cybo said:**
> i want to recover ubuntu after formating. both os are installed on the same partition.

Back up your data cause you'll have to re-install both.

---

### Post by cybo on 2009-01-08
what happens if i format c? will it wipe out ubuntu along with xp?

---

