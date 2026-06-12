---
title: "Locked partitions!!!!"
date: 2009-04-21
forum: General Help
---

### Post by thewolfman on 2009-04-21
Hi chaps,

okay; here is the scenario:

If I want to install Ubuntu on a PC with pre-installed XP or Vista the pre-installed OS (C:Drive) won't let me because it is protected by the recovery partition of the pre-installed OS, the only way I can see to install Ubuntu is to delete the recovery partition of the existing OS; now if I do that I won't be able to restore XP or Vista if the need arise because the recovery partition has been wiped and to use the recovery CD normally the recovery partition must be intact.

So the question is: how do I install Ubuntu without damaging the existing OS?.

Any suggestions would be welcome and this is only hypothetical at the moment!.

Thanks.

thewolfman

---

### Post by mikewhatever on 2009-04-21
If things are as you describe and there is no way to create a separate partition for Ubuntu, you can still install it within Windows, or buy another HDD.

---

### Post by plucky on 2009-04-21
> to use the recovery CD normally the recovery partition must be intact.


So what happens if your hard disk crashes? I think this assumption is incorrect.You should always have a backup of your recovery partition so that you can restore your system in case of a hard disk failure.

You are allowed 4 primary partitions on one hard disk,of which one can be an extended partition,which can contain a great number of logical partitions.

Ubuntu can be installed and booted from a logical partition.

So from your scenario the recovery,XP and Vista partitions can be primary and you can then create an extended partition in which to install Ubuntu.

Or do as **mikewhatever** said.

Good Luck

---

### Post by CatKiller on 2009-04-21
What partitions have you got on that drive? You can have four primary partitions, and one of those primary partitions can be an extended partition which can contain a large number of other partitions.

(EDIT: Actually, plucky already said this. But still, we'll need to know what partitions you've already got if we're going to be able to help you)

Ubuntu's installer would normally resize an existing partition and create new partitions in the free space. You may still be able to do this, depending on what partitions you already have on there.

---

### Post by thewolfman on 2009-04-22
A good example of my efforts was with a friends PC (Varga, 250GB, pre-installed Vista).

When I tried to resize the C: drive partition the recovery partition wouldn't let me so regardless of whether I wanted to install Ubuntu or any other OS, the recovery partition denied my access to the drive. I was using a 3rd party partition tool from Data Becker and have never had problems with the tool.

The only way to install another OS was to wipe the recovery partition.

There was no way it was going to let me resize otherwise!.

Thanks thewolfman

---

