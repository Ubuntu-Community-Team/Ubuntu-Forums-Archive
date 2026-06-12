---
title: "Print jobs are huge ~700MB for 7 copies of a 3.5M PDF"
date: 2008-12-28
forum: General Help
---

### Post by JonnyRo on 2008-12-28
Hi,

I am using a HP LaserJet 4600 over jetdirect.  It takes FOREVER to print some PDF files, and one in particular weighing in at 3.5M takes almost 5 minutes to print one page.  

I looked at the CUPS queue and 7 copies of this PDF weigh in at a 525MB print job size.  

How could the print job be so big?  I tried looking for a resolution setting in CUPS, in case the printer was running at some insanely high resolution, but i was unable to find such a setting.

Any tips would be greatly appreciated,

Jonathan

---

### Post by dcstar on 2008-12-28
> **JonnyRo said:**
> Hi,

I am using a HP LaserJet 4600 over jetdirect.  It takes FOREVER to print some PDF files, and one in particular weighing in at 3.5M takes almost 5 minutes to print one page.  

I looked at the CUPS queue and 7 copies of this PDF weigh in at a 525MB print job size.  

How could the print job be so big?  I tried looking for a resolution setting in CUPS, in case the printer was running at some insanely high resolution, but i was unable to find such a setting.

Any tips would be greatly appreciated,

Jonathan

Are you printing in Postscript or PJL?, Postscript can generate very (very) large print jobs.

---

### Post by darreld on 2008-12-31
> **dcstar said:**
> Are you printing in Postscript or PJL?, Postscript can generate very (very) large print jobs.

How would he know that?  I am having the same problem printing PDF's to my Brother 7820N (which 8.10 found perfectly).  It is extremely slow and eventually I get an error on the printer.  Everything else has printed fine.  Same PDF's print to the same printer immediately on my Mac.

-darrel

---

