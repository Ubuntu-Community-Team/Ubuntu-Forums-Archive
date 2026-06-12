---
title: "Samsung ML-4500 problems"
date: 2006-06-02
forum: Desktop Environments
---

### Post by garethppls on 2006-06-02
Since the printer CUPS files were updated this GDI printer will no longer print properly and keeps stalling.

One thing I noticed in the gnome-cups-manager (i fixed it yay) was 
Ready: No %%BoundingBox: comment in header!

what does this mean and has anyone found a solution as its really annoying me as I need this as a file server

worked in Dapper Flight 6 + 7 before the main release

---

### Post by garethppls on 2006-06-02
Ready: Unable to lookup host 'parallel' - No address associated with name

now it says this :S I really need this as a print server :(

---

### Post by malakoffee on 2006-06-22
[QUOTE=garethppls]Ready: Unable to lookup host 'parallel' - No address associated with name

now it says this :S I really need this as a print server :([/QUOTE]

Same situation for me here on Dapper : ML-4500 will not print

Admin : Printer : ML-4500 Properties shows message in Status ::
**Printing: Unable to lookup host 'parallel' - Unknown host**

I note that the printer setup facility will only let me setup as a CUPS network printer to lp0.
It will NOT let me setup a a local printer . . . it says "No printers detected"

In the /var/log/cups/error_log I have your previously reported message "No %%BoundingBox: comment in header!", but there is other stuff too . . .. 
**cupsdAuthorize: Local authentication certificate not found!**

It would be nice to have a diagnosic procedure for this printing problem 

Thanks 
Malakoff

---

