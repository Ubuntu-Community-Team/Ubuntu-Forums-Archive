---
title: "Want to import from TBird to Evolution, don't understand the instructions"
date: 2007-08-29
forum: Desktop Environments
---

### Post by brjoon1021 on 2007-08-29
When I try to import using Evolution, the file browser will not show the directory where my TBird emails are kept. The file browser that opens with the import function of Evolution does not show anything to do with Thunderbird. Can you help ?

This is apparently where they are kept by Thunderbird:   /home/user/.mozilla-thunderbird/l37iv1v1.default/Mail/Local Folders

---

### Post by Brandon.Viking on 2007-08-30
try typing in the hidden directories in manually ... anything which starts with '.' is hidden ... should still be in the file system.

Hope that helps.:)

---

### Post by dndrich on 2007-09-03
I have been playing with this, and I have figured out a way to do this.  First, close Evolution and Thunderbird.  Then, open Nautilus to your home folder.  Now, to see the hidden files, which is where the mailbox is, type "control" + h.  Now you will see your hidden files.  Scroll down to .mozilla-thunderbird.  Open that folder tree until you find the default user folder.  It will be some cryptic numbers and letters followed by .default.  Copy that folder with a copy and paste into your main home folder, or desktop, wherever you want it.  Now it is not unhidden.  Next, open that folder, and you will see some more folders.  Open "local folder", if that is where you kept your mail, which is likely.  In there you'll see a bunch of files that correspond to your folders in Thunderbird, such as Inbox, Sent, Drafts, etc.  Now, each one you want to import you have to rename with an .mbox extension.  So, for example, take Inbox, right click, go to rename, and just add .mbox to the end.  Now open Evolution.  Go to file, import.  Now click on individual file.  Now choose the location of the renamed file...you'll find it easily if you did this right.  Click import, and voile', it imports the mail perfectly!  You will have to rebuild your directory tree inside Evolution if you had multiple folders in Thunderbird.  So there is some work to be done by hand, but at least you can easily capture all of your mail.  Let me know if this doesn't make sense.

Daniel

---

