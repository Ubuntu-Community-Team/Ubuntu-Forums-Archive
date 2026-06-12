---
title: "Can't Download Updates"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Miniberger on 2006-09-05
Whenever I try to open the update manager, I get the following error message: "Only one software management tool is allowed to run at the same time" I did not have any other management tool open nor was I using the terminal. I restarted and the same thing happened.

When I open Synaptic, it says this:"Error: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." I then click ok and it functions as normal.

Is the error in Synaptic related to the one in the update manager?

Why won't the update manager run?

---

### Post by ciscosurfer on 2006-09-05
The last time you updated, did you quit the update or did your machine crash or halt?  You usually get that error when packages haven't been fully configured.  Did you run```
sudo dpkg --configure -a
```to finish configuring any packages that hadn't completed?  Try this, and then use the Update Manager again to see if any errors pop up again.

---

### Post by Miniberger on 2006-09-05
Indeed, there was a package (j2se 1.4) that had not been fully configured. It required documentation to be downloaded to fully configure it, and a link was provided in the terminal. I got the documentation, fully configured j2se 1.4 and now everything is working smoothly.

Thanks for all the help.

---

### Post by ciscosurfer on 2006-09-05
Any time!

---

