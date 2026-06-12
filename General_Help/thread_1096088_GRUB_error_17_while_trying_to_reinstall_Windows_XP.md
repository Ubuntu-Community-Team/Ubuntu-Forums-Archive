---
title: "GRUB error 17 while trying to reinstall Windows XP"
date: 2009-03-14
forum: General Help
---

### Post by Hr_Birnbaum on 2009-03-14
Hi,

After two weeks of testing Ubuntu, I decided to go back to Widows XP for a while.  After running the Windows XP installation / recovery disc, Windows XP won't boot, I get a "GRUB error 17" message displayed.
Can someone please give me a very simple explanation for amateurs of what I should do to fix this problem?

Thank you,

Hr_Birnbaum

---

### Post by cariboo on 2009-03-14
If you installed Windows using the Windows install disk, it should have overwrtitten the mbr. You will have to boot from your Windows install CD into the recovery console and run FIXMBR. You may also have to run FIXBOOT.

Jim

---

