---
title: "huge font in kubuntu"
date: 2006-01-17
forum: General Help
---

### Post by aznmodder on 2006-01-17
everything in kubuntu is HUGE..i cant only see 1 folder on my desktop because it takes up the whole screen, the calendar text is really big so its impossible to read and when menus pop up such as applications and such i can only see 1 menu bar and a piece of the next one. in applications i can see file edit and tools usually but thats it...i have to move the application many times over to get over the the X button on the top right to close it.  

The font is also huge when im entering my user name and password into the login screen...ubuntu with gnome works fine but one time when i installed amsn on it, it had the same problem, i reinstalled with easy amsn install how to on this forum and it worked fine.

any ideas? thanks

---

### Post by Choad on 2006-01-17
[QUOTE=aznmodder]everything in kubuntu is HUGE..i cant only see 1 folder on my desktop because it takes up the whole screen, the calendar text is really big so its impossible to read and when menus pop up such as applications and such i can only see 1 menu bar and a piece of the next one. in applications i can see file edit and tools usually but thats it...i have to move the application many times over to get over the the X button on the top right to close it.  

The font is also huge when im entering my user name and password into the login screen...ubuntu with gnome works fine but one time when i installed amsn on it, it had the same problem, i reinstalled with easy amsn install how to on this forum and it worked fine.

any ideas? thanks[/QUOTE]
kmenu> system settings> appearance> fonts?

what resolution are you using?

---

### Post by aznmodder on 2006-01-17
on ubuntu-gnome im using 1600x1200...shouldnt change just because i go to kubuntu? or does it?

i cant see kmenu X_X

---

### Post by justkrisma on 2006-01-17
[QUOTE=aznmodder]on ubuntu-gnome im using 1600x1200...shouldnt change just because i go to kubuntu? or does it?

i cant see kmenu X_X[/QUOTE]

please try with this command to reconfigure driver and pixel size..i hope works

**sudo dpkg-reconfigure xserver-xorg**

---

### Post by firehead on 2006-01-18
[QUOTE=aznmodder]i cant see kmenu X_X[/QUOTE]
you can enter the system settings menu by typing kcontrol in konsole...there you can change the size of your fonts...not sure wether this is really what causes your huge fonts, try justkrisma's hint first ;)

---

