---
title: "apt-get install is looking for cd"
date: 2006-02-15
forum: Desktop Environments
---

### Post by namit on 2006-02-15
i seam to be asking for cd but i do not have the cd anymore and am on dialup so can not download cd that easy.

anyway of getting around this?

 'Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

---

### Post by ollyshaw on 2006-02-15
Hi,

Edit /etc/fstab

Find the line with CD in it and comment it out by adding a # at the start of the line. Alternatively use synaptic and edit your sources in there.

Olly

---

### Post by GeneralZod on 2006-02-15
[QUOTE=ollyshaw]Hi,

Edit /etc/fstab

Find the line with CD in it and comment it out by adding a # at the start of the line. Alternatively use synaptic and edit your sources in there.

Olly[/QUOTE]

There's really no need to mess around with fstab for this :)

Just open up /etc/apt/sources.list, comment out the relevant line (it will be clear which one it is - it's usually at the top), save, and do a 

```

sudo apt-get update

```

---

