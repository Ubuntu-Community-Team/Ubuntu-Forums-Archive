---
title: "Playonlinux Skyrim Issues"
date: 2013-01-06
forum: Gaming &amp; Leisure
---

### Post by bman on 2013-01-06
So I am trying to get Skyrim installed.

I installed Playonlinux, followed the instructions for Skyrim, got to the part where Steam is suppose to take over.

The login window for steam has no text, but I could still enter my details and hit log in. But then I get this long black/blank window and nothing happens.

Any ideas?

---

### Post by holastickboy on 2013-01-06
This is a common problem with steam documented all over the place.  You need to launch steam with the -no-dwrite option at the end.

An example of this is:
wine steam.exe -no-dwrite

Check the following link for more information:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444)

---

### Post by bman on 2013-01-06
That link dosen't really explain how to add that information?

---

### Post by xREDEMPTIONx on 2013-01-06
You add it to "arguments" in Playonlinux. Press the "Configure" tab in the main POL window, select your Steam drive on the left and highlight the shortcut you made for the Steam drive right below it. Now over on the right under the "General Tab" you will find an entry box for "Arguments", enter it there.

---

### Post by bman on 2013-01-06
Thanks man, worked great!

---

### Post by bman on 2013-01-06
So it finished installing and I got this.

---

### Post by bman on 2013-01-07
After a bit, I found this thread.

[http://ubuntuforums.org/showthread.php?t=2068539](http://ubuntuforums.org/showthread.php?t=2068539)

From that thread followed these instructions..

"If you run skyrim from the desktop shortcut you will probably get something like : "Failed to initialize rendered...etc" to fix this run PlayOnLinux go to Configure>>Wine>>Registry Editor and then navigate to : HKEY_CURRENT_USER/Wine/Direct3D and then set the UseGLSL from disabled to enabled."

And the game launched.

* Of course now the game plays quite badly at Medium settings, when I know my system did High in Windows.

Anyway to improve that (got the latest drivers)

---

