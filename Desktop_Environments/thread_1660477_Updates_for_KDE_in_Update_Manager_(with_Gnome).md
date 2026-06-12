---
title: "Updates for KDE in Update Manager (with Gnome)?"
date: 2011-01-05
forum: Desktop Environments
---

### Post by Skara Brae on 2011-01-05
I have a small question (not a problem).

Why is the Update Manager showing files about KDE that can be updated? :confused:

kdebase-runtime
kdebase-runtime-date
kdelibs-bin
kdelibs5
libplasma
*and-some-more*

I like Gnome, I don't have nor want KDE.

[edit]
Is this because I have KPackageKit installed? (I have _no_ idea why I installed that...)

---

### Post by chrisx on 2011-01-05
You must have installed some software that depends on these things. There is no single API for Linux software, so you'll get updates for all kinds of software - qt, kde, python, gnome, etc..

---

### Post by Krytarik on 2011-01-05
The update manager handles updates for all installed packages (of which are associated archives set), regardless of what desktop environment you are currently using.

Check in "System -> Admininstration -> Synaptic" if those packages are installed (which they obviously are), and "Completely Remove" them.

EDIT: Oh, please check upon removal if there are depencies to other packages, you might have installed, and which depends on them (like chrisx hinted), Synaptic tells you if that is the case!

---

### Post by Skara Brae on 2011-01-05
Ohh, I also installed "KEuroCalc", I now see. I remember I was searching for an (offline) currency calculator some (longer) time ago. I guess that is why I get these KDE updates.

Should I install those updates because of KEuroCalc (and KPackageKit)?

---

### Post by Krytarik on 2011-01-05
Those are your options:

1.) remove the KDE-packages along with all dependend programs

2.) update the KDE-packages to maintain and support your installed programs

3.) don't update the KDE-packages and have them repeatedly show up in the update manager, unless you lock the version of those via Synaptic (which I don't recommend for the long-term)

---

