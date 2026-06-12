---
title: "add/remove programs"
date: 2005-12-14
forum: Desktop Environments
---

### Post by arnieboy on 2005-12-14
I removed the add/remove programs utility from breezy long back..  could somebody refresh my memory on what the deb package was called so that i can reinstall it from the repos?

---

### Post by jalanbuntu on 2005-12-14
My Add/remove programs utility is also disappear :( 
Sadly... I don't even know why it can be lost ](*,)

---

### Post by arnieboy on 2005-12-14
The easiest way to do it (if u have add/remove programs installed) would be to open up applications-->accessories-->menu editor and look up the executable program for add/remove programs under applications-->system tools
atleast that wud give me a hint what the deb is called. 
thanks in advance,
arnie

---

### Post by jasay on 2005-12-14
Is it "gnome-app-install"?  That's seems to be it, at least in Dapper where I am now.

Edit: hey, that's exactly what I did.

---

### Post by cstudent on 2005-12-14
gnome-app-install

---

### Post by arnieboy on 2005-12-14
thanks a lot jasay and cstudent :)

---

### Post by jalanbuntu on 2005-12-15
Ahhhaaa..... gnome-app-install...... that's it
Now I know why it was uninstalled. I think that was removed when I uninstall my firefox. I upgrade my firefox to version 1.5 and uninstall the old firefox.

Now, when I type 'sudo apt-get install gnome-app-install', it will install firefox too..
So, should I install firefox too? If not, how can I install gnome-app-install without install firefox?

---

### Post by mcduck on 2005-12-15
It needs firefox for html rendering, so no, you can't install it without firefox.

---

