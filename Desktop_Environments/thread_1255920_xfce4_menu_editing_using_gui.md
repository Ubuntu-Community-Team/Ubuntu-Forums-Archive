---
title: "xfce4 menu editing using gui?"
date: 2009-09-02
forum: Desktop Environments
---

### Post by freeballer on 2009-09-02
I asked in irc but nobody knew or replied to me, so I'm here... I searched google and all it said was "settings manager", or "right click on menu, properties, edit"... NONE of those options are showing.. where is the gui xfce4 menu editor in xbuntu 9.04? can you please tell me the command line option, package needed or other information so I don't have to edit multiple .desktop files and the menu itself... which is a rediculous waste of time to do manually. (sorry I'm just tired and ticked off cause I've gotten nowhere on this)

please help, and save my sanity
Geo

---

### Post by kerry_s on 2009-09-02
unfortunately for xfce4.6 there is no gui editor yet, so editing the /usr/share/applications *.desktop files is the way to do it.

it's not hard, create a right click custom action for root edit.
**gksudo mousepad %f**
text should be checked, so just check "other".

another option is to stack your most used programs on a single icon, like you can have a stack for office, one for web, etc...
use the "application finder".

---

