---
title: "Fixing Firefox"
date: 2018-10-05
forum: Desktop Environments
---

### Post by DigiAngel on 2018-10-05
So....not sure how I've managed this, but here goes.  Moons ago I uninstalled firefox and went the chrome route.  I've since uninstalled Chrome...and I now have Opera installed system wide.  I've grabbed the portable version of firefox and put it into my home dir.  Now...whenever I open a link within say...Evolution or another app, I get a new blank window.  Does anyone know how to get firefox to open the actual link in a tab?  I don't want to install firefox system wide, just for myself.  Thank you.

---

### Post by Frogs Hair on 2018-10-05
You can run FF from a folder in the user directory. [Download]("https://www.mozilla.org/en-US/firefox/new/") the .tar.bz2 , extract, and  select the bit labeled firefox to launch. The file manger should be set to execute programs in preferences or the application won't open. When open, an icon should appear in the launcher. For updates go to about Firefox. I currently have a version of FF running out of the documents folder.

---

### Post by DigiAngel on 2018-10-05
Thanks...from the default apps in Bionic under Web it shows:  Preferences - Mozilla Firefox.  Not sure what else I can do to change that.

---

### Post by DigiAngel on 2018-10-05
Looks like this was fixed up with adding a %u to the firefox.desktop in ~/.local/share/applications/firefox.desktop.  Thank you!

---

