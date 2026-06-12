---
title: "Cannot access computer!"
date: 2008-12-17
forum: General Help
---

### Post by jeremycollins on 2008-12-17
I tried to uninstall ubuntu that was dual booted with windowsXP but now I can't access my computer. I removed all partitions except for my windows partition. Now when I turn my computer on I get this:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 22


What do I do?

---

### Post by miked860 on 2008-12-17
> **jeremycollins said:**
> I tried to uninstall ubuntu that was dual booted with windowsXP but now I can't access my computer. I removed all partitions except for my windows partition. Now when I turn my computer on I get this:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 22


What do I do?

It could mean you have a corrupt partition table. I do not know how to fix it. Sorry I can't help you. =( The only reason I know is because I am experiencing the same problem for various reasons.

---

### Post by Snow986 on 2008-12-17
When you deleted the linux partition you deleted the boot loader.  You need to get to windows manually through the command line and edit the boot file to boot your windows partition.  I can't remember exactly how to do it but hopefully someone will chime in else I'll try to remember.

---

### Post by scouser73 on 2008-12-17
Hello, I Googled some information that should be able to help you sort out the problem with Grub. [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

I hope you manage to sort the problems out.

---

### Post by PocketDog on 2008-12-17
It's simple enough buddy, don't worry. Grub's looking for Ubuntu but it's gone, that's all. You don't need Grub any more so boot from your XP install disc, press R when prompted to go to the recovery console. When you get to the command line type FIXMBR, press enter, and reboot.

---

### Post by Snow986 on 2008-12-17
What he said ^.  :)

---

### Post by jeremycollins on 2008-12-17
I still don't understand. Is there anything to fix this? I have a dell xp install disk.

---

### Post by Snow986 on 2008-12-17
put your xp startup disk in.  Then boot to your cd drive.  then follow Pocket Dog's instructions and you're good to go.

---

### Post by jeremycollins on 2008-12-17
I went into recovery mode, and it asked which windows account to load, and I chose mine (the only one available), and it asked for a password. After typing in my password, it said it was an invalid password.  I don't know why though, because I know its right! Any ideas?

---

### Post by jeremycollins on 2008-12-17
Would I have to reinstall xp? If so, how long does that take?

---

### Post by sPiN1 on 2008-12-17
i believe it is telling you to stay with linux cause windows is a greedy ******* who won't share. ;)

---

### Post by jeremycollins on 2008-12-18
Ubuntu doesn't help if it doesn't support my sound card, printer, and wireless netwrk system. How can I fix my computer?

---

### Post by TVTrukChik on 2008-12-18
I think it wants the password for the Administrator account.  If you don't remember setting a password for that account, try just hitting the Enter key and hope there's no password set.

---

