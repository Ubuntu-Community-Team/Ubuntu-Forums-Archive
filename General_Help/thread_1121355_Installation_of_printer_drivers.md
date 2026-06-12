---
title: "Installation of printer drivers"
date: 2009-04-09
forum: General Help
---

### Post by zoomiest on 2009-04-09
I am just building a print server, (Samsung ML-4500), and I need to install the driver on the server... the readme says to execute the install.sh script...  

I have tried  
./setup.sh  
../setup.sh

but all I get is:
```
cannot open shared object file: No such file or directory
```

any suggestions?

---

### Post by mb_webguy on 2009-04-10
That driver is already installed on my system.  Have you tried adding it using System->Administration->Printing, using the "Select printer from database" option?

---

### Post by zoomiest on 2009-04-10
This where I am in new territory...
Does the printer driver need to be installed on the print server? (or just CUPS?)

Perhaps just the client work stations need the driver... please teach me.

I can't execute your suggestion above, because I am in a command line environment, on the print server.

---

### Post by mb_webguy on 2009-04-10
If you have installed CUPS, then the printer should be already supported.  The drivers for all but the newest printers are included in the CUPS installation.  (This is assuming you install all of the packages that CUPS suggests and recommends.)

To make it easier for yourself, you may want to consider installing some sort of graphical environment like the Openbox window manager, and a few configuration utilities, such as system-config-printer.  Once you have the print server is configured, you can remove Openbox or simply run the printer using a text-only session.

---

