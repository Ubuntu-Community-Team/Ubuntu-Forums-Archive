---
title: "Undo update ?"
date: 2009-02-23
forum: General Help
---

### Post by mdharp on 2009-02-23
Is it possible to undo a Hardy Heron update  ?
The last one seems to have caused 2 of my computers to slow down 
_a lot_ doing basic tasks. Nothing else was changed before the problems started. 
Even writing email & text docs is try it & wait affair.
Any help appreciated.

---

### Post by dcstar on 2009-02-23
> **mdharp said:**
> Is it possible to undo a Hardy Heron update  ?
The last one seems to have caused 2 of my computers to slow down 
_a lot_ doing basic tasks. Nothing else was changed before the problems started. 
Even writing email & text docs is try it & wait affair.
Any help appreciated.

Any package can be rolled back to a previous version that exists in the repositories, you have to be more specific about **exactly** what updates you are referring to.

---

### Post by mdharp on 2009-02-23
Hi dcstar.
The update that seems to have caused problems is the latest one, about a week ago.
I think the last good one was Hardy 8.04 19-23. This last one I think was something like 8.04 23-24 or similar.
Sorry if inaccurate, but still very new learning PC 's & Linux.
Are these the details to look for in Repositories ?

---

### Post by dcstar on 2009-02-23
> **mdharp said:**
> Hi dcstar.
The update that seems to have caused problems is the latest one, about a week ago.
I think the last good one was Hardy 8.04 19-23. This last one I think was something like 8.04 23-24 or similar.
Sorry if inaccurate, but still very new learning PC 's & Linux.
Are these the details to look for in Repositories ?

You can look in the Synaptic File-History list for any "Upgraded" items, and then select them and use the Package-Force Version to change them to any previous version that is available.

My 8.04 system is still working fine and has all the current LTS updates (but I DO NOT use Backports - I find that causes too many problems).

---

### Post by mdharp on 2009-02-23
OK. I just found the Boot file browser.
There seem to be 2 versions of everything in here.
2.6.24-19-   &   2.6.24-23-
all in various files eg: config, system map, vmlinuz,abi, initrd.img etc
Is it as simple as deleting the unwanted update files ?
Sorry, I 'll check out your suggestion above.
PS  no idea what a backport is !!

---

### Post by mdharp on 2009-02-23
I went to System > Admin > Synaptic Package Manager. 
3 attempts to open it have failed. 
This problem is behaving like a Windoze virus.

---

