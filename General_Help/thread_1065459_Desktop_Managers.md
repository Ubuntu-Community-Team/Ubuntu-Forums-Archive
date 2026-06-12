---
title: "Desktop Managers"
date: 2009-02-09
forum: General Help
---

### Post by supernova1 on 2009-02-09
I am currently using Gnome, but would like to try out KDE.  Do I have to have a separate Ubuntu installation to try out KDE, or can I somehow install KDE and choose during login which I want to use?  If this is possible, can anyone point me to good instructions on how to set this up?

Thanks,

David

---

### Post by supernova1 on 2009-02-09
Nevermind, I just found the solution just in case anyone else needs this:

sudo apt-get install kubuntu-desktop

And then I can select during login.

Thanks,

David

---

### Post by mb_webguy on 2009-02-09
Installing kubuntu-desktop will also install all of the KDE applications included in Kubuntu.  If you just want to try out KDE, then you can just install the kde package.

---

### Post by sha.goyjo on 2009-02-10
Could you reference the package please? The KDE package in synaptic contains all the apps as well.

---

### Post by mb_webguy on 2009-02-10
The kde package contains the apps that are part of the KDE desktop environment.  The kubuntu-desktop package contains those, plus a number of others as well.  You can see for yourself by opening Synaptic, locating each package, right-clicking on the package and selecting Properties, and clicking the Dependencies tab.

---

### Post by sha.goyjo on 2009-02-11
Tried like you said, installing the kde package. Gnome just ran ON TOP of my kde desktop. Any clues?

---

### Post by mb_webguy on 2009-02-11
You have to select a KDE session at login.

On the login screen, click on Options, the Select Session.  One of the options should say KDE.  Select that, then login as usual.

---

### Post by sha.goyjo on 2009-02-11
I selected the KDE option. Gnome ran ON TOP of KDE. literally, I could see KDE with Gnome on top of it.

---

### Post by mb_webguy on 2009-02-11
> **sha.goyjo said:**
> I selected the KDE option. Gnome ran ON TOP of KDE. literally, I could see KDE with Gnome on top of it.

... Wow.  I've never heard of that before.  I've installed the kde package before and had no problems.

I suppose you could install the kubuntu-desktop package an see if that makes a difference, but except for installing a bunch of extra software, it should be the same.  Just in case there was something wrong with the kde installation, make sure you completely remove kde before you install kubuntu-desktop.

---

### Post by sha.goyjo on 2009-02-12
did that. Same problem. Gnome is using the kubuntu theme but still running on top of kde.

---

