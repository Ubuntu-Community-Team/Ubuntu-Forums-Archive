---
title: "Multiple spellchecking languages in Firefox"
date: 2013-08-09
forum: Desktop Environments
---

### Post by zelenij-krokodil on 2013-08-09
Hi everyone,

I have a recent version of Firefox running on Ubuntu 13.04.  Since I added Spanish dictionary to it, the situation with spellchecking started getting out of hand.  For some reason Firefox insists on listing all possible locales in the list of available languages to spell check.  For instance, there is English US, UK, SA, Australia etc.  The situation with Spanish is even worse - all of South America tries to squeeze into my small Firefox context submenu (here you are welcome to look at the attached screenshot).  So, the question is - do you know how this list can be trimmed down only to the locales I'm really interested in?  I would like to see, say, only English UK and Spanish Spain.
 
Thanks!


[ATTACH=CONFIG]245219[/ATTACH]

---

### Post by whoey on 2013-09-05
I also have this issue, but also the default spell check language keeps reseting to es-ES even after changing it in about:config to en-US.

To remove languages I deleted all from /usr/lib/firefox/dictionaries in a terminal, and installed the ones I actually wanted inside the Tools > Addons > Dictionaries section of Firefox.

---

### Post by zelenij-krokodil on 2013-09-07
Thanks, that make sence and I should have thought about it myself.  I am still eager to see a bit less hacky way to achieve that.

---

