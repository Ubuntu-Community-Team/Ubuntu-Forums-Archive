---
title: "Compiz not staring on log in"
date: 2009-02-23
forum: General Help
---

### Post by bobmatino17 on 2009-02-23
I reacently installed Ubuntu Jaunty (Alpha) on my machine and it works great. However, Compiz wont start on login. any help would be greatly apreciated.

---

### Post by Giant Speck on 2009-02-23
> **bobmatino17 said:**
> I reacently installed Ubuntu Jaunty (Alpha) on my machine and it works great. However, Compiz wont start on login. any help would be greatly apreciated.

Go to System > Preferences > Sessions

This will bring up the Sessions Preferences dialog.  Click the Add button and enter the following:

Name:  Compiz
Command: compiz --replace

Then click Add and close.  This will force Compiz to start when you login.

---

