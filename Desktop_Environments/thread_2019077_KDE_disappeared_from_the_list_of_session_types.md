---
title: "KDE disappeared from the list of session types"
date: 2012-07-07
forum: Desktop Environments
---

### Post by ub07 on 2012-07-07
I have Kubuntu 12.04, and I have been trying out various desktop environments to see which ones I like, but I ran into problems after I installed the Xubuntu desktop. Now KDE, the native desktop, does not appear on the  list of available sessions on the login screen. I am locked out of KDE. The kde-plasma.desktop file in /usr/share/xsessions does exist along with all the other sessions that I have tried. It just is not an option at login.

How do I add KDE back on the list of session types?

Thanks.

---

### Post by ub07 on 2012-07-07
A further piece of information: I edited my .dmrc file to session=kde-plasma.desktop and logged out. I got a message that said that my "saved session type is not valid anymore." How can that be? I did not delete KDE when I installed the Xubuntu desktop. If I try to install the kde desktop, I get a message from apt-get that says that it is already installed and configured (which I already knew).

---

### Post by ub07 on 2012-07-07
It turns out that I was wrong. Indeed, KDE was fully configured as the system told me but that somehow the Xubuntu desktop removed the KDE desktop completely. I reinstalled the KDE desktop and now I have KDE back again and all of my settings were preserved (thank goodness).

Please mark this as solved.

---

