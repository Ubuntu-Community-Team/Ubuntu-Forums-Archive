---
title: "firefox resets each load as if just installed"
date: 2009-04-03
forum: General Help
---

### Post by pikaia on 2009-04-03
Hello.

This just started happening last night after the upgrade from 3.0.7 to 3.0.8, so I'm not sure whats going on.

I tried to install a new theme and when firefox restarted, the theme wasn't loading.  I tried again, and with different themes, all with the same effect, none.  It will install extensions (User Agent Switcher) but nothing else.  It also starts each load with the 'Mozilla Firefox Start Page' and welcome tabs as if THAT is the first time its been run.  If I close firefox with open tabs and select to remember tabs, it doesn't.  

Has anyone seen this before?  DO you know a fix?  I went into the config and checked out the sessionstore and its set for 'true' as well as the other associated parameters.  So I've reached the end of my google searching abilities.  

Thanks for any help.

---

### Post by ajgreeny on 2009-04-03
Sounds like a configuration problem, so rename your ~/.mozilla folder to ~/.mozillaold and restart FF.  A new profile will be made, but you can copy across the bookmarks file from the old profile as they will probably be the most important to you.  Bookmarks are now in a file called ~/.mozilla/firefox/####.default/places.sqlite, not bookmarks.html.  If you want to keep all your extensions, you could try just renaming the firefox folder in ~/.mozilla, but the problem may be an extension, so try that, but be prepared to change the whole .mozilla folder if needed.

---

### Post by lidex on 2009-04-03
Had the same problem - uninstall/re-install worked for me. Of course back up your profile first. FEBE extension has made reconfig a breeze. You may want to try it when you get FF as you like it.

Had problems on a windows box as well. Did not update properly from within FF and had to uninstall then re-install after downloading full executable. Did you check version after update?

---

### Post by pikaia on 2009-04-03
I did a remove --purge and manually deleted all folders that referenced firefox, and reinstalled, but that didn't solve the issue.  I'll try doing it in Synaptic.  I also tried installing through the firefox website and opening the shell in the extracted folder, but it keeps resetting the preferences as well.  My bookmark toolbar still works though.

I'll try again when I get home.

---

### Post by ajgreeny on 2009-04-05
If your bookmarks toolbar still works with all your old bookmarks, I think you still have your old config in ~/.mozilla folder.  have you tried my earlier sugegstion of renaming that folder and restarting FF?

---

