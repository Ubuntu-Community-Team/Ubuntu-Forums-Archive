---
title: "how to control which services &amp; programs start up on boot in Kubuntu"
date: 2007-08-04
forum: Desktop Environments
---

### Post by cyneuron on 2007-08-04
hello there

i want to control which things start on boot.

for example, common unix printer, and hp printer start on boot.

also when i saw processes n Ksysguard, katapult bluetooth were also there. 

is there any software which may allow to customize startup services and programs ?

i have seen in forum, few guides regarding this. but they seem to follow a very complex procedure. isnt there any simple softwarw which may do the same..

---

### Post by Beernut on 2007-08-04
Open a terminal and type ```
kcontrol
```

Then select KDE Components > Autostart Applications

Not sure if this is what you are looking for or not.  Wonder why kControl isn't a menu item by default.

For services go to System Settings > Advanced > System Services

---

### Post by Aathos on 2007-08-04
I have been trying to do the same thing, but there is no >Autostart Applications in KControl.  I installed kde-core, not kubuntu-desktop, so maybe there is additional package that I need to install?

---

### Post by Vince4Amy on 2007-08-04
Use the System Settings on the K-Menu on Kubuntu & click Advanced.

---

