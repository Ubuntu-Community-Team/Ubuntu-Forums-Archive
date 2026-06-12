---
title: "libqt-mt"
date: 2009-01-16
forum: General Help
---

### Post by DeadRobot on 2009-01-16
I need to install libqt-mt to install FirstClass.

I typed this into terminal:
sudo apt-get install libqt3-mt

but this happend:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libqt3-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libqt3-mt has no installation candidate

How do I fix this?

---

### Post by mssever on 2009-01-16
> **DeadRobot said:**
> I need to install libqt-mt to install FirstClass.

I typed this into terminal:
sudo apt-get install libqt3-mt

but this happend:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libqt3-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libqt3-mt has no installation candidate

How do I fix this?
Have you verified that that's the correct package name? Do you have the proper repositories enabled? Is libqt3-mt even available from a repository?

I have no idea what that library is or what FirstClass is, so I can't be more specific.

---

### Post by DeadRobot on 2009-01-16
yeah thats the correct package name.

but this is my first day on linux so i dont know if i have the right repositories or if its available from them...

---

### Post by mssever on 2009-01-16
> **DeadRobot said:**
> yeah thats the correct package name.

but this is my first day on linux so i dont know if i have the right repositories or if its available from them...
Go to System > Administration > Software sources and make sure that main, universe, and multiverse are all selected. If your app is multimedia-related, you might also need medibuntu (Google that for instructions).

Once that's done, check whether FirstClass is available through Synaptic. If so, that'll be the way to go. Otherwise, see if you can now install libqt3-mt. Failing that, Google [FONT=Courier New][COLOR=Green]libqt3-mt ubuntu[/COLOR][/FONT] and see what you get.

---

### Post by DeadRobot on 2009-01-16
Ok i googled it and downloaded a .deb package of it.

but when i double click the package it says this:

"The package might be corrupted or you are not allwed to open the file.  Check permissions"

Its happend with 2 different packages i've tried.

---

### Post by mssever on 2009-01-16
> **DeadRobot said:**
> Ok i googled it and downloaded a .deb package of it.

but when i double click the package it says this:

"The package might be corrupted or you are not allwed to open the file.  Check permissions"

Its happend with 2 different packages i've tried.
Hmm....

Try it from the command line: ```
sudo gdebi filename
```

---

