---
title: "Sync Desktop Profile Between Computers"
date: 2012-09-13
forum: Desktop Environments
---

### Post by pyutaros on 2012-09-13
I've been working on syncing user settings between computers in Ubuntu 12.04 using Unity.  The new Ubuntu Software Center comes with a built in feature that allows you to sync applications between computers, though it's not an automatic process.  In addition to syncing programs, I'd like to sync desktop background, theme, user picture, global menu shortcuts, desktop icons, and login screen.  I think I should be able to do everything with Ubuntu One if I can figure out the right files that contain the information for each setting.  Here's how each will work:

* Applications - Go to the File menu in Software Center and click Sync Between Computers on every computer you want to sync with.  Then go to the Installed section and manually install programs listed that are missing from any computers.  A little clunky, but better than having to hunt the programs down in the main list.

* Desktop Background - My current solution is a workaround at best.  Sync your Pictures folder using Ubuntu One.  Make a copy of the image file you want to make your background and name it something like "wallpaper.jpg".  Point each computer to that filename in your synced Pictures folder.  Now if you want to change your background picture, simply overwrite the "wallpaper.jpg" file on one computer and it will propagate to all of your computers within a couple of logins.

*Theme - Sync Themes folder using Ubuntu One.  Find the configuration file that contains theme info and sync the folder containing that file.

*User picture and global menu shortcuts - Sync the folder containing the configuration files for both.

*Desktop icons - This is a simple sync in Ubuntu One or Dropbox depending on my users.  My kids use the same desktop so they'll have the same games.  I sync a folder in Dropbox for them that they both have access to.  I then edit the ~/.config/userdir.dir file to point the desktop to the Dropbox location.

*Login screen.  Uncertain about this one.  I may just have to manually set all computers to the same theme.

Feel free to comment with your own ideas or needs for syncing user profiles or experiences.

---

