---
title: "Starting ubuntu without loading gui"
date: 2005-09-08
forum: Desktop Environments
---

### Post by philpot on 2005-09-08
Is there a way to boot up without loading the kubuntu GUI? I am having a problem with "sync out of range" messages.

---

### Post by Ptero-4 on 2005-09-08
[QUOTE=philpot]Is there a way to boot up without loading the kubuntu GUI? I am having a problem with "sync out of range" messages.[/QUOTE]
 Look for a "recovery" entry in your grub menu and boot from it, or if there's no such entry select the one you use to boot your system, press "e" and add "1" at the end, then press "enter" and "b". This will make ubuntu load in singleuser mode where you have full permissions and no gui. Just remember to not do anything more than what you need to do to fix the gui. You may end up breaking your system more than what it's already.

---

