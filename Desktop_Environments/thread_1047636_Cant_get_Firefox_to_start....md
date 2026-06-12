---
title: "Cant get Firefox to start..."
date: 2009-01-22
forum: Desktop Environments
---

### Post by jevan027 on 2009-01-22
So I just recently decided to give Ubuntu a try... I had been having no problems until I decided to go ahead and install the >200 updates since its release. Apparently something happened while I was away from my computer and I had to do a hard restart...now firefox wont properly load.

When I type Firefox into the terminal it returns:
"Could not find compatible GRE between versions 1.9.0.1 and 1.9.0.*"

When I try to install the remaining 100 or so updates I get the error telling me to correct the problem using the dpkg command. I type dpkg --configure -a and it returns the error:
"dpkg: request operation requires superuser privilege" 

Help?

---

### Post by gjoellee on 2009-01-22
try adding "sudo" in front: ```
sudo dpkg --configure -a 
```

because setting up a superuser/root may harm your system, it is not set by default in Ubuntu. However the default user and other users having the permissions for it can use "sudo" to be allowed to do certain things to the system.

---

