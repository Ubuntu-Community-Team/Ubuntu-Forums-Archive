---
title: "shortcut to Active Jobs .desktop"
date: 2022-03-20
forum: Desktop Environments
---

### Post by luusac on 2022-03-20
I am looking for a .desktop file for gnome, similar to /usr/share/applications/system-config-printer.desktop to display the Active Jobs dialog for the default printer.  The closest I have got is the system-config-printer.desktop which then requires the x Job(s) button be clicked to display the active jobs for the printer.  I am using 18.04.6 LTS, thanks

---

### Post by deadflowr on 2022-03-21
You can add the --show-jobs option to the system-config-printer command in a custom .desktop file,
but it needs the printer name like
```
system-config-printer --show-jobs Canon-something-123
```
or whatever the name is.
If you have multiple printers, you could set up desktop files for each.

use something like ```
lpstat -t
``` for getting the proper printer name.

---

### Post by luusac on 2022-03-22
Thanks, that did the job.  It does display a different dialog for the print queue than Printers -> x Job(s) though - Document Print Status instead of Active Jobs.
So what would the alternative of 
Exec=system-config-printer --show-jobs name-of-printer
be in the style of:
Exec=gnome-control-centre printers
Also, it is possible to call the print queue dialog directly without specifying the name of the printer, instead using a reference to whatever the default printer is?
many thanks

---

