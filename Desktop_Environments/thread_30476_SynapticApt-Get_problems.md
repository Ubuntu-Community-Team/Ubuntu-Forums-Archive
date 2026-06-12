---
title: "Synaptic/Apt-Get problems"
date: 2005-04-28
forum: Desktop Environments
---

### Post by Runewalsh3 on 2005-04-28
Hey, I have been having problems with Synaptic lately. Any time I try to install any package, Synaptic tells me that the following packages need to be removed:
KDE
KDE-Amusements
KDE-Core
KDE-Extras
kdelibs
By the way, the package I am trying to install is bluefish, an html editor. I used #apt-get check, and it said the following:
```
The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.0-0ubuntu3.1) but 4:3.4.0-0ubuntu3 is  installed
E: Unmet dependencies. Try using -f.

```
Any ideas?

---

### Post by jodef on 2005-04-28
What version of bluefish are you trying to install? 

I just used synaptic to install **bluefish1.0+cvs200502160**(It's in the universe repository.) and installed fine and I am using the same version of kde libs ie 4:3.4.0-0ubuntu3. It's in the universe repository.

---

### Post by az on 2005-04-29
[QUOTE=Runewalsh3]Hey, I have been having problems with Synaptic lately. Any time I try to install any package, Synaptic tells me that the following packages need to be removed:
KDE
KDE-Amusements
KDE-Core
KDE-Extras
kdelibs
By the way, the package I am trying to install is bluefish, an html editor. I used #apt-get check, and it said the following:
```
The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.0-0ubuntu3.1) but 4:3.4.0-0ubuntu3 is  installed
E: Unmet dependencies. Try using -f.

```
Any ideas?[/QUOTE]

Did you use any Breezy repositories?

---

### Post by Runewalsh3 on 2005-04-29
[QUOTE=azz]Did you use any Breezy repositories?[/QUOTE]
I dont believe that I did. Maybe I should just reinstall KDE,  as I dont really use it on a day-to-day basis.

---

### Post by Runewalsh3 on 2005-04-29
[QUOTE=jodef]What version of bluefish are you trying to install? 

I just used synaptic to install **bluefish1.0+cvs200502160**(It's in the universe repository.) and installed fine and I am using the same version of kde libs ie 4:3.4.0-0ubuntu3. It's in the universe repository.[/QUOTE]
I'm not really sure that the version of bluefish has any bearing on the problem, because any time I try to install _anything_, I get the same exact error dialogue.

---

