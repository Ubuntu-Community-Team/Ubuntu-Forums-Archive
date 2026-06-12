---
title: "Hibernate in Dell Latitude"
date: 2005-07-16
forum: Desktop Environments
---

### Post by WolfJay_83 on 2005-07-16
My laptop will shutdown when selected to "Hibernate the computer" from "Log Out."  But when it resumes, it locks.  The screen displayed is (aprox) as follows.

---------------------------------------------------------------------------------------------------------------
Stopping tasks-------------------
Freeing memory... done (22757 pages freed)
resume - options hould be used to set suspend device .... swsusp:
Need to copy 8269 pages

[6]ACPI: PCI interrupt 0000:00:0d.0[A]->
GSI 9(level, low) ->IRQ 9
ACPI:PCI interrupt 0000:01:00.1[B] -> GSI 10 (level, low)-> IRQ 10
----------------------------------------------------------------------------------------------------------------

after this it locks.  Hibernate/Suspend to disk worked alright in Knoppix and XP.
I tried calling < sudo APM -S > but it said  "No APM support in kernal"
Any Ideas?

Thanks,
Jason

Using:
Dell Latitude LS
P300
128mb Ram, 12Gb HD

---

