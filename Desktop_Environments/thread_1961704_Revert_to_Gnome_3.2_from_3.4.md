---
title: "Revert to Gnome 3.2 from 3.4"
date: 2012-04-19
forum: Desktop Environments
---

### Post by dwitkin on 2012-04-19
Today I upgraded from Gnome shell 3.2 to 3.4 in the hopes it would be more stable. Unfortunately, several Gnome Shell extensions that are "must have" for me worked perfectly in Gnome 3.2 but appear to be incompatible with Gnome 3.4. So, I'm hoping someone can give me step-by-step instructions to revert back to Gnome 3.2.

Your help is appreciated...

---

### Post by Frogs Hair on 2012-04-19
Remove the Gnome Shell from the software center. If you upgraded using a PPA you must remove the software source before reinstalling or 3.4 will be reinstalled.  
 
Software sources can be accessed though update manager > settings other software. Remove the _lines_ with the PPA repository information and run check for updates to reload the software information. 

Install the Gnome Shell from the software center . With the source removed you will have 3.2 back.

Part of the problem may be that 3.2 extensions are not compatible 3.4 but they can be installed after removing all the 3.2 extensions. 

 12.04 will come with the Gnome shell 3.4 .

---

### Post by dwitkin on 2012-04-20
> **Frogs Hair said:**
> Remove the Gnome Shell from the software center. If you upgraded using a PPA you must remove the software source before reinstalling or 3.4 will be reinstalled.  
 
Software sources can be accessed though update manager > settings other software. Remove the _lines_ with the PPA repository information and run check for updates to reload the software information. 

Install the Gnome Shell from the software center . With the source removed you will have 3.2 back.

Part of the problem may be that 3.2 extensions are not compatible 3.4 but they can be installed after removing all the 3.2 extensions. 

 12.04 will come with the Gnome shell 3.4 .
Great. Thanks. I'll try that.

---

