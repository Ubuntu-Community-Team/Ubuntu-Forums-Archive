---
title: "Reset my user profile ??"
date: 2005-12-27
forum: Desktop Environments
---

### Post by CHUCKYCHUCK on 2005-12-27
Hi !
Some time ago, i had several themes bugs with my gnome session ( for example grey colors with my milk theme, some buttons disappeared ..... ), i think it was because i tweaked my configs files too much ...
then i deleted my gnome, nautilus and gconf config files and all the packages installed by the kubuntu-desktop metapackage, all went back to normal

but i just réinstalled today the kubuntu-desktop, and then all those bugs just came back ........
i'd like to Totally reset my profile, just as if i created a new one, so here is my question : could i securely delete All the config files in my home dir ( absolutely all the config files ) ?? or will this even prevent me my from logging into gnome ??

p.s.  i sure those bugs are profile-related, as they do not appear in the root profile ( ex: no theme bugs with graphics apps launched in root )

thanks

---

### Post by amohanty on 2005-12-28
Everything except .Xauthority and .ICEauthority (I think you can even delete this one - but just to be on the safe side) can be deleted. 

WARNING: You will lose _all_ and I mean _all_ you application preferences.

AM

---

