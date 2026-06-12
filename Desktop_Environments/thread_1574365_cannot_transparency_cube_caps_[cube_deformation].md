---
title: "cannot transparency cube caps [cube deformation]"
date: 2010-09-14
forum: Desktop Environments
---

### Post by nickfrazier1 on 2010-09-14
i'm using a 64 bit system. i'm running cube deformation with cylinder.
i am unable to make my cube caps transparent.
i've deleted the original cap settings.
i have also attempted to log out and in again to see if it would change.
any suggestions?

also.....my mouse is not changing to it's new pointer when i'm active in compiz.
when compiz is off my mouse change is set, when it is on it stays as the white pointer unless i'm on firefox.
any suggestions there as well?

thank you for your help.

---

### Post by beefone on 2010-09-14
I think the cube caps have to have a "colour" of some sort, i have not managed to make the caps fully transparent either. As far as the mouse cursor issue, there is a setting in the compiz settings manager to change the cursor theme, if i remember correctly its under general options. If not try:

> sudo gedit /usr/share/icons/default/index.theme

The file should have something like:-
[Icon Theme]
Inherits=DMZ-White 
Just change the "DMZ-White" to whatever the name of the cursor theme folder is.

---

