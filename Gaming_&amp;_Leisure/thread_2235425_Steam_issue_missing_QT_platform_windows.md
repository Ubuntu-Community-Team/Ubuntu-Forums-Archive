---
title: "Steam issue: missing QT platform windows"
date: 2014-07-21
forum: Gaming &amp; Leisure
---

### Post by john267 on 2014-07-21
I installed steam through WINE, along with a few games.

The only one I've gotten to work is FF8. anything else i try gives me "This application failed to start because it could not find or load the Qt platform "windows".

any idea as to a fix for this?

SOLVED: somehow my winecfg was set to windows 2008, and my wine settings set to 2007. Wasn't sure which was best to use, but i set both to Windows XP and the problem is gone

---

### Post by spjackson on 2014-07-22
Does the folder which contains the .exe contain a folder called platforms? Does this platforms folder contain qwindows.dll? I know for sure that a Qt 5 Windows app looks there to load this dll; I also think it can look in other locations but I'm not sure of the details. If you have this folder and dll elsewhere under WINE you should be able to copy it to the application's folder and that should work. However, there's probably a neater solution.

If you already have the folder and dll in the right place, it could also be failing to load it because of failed dependencies, although I have not come across this situation myself.

---

