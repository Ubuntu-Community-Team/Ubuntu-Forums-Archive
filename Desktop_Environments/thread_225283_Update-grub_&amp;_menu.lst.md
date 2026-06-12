---
title: "Update-grub &amp; menu.lst"
date: 2006-07-29
forum: Desktop Environments
---

### Post by Dubbayoo on 2006-07-29
Everytime I install a new kernel update-grub changes my default boot device to hd1,0) which is wrong.
I have set these options correctly:

## default grub root device
## e.g. groot=(hd0,0)
groot=(hd0,0)

## should update-grub adjust the value of the default booted system
## can be true or false
updatedefaultentry=false


but it still changes everything to hd1,0) How can I stop this?

---

### Post by Dubbayoo on 2006-07-29
^

---

### Post by fensirien on 2006-07-29
> ### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

try:
#groot=(hd0,0)
#updatedefaultentry=false

---

### Post by Dubbayoo on 2006-07-29
I missed that; good catch.

---

