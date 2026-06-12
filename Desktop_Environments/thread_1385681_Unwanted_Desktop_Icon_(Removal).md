---
title: "Unwanted Desktop Icon (Removal)"
date: 2010-01-19
forum: Desktop Environments
---

### Post by rbscairns on 2010-01-19
Using Ubuntu 9.10 and have established a connection to my network attached storage (NAS) using Places > Connect to server... (Windows share type) and checking the Add bookmark. This works great and reconnects with each login.

The NAS is listed in the Places drop-down box and when I click it, the "data on nas.local - File Browser" opens. Just what I want.

The annoying thing is that this action also places an icon "data on nas.local" on the desktop and a new entry of the same name in the Places drop-down box. Both of these I do not want.

The only way I have found to remove these two annoying items is to right-click the desktop icon and select "Unmount". This needs to be done every time I access the NAS and want to remove them.

How do I stop the "data on nas.local" icon from appearing on the desktop and from being included in the Places drop-down box?

---

### Post by utnubuuser on 2010-01-19
Might be able to change display setting for nautilus in gconf-editor.  Alt+F2>>gconf-editor>>apps>>nautilus
Though that will probably also affect icons for other drives, such as usb-sticks an/or cd/roms.

---

### Post by rbscairns on 2010-01-19
Thank you utnubuuser :D

What I needed to do was stop the volumes icons from appearing on the desktop (I'm still learning the terminology). I understand that in doing this, all volume icons will not appear on the desktop, such as USB sticks, CD ROM's, etc.

In beginners terms, here is what I did-

[LIST]
[*]Alt+F2 (opens the Run Application)
[*]Type gconf-editor (for the Configuration Editor)
[*]Click Run (opens the Configuration Editor window)
[*]Expand the apps entry
[*]Expands the nautilus entry
[*]Select desktop
[*]Deselect the volumes_visible option
[*]Close the Configuration Editor window
[/LIST]
 These steps stop ALL volume icons from appearing on the desktop.

The listing in the Places drop-down box persists, however I can live with that.

---

