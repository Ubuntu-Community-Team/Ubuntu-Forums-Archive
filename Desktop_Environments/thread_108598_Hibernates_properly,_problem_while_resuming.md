---
title: "Hibernates properly, problem while resuming"
date: 2005-12-26
forum: Desktop Environments
---

### Post by harisund on 2005-12-26
This is what happens when resuming from hibernation: 

Freeing memory ... done (29156 pages freed)
Error evaluating _GTM
IDE device ACPI handler is NULL.

ACPI: PCI interrupt for device 0000:02:0f.1 disabled
ACPI: PCI interrupt for device 0000:02:0f.0 disabled
ACPI: PCI interrupt for device 0000:02:03.0 disabled
resume= option should be used to set suspend deviceswsusp: Need to copy 27818 pages
swsusp: Restoring highmem


Any ides? 

Thanks !

---

### Post by fermulator on 2006-02-06
Interesting...I have the same issue.

No one else has any idea on this one?

Looks like ubuntu locks up right after (or during) the stage of "Restoring Highmem".

My hardware:
Dell Latitude CPi A-Series

---

### Post by harisund on 2006-02-06
Indeed, I too have a Dell Latitude C800.. close to yours I presume..

---

### Post by fermulator on 2006-02-11
Think it's related to this kernel issue?

[http://www.ubuntuforums.org/showthread.php?p=711815#post711815](http://www.ubuntuforums.org/showthread.php?p=711815#post711815)

---

