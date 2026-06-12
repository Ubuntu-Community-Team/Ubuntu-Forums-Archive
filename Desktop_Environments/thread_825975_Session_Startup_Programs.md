---
title: "Session Startup Programs"
date: 2008-06-11
forum: Desktop Environments
---

### Post by LostPavek on 2008-06-11
The list of programs in gnome-session-properties is out of sync with ~/.gnome2/session and I can't figure out why.  Unchecking items in the list when going to System->Preferences->Session doesn't have any effect, if I reboot the same applications still startup as if I hadn't unchecked them.  Most notably bluetooth applet and evolution alarm notifier.

Trying to fix the problem I closed all processes except for what I wanted to run and used gnome-session-save but the programs I didn't want to run are still listed in the session file.  I manually commented out the lines, but I still don't understand why gnome-session-properties doesn't correctly reflect the file itself and why making changes in the program doesn't have any effect.

Does anyone have any ideas on how to begin diagnosing and fixing this problem?

EDIT: Okay, apparently I was confused and didn't realize that the settings set in gnome-session-properties are not stored in the ~/.gnome2/session file.  So that problem is now fixed by just removing the session file.

---

