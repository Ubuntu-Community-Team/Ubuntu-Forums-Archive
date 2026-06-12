---
title: "Formatting SD card in Ubuntu"
date: 2009-05-26
forum: General Help
---

### Post by RevRogue on 2009-05-26
Currently I am running Intrepid Ibex x64.
I need to format the Sd card for my phone but gpart will not show the media card although it is as being mounted as /media/disk, fdisk tells me 

```
last_lba(): I don't know how to handle files with mode 40700
You will not be able to write the partition table.

```

Any kind of help would be greatly appreciated.

---

### Post by dpsleep on 2009-05-26
try re-pluging it in and post the output of "dmesg | tail"

---

### Post by RevRogue on 2009-05-26
[177107.132934] ACPI: Unable to turn cooling device [f6c2af18] 'on'
[177113.132935] ACPI: Unable to turn cooling device [f6c2af18] 'on'
[177119.132963] ACPI: Unable to turn cooling device [f6c2af18] 'on'
[177125.132929] ACPI: Unable to turn cooling device [f6c2af18] 'on'
[177131.132916] ACPI: Unable to turn cooling device [f6c2af18] 'on'
[177137.132946] ACPI: Unable to turn cooling device [f6c2af18] 'on'
[177143.132927] ACPI: Unable to turn cooling device [f6c2af18] 'on'
[177149.132938] ACPI: Unable to turn cooling device [f6c2af18] 'on'
[177155.134452] ACPI: Unable to turn cooling device [f6c2af18] 'on'
[177161.132939] ACPI: Unable to turn cooling device [f6c2af18] 'on'


not sure how that helps but hey, this is what I get

---

