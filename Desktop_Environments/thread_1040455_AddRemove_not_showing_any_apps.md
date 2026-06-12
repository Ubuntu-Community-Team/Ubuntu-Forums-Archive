---
title: "Add/Remove not showing any apps"
date: 2009-01-15
forum: Desktop Environments
---

### Post by bradshawd on 2009-01-15
Very strange one.  Just done an update (4 or 5) files, was not really watching as it usually goes so smoothly.  No restart required.

Now I have tried to look in add remove for an app and it shows absolutely nothing

completed  "apt-get check"

*******************************************
bradshawd@DONNINGTON:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
********************************************
bradshawd@DONNINGTON:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive](http://archive).................
...................................
...................................
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Done
**********************************************

But still add/remove shows nothing

package Manager on the other hand is merrily showing 25000+ packages available and 1100+ installed.

Sorry about this, but a bit of a noob and, have now come to the end of my knowledge level (also been unable to locate anything in the forums)

Any help much appreciated.

:(Derek

---

### Post by gettinoriginal on 2009-01-16
Check synaptic and make sure that "gnome-app-install" is installed, it may have been uninstalled when you did your changes. Even if it shows that it is installed, check it for reinstall and click apply.

---

### Post by bradshawd on 2009-01-16
Many Thanks to yourself sir.

That fixed it.

Although I did reinstall the data as well.

I managed to install the package I was after via apt-get so have learnt a little more.

Once again many thanks.

---

