---
title: "GNOME default file manager was changed to pcmanfm somehow - how to get nautilus back?"
date: 2010-02-01
forum: Desktop Environments
---

### Post by immerohnegott on 2010-02-01
Just realized that somehow, the Places dialog in the GNOME menu maps to pcmanfm instead of Nautilus. I did not do this myself, so I have no idea how to get it to map back to Nautilus - I found a couple of older howtos on how to change the file manager TO something non-nautilus, but they involve editing a couple of .desktop files in /usr/share/applications that do not exist on my install. 

I ran dpkg-reconfigure nautilus to no avail, and went through gconf-editor, which shows nautilus as the file manager in desktop>gnome>session>required_components. I couldn't find any other file management references that would map to a system-wide default.

I still have access through the desktop icons, but the places menu is much easier to navigate quickly...any thoughts?

---

### Post by omelette on 2010-02-08
Hi.  I also had Nautilus changed as the default file manager - the solution is to go;

(1) System/Preferences/System Settings
(2) Select Default Applications -> File Manager
(3) Select 'Other' at bottom, then the 'browse' option - "..."
(4) Select 'Add' from the 'Applications Preference Order'
(5) Type in "Nautilus" rather than browse for it, click OK.
(6) Ubuntu associates this with 'File Manager', adding this as an option.
(7) Select 'File Manager'.

---

