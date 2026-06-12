---
title: "restore nautilus icons?"
date: 2010-05-10
forum: Desktop Environments
---

### Post by aganhuyag on 2010-05-10
I have installed nautilus-elementary but didn't like it. So I wanted to go back to regular nautilus but the gui items and icons are missing. Only icons left are Backward and Forward buttons. I have removed elementary repository and reinstalled the nautilus but it didn't restore the default nautilus. How can I restore it? Is there any additional packages to install? Thanks :)

---

### Post by kerry_s on 2010-05-10
did you remove the hidden settings folders/files in your home?
press ctrl+h to see hidden in nautilus.

look under ".gnome2" & ".gconf"

---

### Post by aganhuyag on 2010-05-10
I didn't remove the hidden files (not intentionally, does the elementary installation and un-installation remove those files?)

I have checked those folders, those files seem to be present.

---

### Post by ammonkey on 2010-05-11
sudo apt-get install --reinstall nautilus ?

---

### Post by kerry_s on 2010-05-11
> **aganhuyag said:**
> I didn't remove the hidden files (not intentionally, does the elementary installation and un-installation remove those files?)

I have checked those folders, those files seem to be present.

no, uninstalling does not remove those files.
once you delete those it should return to the default nautilus settings.

after you delete them log out & back in.

---

### Post by aganhuyag on 2010-05-12
> **kerry_s said:**
> no, uninstalling does not remove those files.
once you delete those it should return to the default nautilus settings.

after you delete them log out & back in.

deleting those files only brought back breadcrumbs.. ;) but the others are still missing... :confused:

---

