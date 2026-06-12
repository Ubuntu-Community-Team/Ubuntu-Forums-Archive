---
title: "How To Uninstall ubuntu"
date: 2006-02-27
forum: Desktop Environments
---

### Post by rjfalcon on 2006-02-27
Hi, How do I uninstall ubuntu and all the components of ubuntu?

RJ-Falcon

---

### Post by Ramses de Norre on 2006-02-27
Just install whatever you want over it.
Or delete the partitions.
What's the reason you don't like it?

---

### Post by rjfalcon on 2006-02-27
I like it.. very much actually but My internet modem doesn't have the drivers.. so my Internet doesn't work.

---

### Post by rjfalcon on 2006-02-27
When I delete the partition is.. Grub (or something like that) also deleted?
so I don't get the screen at the boot..

---

### Post by vbmaster on 2006-02-27
for every Linux distribution the method of uninstalling is by removing the partition  in which it was installed

[QUOTE=rjfalcon]When I delete the partition is.. Grub (or something like that) also deleted?
so I don't get the screen at the boot..[/QUOTE]

Of course... grub is in /boot/grub of your ext3 partition

---

### Post by rjfalcon on 2006-02-27
[QUOTE=vbmaster]for every Linux distribution the method of uninstalling is by removing the partition  in which it was installed



Of course... grub is in /boot/grub of your ext3 partition[/QUOTE]


Ok thnx.

When there are drivers for my modem I'll install it again. ^^

---

### Post by Ramses de Norre on 2006-02-27
If you've got a dual boot with windows: insert the installation disc, look for something like a recovery mode, type fixmbr at the prompt.
You've got you original win-only mbr back then.

---

### Post by rjfalcon on 2006-02-27
[QUOTE=Ramses de Norre]If you've got a dual boot with windows: insert the installation disc, look for something like a recovery mode, type fixmbr at the prompt.
You've got you original win-only mbr back then.[/QUOTE]

The installation disk of Ubuntu or Windows?

---

### Post by Ramses de Norre on 2006-02-27
Does a modem need drivers? Or do you mean the ethernet card?
I thought all modems use the same standards and plugin in the cable is all you need to do.

EDIT: the windows installation disc.

---

### Post by rjfalcon on 2006-02-27
[QUOTE=Ramses de Norre]Does a modem need drivers? Or do you mean the ethernet card?
I thought all modems use the same standards and plugin in the cable is all you need to do.

EDIT: the windows installation disc.[/QUOTE]

My adapter for my wireless network.. It isn't working and I think it's the drivers.

---

