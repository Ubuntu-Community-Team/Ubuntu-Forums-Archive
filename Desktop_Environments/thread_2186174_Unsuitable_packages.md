---
title: "Unsuitable packages"
date: 2013-11-06
forum: Desktop Environments
---

### Post by vasa1 on 2013-11-06
I was looking at Xubuntu's [strategy document]("http://bazaar.launchpad.net/~knome/+junk/xubuntu-strategy-document-rewrite-1311/view/head:/strategy-document"). There's a section describing "unsuitable packages":
> 
=== Unsuitable Packages ===
      
Packages that work against our goals and our mission statement aren't appropriate when being considered for inclusion in Xubuntu. The following list of guidelines can be used to help identify areas of concern in candidate packages:
 * Packages that do not use GTK toolkit (i.e. QT/KDE applications)
 * Packages that use interpreted languages (generally slower and require more memory)
 * C++ programs (tend to be heavier than C programs)
 * Packages that will pull heavy libraries, especially if they will run and/or start frequently


Can someone provide examples of what would be excluded by the second item?
Is there a convenient command for non-techie types to know which language a program is written in?

---

### Post by ian-weisser on 2013-11-06
A media player binary compiled from a source written in C would meet the second criteria.
A media player binary in compiled Python bytecode would meet the second criteria.
A media player script written in Python (text) would not meet the second criteria.

To determine the language, you must inspect the source code. You cannot easily tell from the compiled binary.
Locating source code is not difficult - the *apt-src* package is one way, the upstream website (see ***apt-cache show packagename***) is another.

There's a difference between what the Xubuntu Team wants to go into Xubuntu (a dependency of the xubuntu-desktop metapackage) vs. the acceptance criteria for a new package in the Ubuntu Repositories.

For example, let's say you create a new package with a desktop weather application. You can add it to the Ubuntu Repositories regardless of the language it's written in, regardless of the graphical toolkit, and regardless of how many complex libraries it requires. Once it's in the Ubuntu Repos, the Xubuntu Team will judge by their own criteria if it's worth adding to Xubuntu. If they choose not to, Xubuntu users can still add your package from the Software Center.

---

### Post by 3rdalbum on 2013-11-06
As Ian said, you can use any Ubuntu package on Xubuntu regardless of what language it's written in or what toolkit it uses.

The document just defines what programs will never be included on the default install of Xubuntu.

---

### Post by vasa1 on 2013-11-07
Thanks for the replies. I do use *apt-cache package_name*.

---

