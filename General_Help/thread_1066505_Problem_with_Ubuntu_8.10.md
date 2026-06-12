---
title: "Problem with Ubuntu 8.10"
date: 2009-02-10
forum: General Help
---

### Post by Aesculaius on 2009-02-10
Hi there, i have ubuntu installed on my Win XP system using wubi.. well it glitched and crashed.. when I rebooted it gave me a grub prompt.. so I figured instead of trouble shooting ill just kick it out and reinstall it. Unfortunately.. a piece of it is left over. Its under C:\Ubuntu.old.. theres a folder in there called disks and I cant get rid of it.. its corrupted. I tried booting SystemRescueCD to get rid of it and it gives me an input/output error.. when I run ls -l ubuntu.old I get this:
total: 0
d??????????? ? ? ? ?          ? disks

rmdir --ignore-fail-on-non-empty wont get rid of the directory.. and passing in -v doesnt give me any info to play with just input/output error.

---

### Post by Aesculaius on 2009-02-11
Hmm nevermind.. I think when I ran fsck on the drive with SystemRescueCD it must of fixed it.. I was able to delete it with windows. Thanks anyway though for those who may have posted =)

---

