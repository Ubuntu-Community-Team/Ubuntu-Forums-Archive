---
title: "can't burn dvd iso"
date: 2006-02-19
forum: Desktop Environments
---

### Post by kasemodz on 2006-02-19
Alright, I have a compressed dvd image. I tried to burn it through k3b and it gave me an error. Basically it was trying to burn it but it couldn't. Like the dvd would run a little then slow down and keep doing that. In the debugging it gave me an i/o error.

It gives me the same error at gnomebaker.
>          0/4681486336 ( 0.0%) @0x, remaining ??:??
         0/4681486336 ( 0.0%) @0x, remaining ??:??
         0/4681486336 ( 0.0%) @0x, remaining ??:??
         0/4681486336 ( 0.0%) @0x, remaining ??:??
         0/4681486336 ( 0.0%) @0x, remaining ??:??
         0/4681486336 ( 0.0%) @0x, remaining ??:??
         0/4681486336 ( 0.0%) @0x, remaining ??:??
         0/4681486336 ( 0.0%) @0x, remaining ??:??

---

### Post by kasemodz on 2006-02-19
Alright in k3b setup i have cdrecord and cdrdao. Do i need anything else?

---

### Post by nalmeth on 2006-02-19
You should make sure they have the proper permissions.
Open k3b, go to settings --> k3b setup
make sure cdrdao and cdrecord have root permission at bottom of window

---

