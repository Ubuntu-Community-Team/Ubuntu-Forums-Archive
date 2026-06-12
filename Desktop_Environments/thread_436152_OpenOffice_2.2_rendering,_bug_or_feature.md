---
title: "OpenOffice 2.2 rendering, bug or feature?"
date: 2007-05-07
forum: Desktop Environments
---

### Post by mcframe on 2007-05-07
I recently upgraded to Kubuntu 7.04 to find that font rendering in OO2.2 terribly bad. 
This is the same document in edgy and feisty. 

The document in edgy:[IMG]http://web.utanet.at/hhackenb/OO2.0edgy.png[/IMG]
Same doc in feisty:[IMG]http://web.utanet.at/hhackenb/OO2.2feisty.png[/IMG]

Before i drop a bug report, does anyone have a solution?

---

### Post by jamespetts on 2007-05-07
Do you have the same problem with different fonts, or just Optima?

---

### Post by mcframe on 2007-05-07
> **jamespetts said:**
> Do you have the same problem with different fonts, or just Optima?
Some fonts appear in a  somehow reduced quality (no matter if anitaliasing is enabled or not) , although Optima looks worst.

---

### Post by aidanr on 2007-05-07
i think you need to install openoffice.org-kde, i had to install openoffice.org-gtk on xubuntu, because without it it looked like that

---

### Post by mcframe on 2007-05-08
> **aidanr said:**
> i think you need to install openoffice.org-kde, i had to install openoffice.org-gtk on xubuntu, because without it it looked like that
Thanks for this hint, but I had openoffice.org-kde installed. 
It appears to me that the overall dpi of openoffice is greater than it was under edgy. Using the same OO configuration folder it's clear to see that the same font size in the same zoom level is rendered much bigger than in edgy. 
Unfortunately I have no clue what could be responsible for this.

---

### Post by Ramses on 2007-05-08
Try to move old open office configuration from your home folder to some other folder and let open office start without any old configuration files.

---

### Post by mcframe on 2007-05-08
> **Ramses said:**
> Try to move old open office configuration from your home folder to some other folder and let open office start without any old configuration files.
THX for the tip: I did it but it makes no difference. :(

---

### Post by Hagar Delest on 2007-05-09
You can try the manual upgrade instead of the Ubuntu version :
See this thread : [ HOWTO: Install OpenOffice.org 2.2 on Ubuntu 6.10]("http://ubuntuforums.org/showthread.php?t=398074")
Or this one : [http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370](http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370).

---

### Post by mcframe on 2007-05-09
I now managed to change the screen resolution (used by gtk programs) by adding ```
DisplaySize 336 210
``` to the monitor section of xorg.conf and adding a dpi setting to kdmrc.
The user interface of OpenOffice now looks te same as in edgy unfortunately the terribly bad font rendering remains.

---

