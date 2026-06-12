---
title: "nautilus ctrl-L behavior"
date: 2005-11-09
forum: Desktop Environments
---

### Post by m4rkl4r on 2005-11-09
I have two suggestions that would definitely improve the user experience for ctrl-L support pn the gnome desktop.  I don't see a place on the web specifically for suggestions re gnome desktop, after 5 minutes on google.

Preliminaries first.
Congratulations to the nautilus team for the nifty "ctrl-s" that allows the user to filter the results shown with a regular expression.  I first saw this suggested when nautilus was in beta, although the suggestion at that time is still superior to the current one from a usability standpoint, which was that such support should be built directly into the location bar.  I should be able to navigate to /home/me/Documents/*.odt and be presented with all .odt documents.

Now to the suggestions.  
When the user gets a location bar/dialog with ctrl-L,
1. If the path given is to a file instead of a folder, then there should be a nautilus window displaying only that file.  
Note that this is the logical end of the above suggestion to integrate regular-expression support in, and is the current behavior of the chooser dialog.  
Notice also that if the chooser implemented regex filtering, it would speed up the current problem where navigating to /usr/bin takes forever while all the objects are being created, or what have you.  You could navigate, for example, to /usr/bin/g* or /usr/bin/*vim* and cut down on the number of files that pop up.

2.  When ctrl-L is used to get a location dialog on an empty desktop, there should be a check box for "default location", so that every time one opens the dialog it is not necessary to navigate again to the desired location.
If the box is unchecked, it can go back to ~/Desktop

M4rkl4r

---

### Post by 23meg on 2005-11-09
You could post your suggestions on [the Gnome bugzilla]("http://bugzilla.gnome.org/") or [gnomesupport.org]("http://www.gnomesupport.org") .

---

### Post by m4rkl4r on 2005-11-10
Thanks, and done

---

