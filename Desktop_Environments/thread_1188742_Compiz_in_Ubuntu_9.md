---
title: "Compiz in Ubuntu 9"
date: 2009-06-16
forum: Desktop Environments
---

### Post by Zero++ on 2009-06-16
Does any one know how to get Compiz to load at startup? Their website says to go to System, preferences, and desktop effects. My Preferences Menu does not have a Desktop Effects Option. Any help would be appreciated!

---

### Post by ciprian.topala on 2009-06-16
have you tried installing compizconfig-settings-manager package and then go to system->preferences->compizconfig settings manager to choose the effects you want?

---

### Post by techstop on 2009-06-16
> **Zero++ said:**
> Does any one know how to get Compiz to load at startup? Their website says to go to System, preferences, and desktop effects. My Preferences Menu does not have a Desktop Effects Option. Any help would be appreciated!

You're looking in the wrong location. The menu you need is;

System>Appearance>Visual Effects

---

### Post by mgbowe1 on 2009-06-16
if you have the compiz settings manager just check the load on startup button in the general>general options tab.

---

### Post by Zero++ on 2009-06-16
> **ciprian.topala said:**
> have you tried installing compizconfig-settings-manager package and then go to system->preferences->compizconfig settings manager to choose the effects you want?

I can set effects I just have to reload the window manager after I start up in order to get them to work

---

### Post by Zero++ on 2009-06-16
> **techstop said:**
> You're looking in the wrong location. The menu you need is;

System>Appearance>Visual Effects

I have enabled Extra effects but I still have to reload the windows manager on startup to get it to work

---

### Post by Zero++ on 2009-06-16
> **mgbowe1 said:**
> if you have the compiz settings manager just check the load on startup button in the general>general options tab.

My general options tab does not have that option

---

### Post by Viva on 2009-06-16
Install fusion-icon and add it to start up.

---

### Post by Zero++ on 2009-06-16
Thanks for the suggestions but none have allowed me to load all of my desktop effects at startup. I still have to reload the windows manager every time the computer starts up. Is there a command to reload the windows manager I could put in my startup file? Any other suggestions?

---

### Post by mgbowe1 on 2009-06-16
> **Zero++ said:**
> My general options tab does not have that option
it's in general>general options and then you need to look in all the tabs that are brought up by double clicking general options.

---

### Post by Zero++ on 2009-06-16
> **Viva said:**
> Install fusion-icon and add it to start up.
Already did still no help. Thanks though

---

### Post by Zero++ on 2009-06-19
Fixed it! All I had to do was add the Compiz Command to my startup list (under system and preferences if anyone runs into the same problem) and problem solved! I was using the CCSM command before with less than ideal results! Thanks for all the tips and ideas turns out I'm just a noob!

---

