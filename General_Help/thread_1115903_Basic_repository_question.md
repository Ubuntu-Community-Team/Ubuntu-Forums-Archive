---
title: "Basic repository question"
date: 2009-04-04
forum: General Help
---

### Post by Universal344 on 2009-04-04
I have been playing around with desktop effects in KDE and when trying to install packages, I've noticed that some can only be installed through the command line as I cannot find them in synaptic or adept.  Examples of these are emerald and compiz-kde.  These packages will install with apt-get but will not appear in a GNOME or KDE's package managers.  Can anyone explain this to me?

---

### Post by ShaunG on 2009-04-04
If you can apt-get them then you should be able to install from Synaptics too.

In synaptics use the search fucntion and search for compiz-kde or emerald or whatever it is you want to install. It should appear then.

---

### Post by fabricator4 on 2009-04-04
I've noticed the same thing, but I'm using Gnome.  If I go 
Applications->Add/Remove it doesn't show everything like Emerald and Procmeter3 to give two examples.

To see everything available I have to go
System->Administration->Synaptic Package Manager

Perhaps they are making the distinction between "packages" and those that are merely "application packages".

Make sure you have your software sources set to everything as the default may leave out restricted and/or multiverse.  I suspect you've checked this already however...

Cheers,  Chris

---

### Post by ShaunG on 2009-04-04
Oh yes sorry. Add/Remove is for applications.

Some things which aren't applications won't be in there such as emerald.

If you are looking to install something and it's not in add/remove, check Synaptics.

---

### Post by mb_webguy on 2009-04-04
There have been a number of posts recently about packages not showing up in Synaptic.  Most but not all of these relate to Adobe Air screwing up the package index.  A simple fix in any case is to run the command "sudo update-apt-xapian-index" in the terminal.

---

