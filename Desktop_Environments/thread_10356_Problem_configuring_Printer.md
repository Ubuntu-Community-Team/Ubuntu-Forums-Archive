---
title: "Problem configuring Printer"
date: 2005-01-07
forum: Desktop Environments
---

### Post by parrot on 2005-01-07
When I attempt to configure my printer, I get the error message:
“The CUPS server could not be contacted.”
Does anyone have an inkling as to how to fix this? Thanx.

---

### Post by hardcandy on 2005-01-07
The first thing to do is "sudo /etc/init.d/cupsys restart" to make sure the cups deamon is running.

---

