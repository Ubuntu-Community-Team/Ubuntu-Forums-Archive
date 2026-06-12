---
title: "Doublesided printing"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Kola on 2006-09-09
Hi,

I am running Kubuntu 6.06 with a HP Deskjet 5652 that has doublesided printing.

From the start printing worked ok. When I tried doublesided printing from System Settings - Printer it worked perfectly but when I wanted to change it back to singlesided printing it still prints doublesided.

In the Configure dialog on the printer it says: Double-Sided Printing: <off> but it stills prints doublesided?

I am pretty new to linux so I don't know where to check/edit the configuration so it prints singleside copies again, can someone please help me out?

TIA

---

### Post by masnevets on 2006-09-09
If the program you use lets you put in a command to print (for instance, choosing custom in evince), you want to pass the -o sides=one-sided option to lp.

---

