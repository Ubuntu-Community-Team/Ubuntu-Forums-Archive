---
title: "Rollback Rx-Fragmentation Problem"
date: 2008-12-18
forum: General Help
---

### Post by jek1862 on 2008-12-18
I have installed the Rollback RX utility.  However, I have a fragmentation problem with it.  I made sure my disc was fully defragged before installing it.  Yet, from the initial snapshot, which is the only one I have, it shows a whopping 822 fragments on the file for rollback rx.
Is this normal?  I would think not.  I have used the utility's defrag tool to try and defrag it, no luck.  I have used other defrag tools to defrag it, still the same problem.
Please educate me about this, and how to fix this problem, please. Thank you.

---

### Post by prshah on 2008-12-18
> **jek1862 said:**
> I have installed the Rollback RX utility.  However, I have a fragmentation problem with it.

This is a Windows program not related to "Ubuntu, Kubuntu, Edubuntu and Xubuntu", so it should be in a windows (sub)forum.

That said, you should disable rollback RX _before_ running a disk defrag. [Source]("http://en.wikipedia.org/wiki/Rollback_Rx"):
> It can be beneficial to disable RollBack Rx prior to using any Windows defragmentation utility, as file relocations are treated by RollBack Rx as relatively large data changes and can therefore cause large snapshots. The current version 8 does not support any third party disk defragmenter. However, defragmentation can be carried out without disabling RollBack Rx, and the data used can be freed by "re-baselining" (which will cause the removal of all snapshots taken so far).

---

