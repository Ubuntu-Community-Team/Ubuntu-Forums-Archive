---
title: "HP Printer settings ???"
date: 2006-01-11
forum: Desktop Environments
---

### Post by raghu on 2006-01-11
I installed ubuntu newly in my machine... how can I connect my HP 656c series printer which I used to connect when I was using windows (with a driver cd provided by HP no linux driver stuff available in that ....)

Please help me out it is urgent.....

---

### Post by lamego on 2006-01-11
Did you tried a simple add printer and to see if there is a specific driver or a compatible driver available on the list ?

---

### Post by Joey French on 2006-01-11
My hp printer was installed no problem without even lifting a finger. Don't worry, HP printers have great Ubuntu support. Are you sure it is not installed already?

---

### Post by Rollmops on 2006-01-11
I suggest installing the "hplip" package. It includes tools and a GUI for the HP-specific features.

Run "hp-info" and use the given location as the location when adding the printer via the printer-manager of Ubuntu. Make sure you use the printer-driver with "hplip" in the name.

Then the program "hp-toolbox" schows some mor information about the printer status.

Another nice printing tool is "gtklp". You can use this instead of the default "lpr" program. With it you can adjust some more printing features via a GUI.

---

