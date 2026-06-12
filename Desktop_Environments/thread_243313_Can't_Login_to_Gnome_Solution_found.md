---
title: "Can't Login to Gnome: Solution found"
date: 2006-08-24
forum: Desktop Environments
---

### Post by jazzfish on 2006-08-24
:)  Greetings,

I previously posted that after updating from Breezy to Dapper through the live upgrade process I could not log into the Gnome desktop. What would happen was that the graphical login screen would come up fine, but when I entered a valid username/password combo the desktop would appear to be starting up - but then the screen would go dark for a few seconds and the login screen would come back again.  This repeated indefinitely. 

Figuring the obvious - it had something to do with Gnome desktop (dah)  I  decided to reinstall the Gnome desktop.  

I used the aptitude package manager from the console to downgrade the Gnome installation to an earlier version.  When I closed the console and went back to login - voila - it worked.  

Then I thought the newest package was OK but the earlier installation was corrupt. So I upgraded (again) to the newest version.  Even though that was the same version that had been installed before and had the problem, when I did the upgrade - voila again - ... it still worked..  so Dapper is finally starting to live up to it's name and is lookin good!!

BTW Aptitude is pretty cool for a console application!

Thanks to those who responded to me. Even though it wasn't the buggy X installation I appreciate the efforts.   :cool: 

- Bob

---

