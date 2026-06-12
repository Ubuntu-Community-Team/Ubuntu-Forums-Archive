---
title: "New Cpu"
date: 2006-03-25
forum: Desktop Environments
---

### Post by Digidiz on 2006-03-25
i am considering getting a new cpu, would i need to re-install Ubuntu??

---

### Post by cjazz on 2006-03-25
It would help to know what you have now, what you're getting and what kernel you're using now. Is this just a new cpu or does it involve a new motherboard as well?

---

### Post by Digidiz on 2006-03-25
no its just a new cpu thats compatible with the motherboard its a 3.0ghz ht, current one i have does not have ht

---

### Post by FIONEX on 2006-03-25
HT is bios related and not system related.  It just takes in more than one command from the cache at the same time.  So I doubt it has any impact on the drivers that are loaded.  As long as it's the same Model and Step, you should be fine.  Or am I wrong on this one?

My best advice to you is to back up your data regardless kuz you never know what can go wrong.

---

### Post by MichaelZ on 2006-03-25
Hello,

I do not hink that in you specific case a new installation would be necessary. Anyw, better to backup the data. If you will have problems, a new install would be necessary (IMHO).

Best wishes,
Michael

---

### Post by lcg on 2006-03-25
[QUOTE=Digidiz]no its just a new cpu thats compatible with the motherboard its a 3.0ghz ht, current one i have does not have ht[/QUOTE]
If you only change your CPU, you don't have to reinstall. However, you should install a SMP kernel to make use of the HT CPU.

HTH,
Lars

---

### Post by Digidiz on 2006-03-26
[QUOTE=lcg]If you only change your CPU, you don't have to reinstall. However, you should install a SMP kernel to make use of the HT CPU.

HTH,
Lars[/QUOTE]


ok cheers, i assume you mean add it with the synaptic package manager??

---

### Post by 5-HT on 2006-03-26
[quote=Digidiz]ok cheers, i assume you mean add it with the synaptic package manager??[/quote]

Yup, can be installed via synaptic/aptitude/apt/etc...whichever you prefer.

Here's a great guide for picking and installing the right kernel for your setup:

[http://ubuntuforums.org/showthread.php?t=85917]("http://ubuntuforums.org/showthread.php?t=85917")

As lcg mentioned, the smp kernel will need to be installed to take advantage of HT, though the new CPU should be detected automatically on boot.

HTH

---

