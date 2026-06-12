---
title: "my FireFox Browser Crashed, Help!"
date: 2009-03-26
forum: General Help
---

### Post by The Moorish on 2009-03-26
Hello!  a severe vulnerability have been discovered a couple 
days ago effecting firefox browser , i have mistakenly opened an
affected website  , and now my browser doesn't work anymore, 
please let me know what should i do to get it back?


ps: now i am using ie for Linux.

---

### Post by thehipho on 2009-03-26
You could try this to get firefox working again.

Open a terminal and type:  firefox -ProfileManager

If you see the Profile Manager you could then create a different profile,
and import your bookmarks and settings over to the new profile.

Hope that helps you!

---

### Post by The Moorish on 2009-03-26
> **thehipho said:**
> You could try this to get firefox working again.

Open a terminal and type:  firefox -ProfileManager

If you see the Profile Manager you could then create a different profile,
and import your bookmarks and settings over to the new profile.

Hope that helps you!

Thank you thehipho for your quick reply

i have tried :~$ firefox -ProfileManager
  this is what i get :
Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*.

---

### Post by thehipho on 2009-03-26
Here you go found this after doing a quick google search.

You could give it a try:

sudo  xulrunner-1.9 --register-global

---

### Post by The Moorish on 2009-03-26
> **thehipho said:**
> Here you go found this after doing a quick google search.

You could give it a try:

sudo  xulrunner-1.9 --register-global

Problem solved!:lolflag:

its up and running again!

Firefox need a security update because the vulnerability is in the wild!

again Thank you so much thehipho ,i really really appreciate your help!

---

### Post by thehipho on 2009-03-26
Good, don't want to be without ff & gg, hehe.

---

### Post by The Moorish on 2009-03-26
> **thehipho said:**
> Good, don't want to be without ff & gg, hehe.

i agree ,hehe

---

