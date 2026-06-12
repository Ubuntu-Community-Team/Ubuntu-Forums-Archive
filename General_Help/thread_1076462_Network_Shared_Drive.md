---
title: "Network Shared Drive"
date: 2009-02-21
forum: General Help
---

### Post by RhodyRich on 2009-02-21
If I open up "Computer" from "Places" I can easily navigate to a network shared drive and manage the files there. However if I am using a program such as Firefox and want to save a page, the network drive is not listed as a choice for the save. What do I have to do to get the network drive listed when I so a "Save As"?

Thanks

---

### Post by Faolan on 2009-02-21
The only way I've gotten this to work is to to permanently mount it and make it a shortcut for Nautilus.

---

### Post by cariboo on 2009-02-21
Nautilus mounts network drives in ~/.gvfs. So to save a file you would have to navigate to .gvfs/<network_share>.

Jim

---

