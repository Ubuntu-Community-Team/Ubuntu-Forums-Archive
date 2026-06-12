---
title: "[SOLVED] Use Metacity with Gutsy"
date: 2008-02-19
forum: Desktop Environments
---

### Post by Bruce M. on 2008-02-19
I have Compiz turned off:
[LIST]
[*]System>Preferences>Appearance
[*]Visual Effects: None
[/LIST]
However Compiz is still my "*window manager*" *See attached.*

And I think it's stopping my conky from displaying automatically at startup.
Keep in mind I have an OLD computer (P-III 800MHtz - 512MB RAM, sound and video built in to the motherboard)

So two questions:
[LIST=1]
[*]What damage will it to to Gutsy if, through Synaptic, I "Mark for Complete Removal" everything "Compiz"?
[*]How do I go about making **Metacity** my **"Default"** window manager?
[/LIST]

***Note:*** Metacity is installed, just not running I think. :confused:

Thanks
Bruce

**EDIT:  This should be jailed, there are two threads of the same name, don't know how it happened.**

---

### Post by Perpetual on 2008-02-20
If you go to Sessions does it show compiz set to start at boot?  If so, can you go to properties of the compiz session and change it from compiz --replace to metacity --replace?

---

### Post by Bruce M. on 2008-02-22
> **Perpetual said:**
> If you go to Sessions does it show compiz set to start at boot?  If so, can you go to properties of the compiz session and change it from compiz --replace to metacity --replace?

Sessions showed compiz even after doing a metacity --replace.
Properties of the Compiz Session?

I went to Configuration Editor and set metacity as default there.  That seemed to work :)

---

