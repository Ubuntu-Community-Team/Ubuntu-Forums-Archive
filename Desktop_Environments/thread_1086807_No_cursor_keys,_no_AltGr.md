---
title: "No cursor keys, no AltGr"
date: 2009-03-04
forum: Desktop Environments
---

### Post by QNo on 2009-03-04
Hi,

After Upgrading to Kubuntu 8.10 incl. KDE 4.2, the cursor keys (up, down, right, left, screen up, screen down ...) as well as the AltGr key (especially no |, no @) do not work in any X application (nor with KDE nor with GNOME); they work on the text based console, and of course they did work prior to the upgrade.

I attached my xorg.conf and the last Xorg.0.log. I can't find anything wrong, although i do not really understand that HAL part. Is there anything what i have to fix?

TIA
Chris

---

### Post by QNo on 2009-03-05
Just tested: Windowmaker and twm have the same problem.

---

### Post by QNo on 2009-03-14
The problem appeared, when i logged in as a user via kdm or when i started startx as a user. It did not appear when i started startx as root. So  i looked for config files in ~. The only candidate was .Xmodmap. I removed that file (of course into a backup directory), and everything worked fine.

---

