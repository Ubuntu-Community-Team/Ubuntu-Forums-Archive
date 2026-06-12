---
title: "kmenuedit does not save changes"
date: 2009-04-11
forum: Desktop Environments
---

### Post by kubumar on 2009-04-11
Hey,

When I try to ad items to the k-menu with kmenuedit it doesnt work. Kmenuedit works without errors. I can press "save", it says "updating menus", but when I close it, nothing is changed. I tried it in the console as root too: no errors, but no changes too :(
I am using  kubuntu 9.04.

What can be wrong?

greets martin

---

### Post by ytene on 2009-10-01
Martin,

This doesn't help you much, but I am also seeing the exact same behaviour. I performed a base ubuntu installation, then installed KDE on top, then switched to KDE as my default Window Manager. 

With this latest release of KMenuEdit I don't get to choose between making my changes at a User level or System wide [all changes seem to be system wide] and yet none appear for users. 

If I close and re-open KMenuEdit, it preserves all of the changes that I have asked for in it's local "cache" of the menu structure. 

The missing bit seems to be that the menu structure stored by KMenuEdit is not being copied to the system itself. Now, I always thought that KDE pushes a "localised" copy of the KDE menu structure into the home folder of each KDE-using account. Unfortunately, I've trawled and cannot find the issue. 

If nothing else turns up in the forums or across the web, we'll have to file a bug report with the KMenuEdit developers, I guess.

Regards,

C

---

### Post by jpv2 on 2009-12-09
Hi,

I just wanted to manually add Thunderbird 3 icon to KMenu and encountered the same problem. Any changes done&saved in kmenueditor don't appear in kmenu and are forgotten when I reopen kmenueditor. Do you know if this bug was already filed? Any temporary solution?

Regards
jpv2

---

