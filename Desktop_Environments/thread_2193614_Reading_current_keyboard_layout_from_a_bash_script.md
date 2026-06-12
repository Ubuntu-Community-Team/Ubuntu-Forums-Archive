---
title: "Reading current keyboard layout from a bash script"
date: 2013-12-13
forum: Desktop Environments
---

### Post by arbiel-perlacremaz-g on 2013-12-13
Hi

Writing a bash script to boot a PC from an iso file (using grub2 loopback command), I try to have it read, in a multi-language multi-keyboard-layout, the current language and keyboard layout and pass the information to the kernel.

The command 
setxkbmap -print | grep xkb_symbols | awk '{print $4}' | awk -F"+" '{print $2}'
prints the preferred settings, but not the current one (in use).

Can anybody help ?

Arbiel

---

