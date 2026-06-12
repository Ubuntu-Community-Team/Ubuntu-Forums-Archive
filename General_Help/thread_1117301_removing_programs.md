---
title: "removing programs"
date: 2009-04-05
forum: General Help
---

### Post by mikeonthebeach on 2009-04-05
how does one delete programs for ubuntu 8.10

---

### Post by _Purple_ on 2009-04-05
```
sudo apt-get remove Package_name
```

---

### Post by ShaunG on 2009-04-05
In add/remove programs search for the program then choose to remove it.

Or in Synaptics you can search for the program, right cick then choose mark for removal/complete removal. The click apply up the top

Or from the command line:

```
sudo apt-get remove <program name>
```

---

### Post by vegetarianshrimp on 2009-04-05
Hmm...It depends. If you added them through the Add/Remove in the Applications menu, then all you have to do is uncheck the little checkbox next to the program, and press apply. If you downloaded the deb, you have to go to Synaptic Package Manger, click on status, click on Installed (local or obsolete) and uninstall the package. I'm not sure what to do if you compiled it from source (maybe the same thing as debs?)

---

