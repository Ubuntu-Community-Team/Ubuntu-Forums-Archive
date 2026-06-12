---
title: "Apt-get remove?"
date: 2009-03-09
forum: General Help
---

### Post by RedSingularity on 2009-03-09
What is the difference between "apt-get remove package*" and "apt-get autoremove package"?  I thought "remove package*" will automatically remove any apps associated with the word "package".  So then what does "autoremove" do?

---

### Post by simeon87 on 2009-03-09
From the man pages:

remove

           remove is identical to install except that packages are removed
           instead of installed. If a plus sign is appended to the package
           name (with no intervening space), the identified package will be
           installed instead of removed.

autoremove

autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

---

### Post by RedSingularity on 2009-03-09
Yes but then wouldn't "remove package*" do the same thing because the * is a wildcard??

---

### Post by issih on 2009-03-09
Generally using * like that in a unix command matches anything that has the same pattern textually, where the * can replace any amount of text.

So b*n would match ban button and brandon, with the star matching a, utto and rando respectively. It is simply a textual match though, nothing more.

apt-get satisfy's dependencies by maintaining a list of other packages that are required for the correct functioning of the package being installed. Any that are necessary and not yet installed are automatically installed when a package is requested for installation.

There is no requirement in any way for those packages that are installed to satisfy dependancies to be named in some way that textually matches the package that requires them, so there is no reason why wildcard matching should remove them (even if it does work with apt-get which I am unsure about, in many ways i hope it doesn't).

Secondly if it did work like that you'd have all sorts of problems when more than one installed package referenced another one as a dependency. Imagine installing a which requires package c, then installing b that needs c (but its already there so no need to install it again). Now you choose to remove a, if things were matched in some way by naming convention, the version of c installed with a would go too, and b would suddenly break.

in essence, no wildcard matching doesn't work, you remove a package, and the output will tell you if there are other installed packages that are now redundant. Yu use autoremove to get rid of those orphans.

Hope that helps

---

### Post by RedSingularity on 2009-03-09
WOW that does help!  THANKS!!  That cleared up alot for me  :)

---

