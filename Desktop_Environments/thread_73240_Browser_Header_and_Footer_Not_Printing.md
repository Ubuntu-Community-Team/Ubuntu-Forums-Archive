---
title: "Browser Header and Footer Not Printing"
date: 2005-10-08
forum: Desktop Environments
---

### Post by wacole on 2005-10-08
I'm using Firefox 1.0.6 and Mozilla 1.7.12.  In both cases when printing to my inkjet [a Canon S600 using the Turboprint driver], neither the header nor footer prints.  I've looked at System|Administration|Printing and checked the properties for the S600, but don't see anything that could be an adjustment that might fix this.  There appears, also, to be nothing in the Turboprint Configuration tool that addresses this.

Would be very grateful for clues.  Thank you very much.

---

### Post by wacole on 2005-10-10
OK, figured it out.

BTW I use the Turboprint drivers for my Canon S600 ... that may make the difference.

First, _in Firefox_, do File|Print.
Then click on the Properties button located on the Printer line.
In the area of Printer Properties labled "Gap from edge of paper to Margin (inches),enter these settings:
    Top 0.12
    Bottom 0.25
    Left 0.25
    Right 0.04 (the default)
Click OK

and, voila, the headers and footers for a web page printed using 1.0.3 Firefox print just fine.

---

