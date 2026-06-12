---
title: "Grub Menu not showing up on serial console?"
date: 2009-05-06
forum: General Help
---

### Post by NiceGuy12 on 2009-05-06
Hi everyone,

I have recently today configured serial console logins on my ubuntu server, everything appears great, except one thing ...

I also configured the grub menu to show up on the serial console, but after rebooting my ubuntu serve several times, the grub menu never show up the the serial console.

Grub configuration in **/boot/grub/menu.1st**
```
serial --unit=0 --speed=115200 --word=8 --parity=no --stop=1
terminal --timeout=15 serial console
```

Anybody have any ideas
Thanks

---

### Post by NiceGuy12 on 2009-05-07
Turns out my entry in grub ...

```
serial --unit=0 --speed=115200 --word=8 --parity=no --stop=1 terminal --timeout=15 serial console
```

Spanned over only one line, however as it turns out there are two distinct lines here, that is

```
line1 --> serial --unit=0 --speed=115200 --word=8 --parity=no --stop=1 
line 2--> terminal --timeout=15 serial console
```

Changing to solved
Thanks

---

