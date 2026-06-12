---
title: "Prevent one user from graphical login (only login via ssh)"
date: 2011-10-27
forum: Desktop Environments
---

### Post by DennyBeach on 2011-10-27
I am running Ubuntu 11.10 desktop.
 
I have a special user account that runs a custom program as a default shell.  That username needs to login via SSH to run the custom program which exits after the information is displayed.  This part works great.
 
However, I do not want this username to be able to get a GDM desktop.   I want for this username to only be able to login with SSH or to a command prompt.
 
Is there a way to do this while allowing other users to login normally to their GUI desktops?
 
Thank you.

---

### Post by DennyBeach on 2011-10-27
I did find one working method on my own:
 
"rm -r" the user's home folder, then create a new one and set its permissions to "d--x------". The user can successfully authenticate in the GDM login, but the desktop fails to load and brings back the login screen.
 
I'd like to think there is a cleaner way of doing this though.

---

