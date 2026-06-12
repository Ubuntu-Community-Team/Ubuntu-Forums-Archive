---
title: "OpenOffice UI font"
date: 2005-11-27
forum: Desktop Environments
---

### Post by Brent Dax on 2005-11-27
I'm having a weird problem with OpenOffice.  Sometimes, when I open a document with it, it chooses a very strange font (such as BernhardFashion BT) to render the UI--menu titles, drop-down menus, etc.--in.  If I close OO and re-open it, it will usually pick a more sensible font.  When it does have a weird font, the selection of fonts to use in the document is often very limited.

This happens on two machines, both running Breezy Badger; one is an x86 laptop and the other is an AMD64 desktop (running the AMD64 version of Breezy).  I keep their home directories synchronized with Unison, which may be a factor, as it seems to happen especially often right after a synchronization.

Thanks for any advice!

---

### Post by Perfect Storm on 2005-11-27
Which version of Open Office are you using? The one who comes with Breezy or the final one?

---

### Post by Brent Dax on 2005-11-27
[QUOTE=Artificial Intelligence]Which version of Open Office are you using? The one who comes with Breezy or the final one?[/QUOTE]
Yes, I'm still using the beta that comes with Breezy; I was planning to upgrade once Backports picked up the final version.

---

### Post by Perfect Storm on 2005-11-27
Try see if it helps with the final version, add this to the repo:

## Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

---

### Post by Brent Dax on 2005-11-27
[QUOTE=Artificial Intelligence]deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./[/QUOTE]
I ended up with a horribly botched installation--it removed a ton of packages without installing replacements, with the basic result that the OO apps completely disappeared from my system.  I'm currently putting the machine through the arduous process of downloading and installing the old version.  Perhaps this is because I'm on AMD64 right now?

---

### Post by Perfect Storm on 2005-11-27
I don't know. Though it sounds weird. I've no experience with arch 64, the only thing that should be removed is ubuntu-desktop and previous version of OO2. Which files/applications want it to remove?

---

### Post by Brent Dax on 2005-11-27
[QUOTE=Artificial Intelligence]I don't know. Though it sounds weird. I've no experience with arch 64, the only thing that should be removed is ubuntu-desktop and previous version of OO2. Which files/applications want it to remove?[/QUOTE]
Oh, they were all parts of OO, but the point is that it didn't *replace* them, it just *removed* them.  The packages were things like openoffice2-writer, openoffice2-calc, etc.  After Synaptic finished, they had all disappeared from the menu and I couldn't start them on the command line.

It was rather strange, really--there were only five upgradable packages in Synaptic, and one of them wouldn't install at all.

---

### Post by Perfect Storm on 2005-11-27
Try to install them one at the time.

---

