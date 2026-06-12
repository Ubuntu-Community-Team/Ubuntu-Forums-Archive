---
title: "breezy kernel in hoary distro?"
date: 2005-09-09
forum: Desktop Environments
---

### Post by blakken on 2005-09-09
my simple question is where could I get the latest kernel package of breezy in order to install it over an hoary  install?is that possible ?thanx  ;-)

---

### Post by Kuolio on 2005-09-09
It's quite simple:

Just update your sources.list and replace hoary with breezy. Then start synaptic, update (and dont upgrade, unles you want breezy), search for kernel and install it. 

After it's done, update (optional) kernel headers and restricted modules (for nvidia/ati support). When you are done, update sources.list back to hoary and update synaptic.

That's how I did it, and everything is working like a charm.

---

### Post by f1dave on 2005-09-09
...for now ;)

Just a note to new users, this is something that you really don't need or want to do until you know what you're doing. Throwing in newer kernels and whatnot can come later, after you're used to it. Imho it's worth just waiting for breezy anyway... normal users don't need to constantly update their kernel.

---

### Post by blakken on 2005-09-09
[QUOTE=Kuolio]It's quite simple:

Just update your sources.list and replace hoary with breezy. Then start synaptic, update (and dont upgrade, unles you want breezy), search for kernel and install it. 

After it's done, update (optional) kernel headers and restricted modules (for nvidia/ati support). When you are done, update sources.list back to hoary and update synaptic.

That's how I did it, and everything is working like a charm.[/QUOTE]
 ;-)  thank you very much but that's the reason why I asked how to install kernel over hoary cause i don't want to use breezy ...all I heard is that it is buggy

---

