---
title: "Convert Nvidia Raid to Linux Raid"
date: 2009-01-12
forum: General Help
---

### Post by ryan00davis on 2009-01-12
I am just about fed up with the nvidia raid and dual booting.  i dont believe the nvidia raid can be managed from inside linux (it needs to boot into windows to rebuild array, etc).

is it possible to convert the nvidia raid to linux raid without deleting the data.  I have about 2TB of data on the array, so backing up and formatting isn't really an option as i do not have the disks to do so.

Thanks for any help,
Ryan

---

### Post by fjgaude on 2009-01-12
I know of no way other than backup your BIOS raid to something, create the raid in software using mdadm and then copy the data over.

Here's a good link to understand software raid under Linux:

[http://linux-raid.osdl.org/index.php/Detecting%2C_querying_and_testing](http://linux-raid.osdl.org/index.php/Detecting%2C_querying_and_testing)

Maybe more than you were after. <smile>

I guess you have tried **dmraid** and have found it wanting?

---

