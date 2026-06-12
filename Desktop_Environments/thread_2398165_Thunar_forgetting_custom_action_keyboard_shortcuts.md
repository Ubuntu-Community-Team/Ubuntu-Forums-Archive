---
title: "Thunar forgetting custom action keyboard shortcuts"
date: 2018-08-08
forum: Desktop Environments
---

### Post by kazakore on 2018-08-08
I followed [This Guide]("https://askubuntu.com/questions/403922/keyboard-shortcut-for-thunar-custom-actions") a while ago and set a keyboard shortcut to open the terminal in current directory (exactly as per the guide in the end.) This has worked fine for some time but this morning it stopped working!

So I go and edit the shortcut again but it doesn't work. If I open the folder and watch the file /home/dale/.config/Thunar/accels.scm I can even see it did modified and my edits deleted a minute of so after logging in!! Why is this happening? I want my edits to stick and not be deleted every time I log into the system like it should do! Especially as the edits do nothing without logging out and in again!

Is there any other way to do this? Or any way to see what and why this file is being rewritten on log in? It may be related to me running out of space on my shared system/home partition (error causing logs to fill up drive in a matter of minutes) a few days ago, quite a few open applications lost all their Preference settings (they must always try and resave it on application close, rather than when changes are actually made.) But I am back to have over 30GB spare space now so all should be good, plus like I said I can see the file get changed in front of my eyes (either watching modify date change or having it edit to open and getting a notification that the file on disk has changed.)

Any help much appreciated.



EDIT: Correction. It rewrites the accels.scm file shortly after opening Thunar for the first time in session (going by Modified date/time) not automatically shortly after logging in.


EDIT2: Removed (renamed) whole folder, rebooted, followed guide again and this time it worked. Would be nice to know why I couldn't get it to stick before but at least I have my shortcut back :)

---

