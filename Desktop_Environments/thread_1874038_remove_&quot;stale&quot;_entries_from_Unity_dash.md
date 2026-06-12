---
title: "remove &quot;stale&quot; entries from Unity dash?"
date: 2011-11-02
forum: Desktop Environments
---

### Post by gamblor01 on 2011-11-02
Does anyone know how to manually remove entries from popping up the dash?  I had issues with Unity and SQL Developer in 11.04 (which unfortunately have not been fixed in 11.10).  The bug report is here if you're interested:

[https://bugs.launchpad.net/unity/+bug/757991](https://bugs.launchpad.net/unity/+bug/757991)



If I remember correctly there are a few different ways that SQL Developer can be installed on a Linux system (either via rpm or by a zip file).  I originally used the .zip file but after upgrading to 11.04, Unity wouldn't respect my shortcut in the launchbar.  Therefore, I used alien to convert the .rpm file to .deb and installed that way.  At least now I can hit the super key and then start typing "sqld" to get the list.  But notice in the screenshot there are 2 SQL Developer entries.  One has a legitimate icon while the other does not -- but selecting either one will launch the program successfully.

Is there a way I can remove one of these entries so that it doesn't appear when I'm searching in the dash?  I would prefer to remove the one with the blank icon.  Actually I would prefer the bug to be fixed but since that doesn't seem to be happening...

If you know how to fix this please share.  Thanks!

---

### Post by gamblor01 on 2011-12-30
I know this is rather old but I stumbled across the answer for this today while trying to get iReport to show up in the list of applications when I search in dash.  I noticed that I actually had 2 entries for SQL Developer (that is, 2 .desktop files).  The first was in /usr/share/applications and the second was in ~/.local/share/applications.

By examining these files, I was able to determine that the file /usr/share/applications/Oracle-sqldeveloper.desktop was the stale entry (the Icon line specified a file that didn't exist).  Thus, I simply deleted the file and now when I search my dash for sqld, only the "real" application is found.  Hooray!

---

