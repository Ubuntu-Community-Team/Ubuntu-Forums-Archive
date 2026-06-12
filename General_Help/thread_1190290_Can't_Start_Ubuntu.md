---
title: "Can't Start Ubuntu"
date: 2009-06-17
forum: General Help
---

### Post by dkolok on 2009-06-17
Have dual boot Ubuntu and Windows XP. When attempting to boot to Ubuntu get 

"BusyBox v1.1.3 (Debran 1.11.1.3-5 ubuntu12)Built-in shell (ash)
Enter 'help' for list of built-in commands.

(initramfs) -"

Tried researching threads with same problem. Dual boot; I am not attempting to boot from CD.

---

### Post by snakeman21 on 2009-06-17
Sounds like you're stuck in the shell (command line interface).  Unfortunately, though this has happened to me before, I do not know how to fix it... I ended up reinstalling.  Hopefully someone else will know?

---

### Post by jonobr on 2009-06-17
I would recommend verifying the checksum on the downloaded file (iso) to ensure the file is ok.

---

### Post by dkolok on 2009-06-17
Don't understand how to verify checksum on the downloaded file (iso). Reinstall Ubuntu? Do not want to lose data.

---

### Post by jonobr on 2009-06-17
From reading your thread, i figured you were booting from cd....

However, it looks as if you had a working ubuntu install and it started doing this? Is that correct?

---

### Post by dkolok on 2009-06-18
Yes, correct, Ubuntu installed.

---

### Post by metiosarius on 2009-06-18
> **dkolok said:**
> Yes, correct, Ubuntu installed.

Wait around for better idea's, but, if you get desperate, you can always use a livecd to facilitate copying your /home directory to an external drive and/or network location, then reinstall and restore your files.

Sounds to me like either a) grub got messed with, or b) possible hdd failure.

---

### Post by dkolok on 2009-06-18
Windows works when I choose it in dual boot.

---

### Post by metiosarius on 2009-06-18
> **dkolok said:**
> Windows works when I choose it in dual boot.

Search google or this forum for using a livecd to re-install grub. it just might fix your issues. I don't really have the time to find it for you atm.

---

### Post by jonobr on 2009-06-18
Yep agreed, wait around a while lets see if there is something out there which may fix your issue not needing a resintall...

---

### Post by jonobr on 2009-06-18
Hello

I found [THIS]("http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-wont-boot-past-black-command-type-screen-725218/") which started off positive and a ends up with going into recovery mode which I think you tried,
Have a read/.

---

### Post by merlinus on 2009-06-18
Run from the live cd, open a terminal and post results of

```

sudo fdisk -l

```

---

