---
title: "Getting rid of XP"
date: 2009-12-19
forum: Desktop Environments
---

### Post by Alourien on 2009-12-19
Hey guys, I have a question.

I installed Ubuntu onto a second drive keeping XP on the other. How can I make it so that I can get rid of XP and boot Ubuntu from the second without the first?

Any help would be greatly appreciated.

---

### Post by /////// on 2009-12-19
I'm not sure I understand what you want. After installing Ubuntu, you should be seeing grub boot up. Do you want to completely delete XP, get rid of the xp boot option from grub or set Ubuntu as the default OS in grub?

---

### Post by koba101 on 2009-12-20
if i get your question right you could erase that hardisk...as for the GRUB, you can edit it on ubuntu (startup-manager) to remove the windows selection

---

### Post by MelDJ on 2009-12-20
did you install through wubi?

---

### Post by Alourien on 2009-12-21
> **koba101 said:**
> if i get your question right you could erase that hardisk...as for the GRUB, you can edit it on ubuntu (startup-manager) to remove the windows selection

But if I delete the other hard-disk, wont GRUB not boot? And to clear up my question, I am completely trying to get rid of XP.

---

### Post by Alourien on 2009-12-21
> **MelDJ said:**
> did you install through wubi?

Yeah, I did. Does that make a difference?

Thanks for all your help guys!

---

### Post by KeLa on 2009-12-21
It means that when you installed with wubi the ubuntu partitions are inside of an file in windows partition. So you can't remove Windows without destroying ubuntu.
You must install ubuntu via boot cd not with wubi if you want to get rid of windows.

---

### Post by Alourien on 2009-12-21
Ha...makes sense. Thank KeLa for your help, and the others as well!

---

