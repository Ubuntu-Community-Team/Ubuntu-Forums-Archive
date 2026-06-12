---
title: "How to *Search* the KDE menu"
date: 2005-06-22
forum: Desktop Environments
---

### Post by gentsquash on 2005-06-22
Does KDE provide a facility for [COLOR=DarkRed]*searching*[/COLOR] the "K" menu? [SIZE=1](This
menu is invoked, usually, by the "K" in the lower lefthand corner
of `kicker'.)
[/SIZE]
================
Also, I have in my notes that one can adjoin items to the "K"
menu via 
```
K -> Setting -> Menu Editor
K -> Setting -> Menu Updating Tool  
``` 
However, my "K" menu _no longer_ has a "Setting" entry; I probably
damaged [color=brown]~/.kde[/color] at some point.  

Is there a way to restore my "K" menu to its standard setting (at
least at the top level), _*without*_ trashing all of my KDE
customizations. [SIZE=1] (I presume that I could just delete
[color=brown]~/.kde[/color], but that would delete window-defaults
and icon-placements and ...)[/SIZE]

---

### Post by SGC on 2005-06-22
To add/delete/modify items in  kmenu , right-click on the kmenu and choose "Menu editor"

To restore the orginal kmenu delete this file :
~/.config/menus/applications-kmenuedit.menu

If you don't edit the kmenu before, you will not see the above file. KDE creates this file the first time you modify the kmenu.

---

### Post by ltmon on 2005-06-22
[QUOTE=gentsquash]Does KDE provide a facility for [COLOR=DarkRed]*searching*[/COLOR] the "K" menu? [SIZE=1](This
menu is invoked, usually, by the "K" in the lower lefthand corner
of `kicker'.)
[/SIZE]
[/QUOTE]

Not at this stage as far as I know, although I have seen some discussion on KDE forums about putting a search feature in.

Maybe you can get something similar working with the "applications" io slave.  Open Konqueror and type "applications:/" into the location bar.  This provides an alternative to using the Kmenu, but I don't know if it's searchable (can't check now because I'm not at home).

L.

---

### Post by Worzel on 2005-06-23
Not really, because there's nothing to search. The menu simply displays installed programmes depending on how each respective prog-name.desktop file is detailed - you'll find a lot of them under /usr/share/applications/kde. Some programmes may be installed but not show in the menu because a NoDisplay=true parameter is set (you could change this to =false by editing as root if you wanted.
For more info, have a look at [http://standards.freedesktop.org/menu-spec/latest/](http://standards.freedesktop.org/menu-spec/latest/) .
HTH
Jim

---

### Post by zupermanz on 2005-09-26
[QUOTE=SGC]To add/delete/modify items in  kmenu , right-click on the kmenu and choose "Menu editor"

To restore the orginal kmenu delete this file :
~/.config/menus/applications-kmenuedit.menu

If you don't edit the kmenu before, you will not see the above file. KDE creates this file the first time you modify the kmenu.[/QUOTE]
THAT saved me sometime!!! Thanks!

---

### Post by GeneralZod on 2005-09-26
I actually filed a Wish for this a couple of months ago (specifically, find-as-you-type in the K-Menu across app names and descriptions) - I have tons of stuff installed, and it's often tricky to find it in the menus, well-organised though they are.

It's currently assigned to Aaron Siego, who's a very busy guy, so I'm not sure what will end up happening to it.  I swear one of the KDE developers bumped its priority up to "High" a while back, though :)

---

