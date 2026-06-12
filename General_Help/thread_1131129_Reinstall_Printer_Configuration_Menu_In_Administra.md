---
title: "Reinstall Printer Configuration Menu In Administration"
date: 2009-04-20
forum: General Help
---

### Post by centec2b on 2009-04-20
I am running Hardy Heron that was providing printing to printers on windows machines through the CUPS module

I have now managed to destroy my CUPS printer module

I have (I think) managed to reinstall or at least I have one printer working but I cannot see the printer configuration menu in Admin

I have sought help from existing threads but cannot to devise the correct search terms.

I would be very grateful if someone could tell me or point me in the right direction 

A) How to check if my CUPS module is intact
B) How to get the printer administration menu back into admin

Thank you 

a frustrated centec2b

====================================
SOLUTION
====================================

POSTSCRIPT - ahem - the answer of course dear reader is to go to applications and reinstall from there by using add/remove.....

---

### Post by plucky on 2009-04-20
> A) How to check if my CUPS module is intact

Open Firefox and put this in the address bar ```
http://localhost:631/
``` will open the CUPS page.


> B) How to get the printer administration menu back into admin

Right click on **System** and select "Edit Menus".Then select Administration and make sure "Printing" is ticked.

If that doesn't work,open a terminal and input ```
system-config-printer
``` should open the printer configuration page.


Good Luck

---

### Post by centec2b on 2009-04-20
> **plucky said:**
> Open Firefox and put this in the address bar ```
http://localhost:631/
``` will open the CUPS page.
Good Luck

Plucky thanks and respect for the guidance.  That localhost item is stupendous.  I did go to the gui end of the admin menu to see whether I could reinvoke but there was absolutely nothing there so the reinstall worked in this instance

Thank you

centec2b

---

