---
title: "how to: prevent lock screen/screensaver animation using compiz"
date: 2022-01-04
forum: Desktop Environments
---

### Post by Claus7 on 2022-01-04
Hello,

using flashback I noticed that in the latest versions of ubuntu compiz and lock screen/screensaver were not working as they should: the locked screen was using the open animation of compiz every time I tried to login, revealing for some seconds the contents of the desktop, before becoming compact and hiding the desktop and its contents entirely.  

In earlier versions of ubuntu (e.g. 18.04), when typing under window match: ...& !(name=gnome-screensaver), resulted in the exclusion of lock screen from any open animation of compiz, so every time I was trying to login after the screen was locked, there was no display of the contents of my desktop. 

Changing display manager from gdm3 to lightdm did not change anything. I purged the package gnome-screensaver, which, in the latest versions of ubuntu, in its description, said more or less that it was no longer required. I installed xscreensaver and its dependencies and added it in startup applications using the command: xscreensaver -no-splash

And that was it. Even though a slight animation might appear, there is no sight of the contents of desktop. 

Regards!

---

