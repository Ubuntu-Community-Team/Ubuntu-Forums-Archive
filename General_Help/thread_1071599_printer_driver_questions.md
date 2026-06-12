---
title: "printer driver questions"
date: 2009-02-16
forum: General Help
---

### Post by eleach on 2009-02-16
I'm having a hard time finding a answers to:

   How can I find out what printer drivers are present on my system?
 
   How can if find out which driver is currently being used?
 
   How can I select the driver I want the system to use?
 
Thanks

---

### Post by rbmorse on 2009-02-16
To see what printer drivers you have installed on your system, start with 

/usr/share/ppd

that's the location where most printer drivers live.

To select a specific driver to use with your printer, from the upper task bar go to:

system > administration > printing

If your printer is present, right click on the icon and click on properties. The "make and model" line will show which .ppd file is being used. That's the driver. 

To change it click on the button labeled "change" on the "make and model" line.  Point to the .ppd file you want it to use. 

If your printer is not present, click on the "add" button and follow the prompts.

---

### Post by old fert on 2009-02-16
**Thanks for your indirect help, wasn't my question, but i found the answer by following your advice.  ubuntu posted my printer as an ip6700 in one area and dinstalled driver for another similiar unit.  I found it in the database and corrected.  Thanks again.**

---

### Post by eleach on 2009-02-17
That helps.

Thanks.

---

