---
title: "Battery drained, now browser problems"
date: 2008-12-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pm210 on 2008-12-01
I let me battery drain completely on my Ubuntu Mini9.  Thereafter, I have no bookmarks or the ability to set a bookmark.  No forward or back buttons and no ability to set a homepage, among other impediments to happy surfing.

Any quick fix here for an Ubuntu novice?

Thanks in advance,

---

### Post by lswb on 2008-12-01
If firefox is your browser there will be backups of earlier versions of your bookmark file in your .mozilla directory. Normally there are backups for the 5 previous days, and they are rotated/overwritten, so BEFORE YOU NEXT RUN FIREFOX COPY THEM TO A SAFE PLACE!.

To find them, open a terminal and type

cd .mozilla/firefox
then get a directory listing with ls.

You should see a directory with a random-looking name and an extension of ".default"
For instance on my system I see:
```

lwasserm@merlin:~/.mozilla/firefox$ ls
9z70irl2.default  Crash Reports  profiles.ini

```
The 9z.... or whatever you see on your system is your profile directory, and there is a subdirectory there called "bookmarkbackups" so you could issue these commands:

cd YourDirHere.default/bookmarkbackups
cp * ~
cd

This will copy all the backup files to your home directory and switch you back to your home directory. Now you can run firefox again and not have to worry about overwriting any of the older bookmarkkfiles.

Unfortunately I don't remember exactly how to restore them, but that info is available on one of the mozilla help pages. Just wanted to warn you about saving the old bookmark files before they got overwritten with empty ones.

You should be able to restore the other features by using the edit/preferences menu but if not you could try reinstalling firefox or creating a new profile by running the command "firefox -ProfileManager"

---

### Post by ajgreeny on 2008-12-01
If you still have a good backup in the folder noted here, you can restore it in FF3 with the Bookmarks->Organise Bookmarks menu item.  Go to Import/Backup->Restore and if you have any good backups left there you can get them back from the dated offerings.

---

