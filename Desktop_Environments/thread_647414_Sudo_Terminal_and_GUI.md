---
title: "Sudo Terminal and GUI"
date: 2007-12-22
forum: Desktop Environments
---

### Post by visionthing on 2007-12-22
Only been using Ubuntu for a few weeks so perhaps this already exsists....

I find sudo security a little confusing.

For instance, I can install ClamAV ( just one of many examples ) through apps Add/Remove. Prompts me for password and installs. After if I try to launch the application that is no problem. But try to update the virus def's etc it won't allow me. So I am back to terminal and getting lost.

Is there no way to have something like Windows Run As Command. Shift and Right click on the something in the menu , Have like a run as sudo which prompts the password and continues.

Just a thought. 

thanks

---

### Post by jken146 on 2007-12-22
If you prefix a command with **gksudo** you can run a gui application with root privileges.  This is not recommended for most programs most of the time.  Are you sure you need an anti-virus program anyway?

---

### Post by vanadium on 2007-12-22
The "run as" command of Windows in fact was inspired by the "sudo" or "gksudo" commands. "gksudo" deffers from sudo in that it "graphically" asks the pasword.

---

### Post by aysiu on 2007-12-22
> **jken146 said:**
> Are you sure you need an anti-virus program anyway? Unless the OP is running Ubuntu as a mail server, then, no.

---

### Post by visionthing on 2007-12-22
Thanks. Clamav was just an example. I would just love to see it usable even without an Terminal interface. At least for regular users. 

Work PC's will have to run Anti Virus anyway, needed or not, at least if they store or process credit card data. Its one of the many stipulations of PCI compliance.

---

### Post by aysiu on 2007-12-22
Well, as jken145 mentioned, there is always *gksudo*, which allows you a password prompt without having to use the terminal.

---

