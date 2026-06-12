---
title: "Plextor DVD Burner"
date: 2005-11-03
forum: Desktop Environments
---

### Post by sjpritch25 on 2005-11-03
I used this drive to install Ubuntu, however, its not being recognized by breezy badger.  I have a second drive "which is just a DVD drive and its connected through PATA cable" and that drive is fine, however my Plextor is SATA.  I don't know what to do to make my drive be recognized by linux.  Any Help would be great.

---

### Post by jamieson on 2005-11-03
Same problem here.  I've tried editing libata.h to add support for ATAPI, then compiled the kernel.  No change.  It's not finding the Plextor SATA DVD drive at all.  

Some folks have said that there's a conflict with the IDE drivers, but as if yet I've not found a way to disable any of that stuff.  

About ready to take that new drive back and get the PATA version... but I'd really like to figure this out.  Someone out there must have been able to get this to work.

---

