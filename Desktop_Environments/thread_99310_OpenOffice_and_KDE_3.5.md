---
title: "OpenOffice and KDE 3.5"
date: 2005-12-05
forum: Desktop Environments
---

### Post by markr on 2005-12-05
Ever since I update my system (including moving to KDE 3.5),  openoffice seems to crash when loading MS Office documents from within Konqueror;  it works fine if I open the office application up first and then select "File-Open" - has anyone else seen this problem or could it just be me???

Thanks

MArk.

---

### Post by daller on 2005-12-05
It's the "system:/home"-bug (known)

What you have to do, is to press the "Home"-button in konqueror before you press the document!

(It's not only MS documents, is it)

---

### Post by markr on 2005-12-05
You are right; hitting home first works a treat.

I've seem people talk about this bug on the forums but not fully understood what it was;  guess I do now!!!

I'm assuming this will be fixed at some point.

Mark.

---

### Post by daller on 2005-12-05
It's not a KDE-problem!

The problem is with NON-KDE applications!

These issues should really be fixed before adding "system:/home" as the default!

Guess we have to wait for dapper...

---

### Post by jeremy on 2005-12-05
You can fix it as follows:
Open the K menu and right click on the application in question (I will use openoffice.org2 writer as an example).
click 'Edit Item'.
Where it says 'Command' change from 'ooffice2 -writer %U' to 'ooffice2 -writer %f'.
Save.

I have done this (change the 'U' to 'f') on all the open office entries and Gimp, they all work properly now.

---

### Post by rampage on 2005-12-20
This worked great

thanx guys

---

### Post by carney1979 on 2005-12-21
[QUOTE=daller]It's not a KDE-problem![/QUOTE]

Actually, it is a KDE problem. For example, I notice that the "Open Terminal Here" servicemenu is unavailable unless I hit the home button.

So, there are some problems with the infamous "system:/home" enviroment.

I filed a bug report some time ago, with no resolution (yet).

David

---

### Post by daller on 2005-12-21
It's NOT a KDE-problem, it's a Kubuntu-problem!!!

See my post here:

[http://ubuntuforums.org/showthread.php?t=96227](http://ubuntuforums.org/showthread.php?t=96227)

---

### Post by carney1979 on 2005-12-22
[QUOTE=daller]It's NOT a KDE-problem, it's a Kubuntu-problem!!!

See my post here:

[http://ubuntuforums.org/showthread.php?t=96227](http://ubuntuforums.org/showthread.php?t=96227)[/QUOTE]

For the sake of NOT arguing, I'll take you word on it.

But I really don't understand how the link you provided proves it's a Kubuntu problem instead of a KDE problem....

David

---

### Post by daller on 2005-12-22
[QUOTE=carney1979]For the sake of NOT arguing, I'll take you word on it.

But I really don't understand how the link you provided proves it's a Kubuntu problem instead of a KDE problem....

David[/QUOTE]

Well, it doesn't prove anything, It's just an answer on how to solve it!

It's a fault in the kubuntu implementation! - It is fixed - in dapper!

---

### Post by carney1979 on 2005-12-22
[QUOTE=daller]It is fixed - in dapper![/QUOTE]

Do "they" still put you in the "system:/home" jail, or did they go back to a normal home directory for your default konqueror file manager location?

David

---

### Post by NeoChaosX on 2005-12-22
No, but from what I'm getting, it seems the kio slaves now properly send the right directory to all applications again.

---

