---
title: "memory/system diags software"
date: 2006-01-10
forum: General Help
---

### Post by egg on 2006-01-10
Hi,

I have access to a box, only via SSH.

I need to know:
how much memory is in the unit,
how many slots are there,
number free etc,
type of memory in use etc etc

basically, I need to upgrade the units memory - and need to gather as much info as possible about the current setup.

Which sw can tell me this? Is there a Sandra sisoft for linux?

---

### Post by nocturn on 2006-01-10
[QUOTE=egg]Hi,

I have access to a box, only via SSH.

I need to know:
how much memory is in the unit,
how many slots are there,
number free etc,
type of memory in use etc etc

basically, I need to upgrade the units memory - and need to gather as much info as possible about the current setup.

Which sw can tell me this? Is there a Sandra sisoft for linux?[/QUOTE]

I can't get to my box now (hardware failure tonight), but you should find much information in /proc.  
/proc/meminfo should list the amount of memory at the least.

---

### Post by egg on 2006-01-10
thanks, but I can't find that directory anywhere on the system. odd.

anything else out there?

---

### Post by Thirsteh on 2006-01-10
If /proc doesn't exist, you're probably not in a Linux shell, or you have restricted access (should give you a denied message not a not found message then though).

cat /proc/meminfo | grep MemTotal

will show you how many megs of RAM there are on the system. I don't think it's possible to just see how many ram slots there are.

I do not believe there is a Sisoft Sandra for Linux :)

---

### Post by egg on 2006-01-10
ok, thanks!
 that shows i have 256mb
in the meantime, I've found a quickspecs document for the unit, showing it has 4 slots. So, I guess I'm only using one, and can go crazy filling with new memory! :-)

---

