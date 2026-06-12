---
title: "Nvidia Driver requires CPUs with SSE to run"
date: 2009-03-24
forum: General Help
---

### Post by MNICY on 2009-03-24
My brother has a linux box:
Xubuntu 8.10
AMD Duron processor
250 MB RAM
Geforce FX 5500

Everything was working great on it for months; until today when he downloaded updates.
Now, many applications wont run. The Add/Remove programs wont run. Nvidia Settings wont run...
Many programs...

I click the icon, and the icon changes to loading, but then stops after a few seconds.

I tried running totem in a terminal; this is what I got:
```
NVIDIA driver requires CPUs with SSE to run
The current CPU does not support SSE
```
Totem, and other applications were working until he installed the update today.

Does anyone know any way to fix this?

---

### Post by dcstar on 2009-03-24
> **MNICY said:**
> My brother has a linux box:
Xubuntu 8.10
AMD Duron processor
250 MB RAM
Geforce FX 5500

Everything was working great on it for months; until today when he downloaded updates.
Now, many applications wont run. The Add/Remove programs wont run. Nvidia Settings wont run...
Many programs...

I click the icon, and the icon changes to loading, but then stops after a few seconds.

I tried running totem in a terminal; this is what I got:
```
NVIDIA driver requires CPUs with SSE to run
The current CPU does not support SSE
```
Totem, and other applications were working until he installed the update today.

Does anyone know any way to fix this?

Roll back the Nvidia driver to a previous version and lock it.

---

### Post by MNICY on 2009-03-25
> **dcstar said:**
> Roll back the Nvidia driver to a previous version and lock it.
I tried, but it did not work :(

---

