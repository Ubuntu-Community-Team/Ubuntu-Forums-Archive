---
title: "Sync flash memory"
date: 2009-04-28
forum: General Help
---

### Post by dox_drum on 2009-04-28
Hi there!

I'd like to know if there is a way to keep sync a flash memory with some of my files. I mean, I don't have a clue about it... I've read it's possible, but none of the programs are familiar to me.

Would you please give me some advises?

Thanks in advance...

---

### Post by dcstar on 2009-04-29
> **dox_drum said:**
> Hi there!

I'd like to know if there is a way to keep sync a flash memory with some of my files. I mean, I don't have a clue about it... I've read it's possible, but none of the programs are familiar to me.

Would you please give me some advises?

Thanks in advance...

Have a look at the **unison** package.

---

### Post by dox_drum on 2009-04-29
> **dcstar said:**
> Have a look at the **unison** package.

Hi dcstar! thank you for the suggestion.

I tried with unison and got the following error
```
Failed to set permissions of file /media/KINGSTON/Documents/.unison.Coloquitos.36d98ddb3fa996afe9867150d87050fd.unison.tmp/Coloquito[03].doc to rw-r--r--: the permissions was set to rwx------ instead. The filesystem probably does not support all permission bits. You should probably set the "perms" option to 0o1633 (or to 0 if you don't need to synchronize permissions).
```

After trying to do it as root or even try to change the permissions of the flash memory... the result is always the same.

Does anyone know where is the problem?

Thank you again.

---

### Post by kpkeerthi on 2009-04-29
Is it FAT32 formatted? FAT32s do not support LINUX/UNIX permissions and hence the warning.

---

### Post by dox_drum on 2009-04-29
> **kpkeerthi said:**
> Is it FAT32 formatted? FAT32s do not support LINUX/UNIX permissions and hence the warning.

Really I don't know.

What could I do in order to solve that issue?

---

