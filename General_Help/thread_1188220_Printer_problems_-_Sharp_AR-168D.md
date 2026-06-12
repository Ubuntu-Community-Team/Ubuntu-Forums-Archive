---
title: "Printer problems - Sharp AR-168D"
date: 2009-06-15
forum: General Help
---

### Post by cpeiffler on 2009-06-15
Just installed 9.04 at work. None of the drivers are that are provided through CUPS works. I'll print a test page and it'll finish the job without actually printing.... ahhh! Bosses heat is on me so I need help ASAP! I have a Sharp AR-168d connected to a dell, when printing the status register that it's working when using the default driver provided through openprinting, the other drivers register a "Failed" or "Busy" message.

---

### Post by cpeiffler on 2009-06-15
Also after rebooting the printer and computers, recognizing and installing the printer I sometimes get the message under the document status that the printer may not be connected at all.

---

### Post by todak on 2009-06-15
You need a manufacturer supplied PPD file. It can be downloaded from here: [http://openprinting.org/show_driver.cgi?driver=Postscript-Sharp&fromprinter=Sharp-AR-168D](http://openprinting.org/show_driver.cgi?driver=Postscript-Sharp&fromprinter=Sharp-AR-168D) In the grey box, select the file for **20081112 (DEB for LSB 3.2)**.

---

### Post by cpeiffler on 2009-06-15
That's one of the first places I investigated to try to problem solve this but after it installed it to the the opt folder, it will show me that that printer is busy and will retry in 5 seconds... minutes later I cancel the job. What I get installing the PPD is server-error-internal-error

---

### Post by cpeiffler on 2009-06-15
What I get installing the PPD is server-error-internal-error

---

### Post by wpshooter on 2009-06-15
Are you attempting to add the printer thru System/Administration/Printing and then selecting "New" and then following the provided prompts including selecting your printer manufacturer from the menu and then selecting your particular model from the next menu and then subsequently selecting the driver for that model from the provided listing of drivers ?

When I go thru the above process, there are 2 driver choices offered for the model AR-168D.  The first one is listed as recommended and the second one is listed as a postscript driver.

---

### Post by cpeiffler on 2009-06-15
There are actually three drivers listed. One from opendriver, 1.1... and i forget the other one. Trying all of them and the generic ones end I get zip...

---

### Post by wpshooter on 2009-06-15
> **cpeiffler said:**
> There are actually three drivers listed. One from opendriver, 1.1... and i forget the other one. Trying all of them and the generic ones end I get zip...

Then I would report this as a bug.

---

### Post by cpeiffler on 2009-06-16
Thing is the printer was fine under Windows... i think i'll end up switching it back. Bummer, the Linux experiment is over.

---

