---
title: "Compiz fusion for Trident CyberBlade XPAil"
date: 2009-03-28
forum: General Help
---

### Post by halex00 on 2009-03-28
Hello to everyone, i just installed xubuntu 8.10 on my old laptop Toshiba Satellite 1800-S254, and im trying to run compiz fusion on itbut it doest let me. It have a Trident Cyberblade XPAil

I already installed compiz, emerald but when i try to run the compiz i get this:
halex@unknown:~$ compiz --replace

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: true 
no true found, exiting
halex@unknown:~$ 
halex@unknown:~$ 


Plese, someone help me I really want this laptop to work with all the cool effects.

---

### Post by cariboo on 2009-03-29
Your video chipset isn't supported by the manufacturer, the only drivers are the default drivers that are installed  when you installed xubuntu. You may want to try the vesa driver to see if you can use compiz. In this section change:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"tridentfb"
EndSection
```

to

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"vesa"
EndSection
```

Jim

---

