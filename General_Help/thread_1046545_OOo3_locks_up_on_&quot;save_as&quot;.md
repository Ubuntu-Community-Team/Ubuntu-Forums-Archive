---
title: "OOo3 locks up on &quot;save as&quot;"
date: 2009-01-21
forum: General Help
---

### Post by lykwydchykyn on 2009-01-21
Running Kubuntu Intrepid w/ KDE 4.2RC1

I installed OpenOffice 3 from this ppa:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

It runs ok, but any time I do a "save as" it locks up, and locks up my whole desktop.  I have to switch to a VT and kill soffice.bin.

I've tried deleting my .openoffice and .openoffice2 directories.

Any advice?

EDIT: BTW, I've tried running from the CLI and I get no error output there. My attempts to get a backtrace with gdb have not yielded anything useful.

---

### Post by mikelygee on 2009-01-21
I had a similar problem with Inkscape, which I solved by, if I recall correctly, removing the file '.gkt-bookmarks' in my home directory (backing up the file first, of course).

I may have had the same trouble with OpenOffice as well, but I can't be sure. I'm pretty sure Inkscape wasn't the only application affected.

Good luck!
--Mike

---

### Post by ender4 on 2009-01-21
I had the same trouble but removing .gtk-bookmarks did not fix the  problem.  Even if it did it would be problematic since I use both gnome and kde.

---

### Post by lykwydchykyn on 2009-01-22
I don't have the file .gtk-bookmarks.

Thanks for the suggestion, though.

---

### Post by mikelygee on 2009-01-22
Open the 'General' tab under the 'Tools --> Options' menu.
There should be a checkbox there for 'Use OpenOffice dialogs'. Try
changing that setting.

---

### Post by lykwydchykyn on 2009-01-22
> **mikelygee said:**
> Open the 'General' tab under the 'Tools --> Options' menu.
There should be a checkbox there for 'Use OpenOffice dialogs'. Try
changing that setting.

Awesome, that fixed it.  I take this to mean there is a problem with the KDE integration package?

---

### Post by mikelygee on 2009-01-22
*I take this to mean there is a problem with the KDE integration package? *

I don't know. I've just started using OOo3 with Gnome, and haven't had any problems. However, I ran into this months ago with an earlier version of OOo (also under Gnome). Unfortunately, I can't seem to find the original discussion that led me to the solution, so I can only speculate that this is the same problem.

In any case, I'm glad you've got it working. Nothing makes an application more frustrating than not being able to save!

---

