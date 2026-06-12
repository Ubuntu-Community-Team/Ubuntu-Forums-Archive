---
title: "screenlets"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by sp0onman on 2007-10-26
im having a problem with screenlets which is annoying because i only want to have the widescape weather screenlet. but whenever i try to install it or any other screen let i get this error: Invalid archive. Archive must contain a directory with the screenlet's name. and the archive does have a directory with its name. im running gutsy, used to work in fiesty. 

oh i follwed this guide to install:[http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users](http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users)
edit: none of the screenlets will start, but i can get into the manager.

---

### Post by Forlong on 2007-10-26
> **sp0onman said:**
> im having a problem with screenlets which is annoying because i only want to have the widescape weather screenlet. but whenever i try to install it or any other screen let i get this error: Invalid archive. Archive must contain a directory with the screenlet's name. and the archive does have a directory with its name.
It appears that the Screenlet you are trying to install is out of date.
You can do it manually, though.
Just unpack it and move the Screenlets' folder to **/usr/local/share/screenlets** (you presumably need to be root to do that) or **~/.screenlets** (that's a hidden folder in your home folder).

---

### Post by lanchongzi on 2007-12-12
I Have exactly the same problem
and when I copy the extracted files to either one of the above mentioned folders the screenlet manager won't start anymore

?????????

what now?

is there a fix? i spent like 3 hours trying to figure this out with no success what so ever

---

### Post by lanchongzi on 2007-12-13
solved my problems by overriding the screenlet-0.0.10 with screenlet-0.0.7

---

