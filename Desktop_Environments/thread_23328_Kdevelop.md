---
title: "Kdevelop"
date: 2005-04-01
forum: Desktop Environments
---

### Post by superhac007 on 2005-04-01
It seems that KDevelop is no longer working after I did a system update.  I keep getting a popup window stating that, "Unable to find plugins, Kdevelop will not work properly!".  Any one seen this before?

Thanks.

---

### Post by superhac007 on 2005-04-04
This fixes the problem... Run the following from your shell:

$ kbuildsycoca

If you get an error message about a locked file delete the file as root.. it will be in the tmp dir if this happens.  Then re-execute the command above.

Now you can run kdevelop and it should find the plugins:

$ kdevelop3


L8ter...

---

### Post by !nkubus on 2005-06-14
Thank you it resolve my problem :)

---

