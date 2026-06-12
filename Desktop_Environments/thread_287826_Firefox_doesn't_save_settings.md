---
title: "Firefox doesn't save settings"
date: 2006-10-29
forum: Desktop Environments
---

### Post by Alex99 on 2006-10-29
Hi,
Swiftfox 2.0 doesn't retain the changes I make, such as configuring the toolbar, changing the view mode of the history, changing the mediaplayer connectivity settings. Two extensions should have been uninstalled, too, but even after a restart they show up as to be uninstalled after a restart (they don't show up under about:config, though).

In the profiles folder, the file "lock" seems to be empty, and "sessionstore.js" seems to be broken, too; I can't display it with an editor.

I tried starting Swiftfox with gksudo, as suggested elsewhere in this forum, which works fine, but it bothers me that I always have to enter my password just for opening a browser (it doesn't display the close buttons on all the tabs, either, and other things I would like to change).
I also checked the rights in the profile folder, particularly prefs.js.

Fire/Swiftfox has been acting crazy lately, so I'm hoping I'll get this fixed. Suggestions much appreciated.

edit: solved problem - just had to delete localstore.rdf in profile folder
see [http://kb.mozillazine.org/Resetting_preferences](http://kb.mozillazine.org/Resetting_preferences)

problem with extensions not disappearing from the extensions list after uninstalling: just delete extension folder in profile folder > extensions. install.rdf or similar file will help identify the extension - see
[http://kb.mozillazine.org/Uninstalling_extensions#Problems_uninstalling_in_recent_versions](http://kb.mozillazine.org/Uninstalling_extensions#Problems_uninstalling_in_recent_versions)

---

