---
title: "SDL: No available video device"
date: 2008-12-16
forum: General Help
---

### Post by EntityIngredient on 2008-12-16
When I try to run any program that uses SDL, I get this error:
```
Unable to initialise SDL : No available video device
```
I have a *NVIDIA GeForce 8500 GT*, and I'm using the *NVIDIA accelerated graphics driver (version 177) [Recommended]* driver.
I've already tried to
[LIST]
[*]Set DISPLAY env to :0
[*]xhost +localhost
[*]Run the program as root
[*]Reboot..
[/LIST]
Also note that I'm not compiling the program myself, and this happens with all (And *only*) programs that use SDL.

Can anyone help?

---

### Post by EntityIngredient on 2008-12-17
Nothing works..  ](*,)

---

### Post by EntityIngredient on 2008-12-17
I compiled SDL myself and it works now. Hooray.

---

