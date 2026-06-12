---
title: "Bypass Deleted Items"
date: 2009-03-01
forum: General Help
---

### Post by maff130 on 2009-03-01
Hi,

I've been using Ubuntu for a good while now, dualbooting with Windows XP.
In windows, I have the recycle bin set to be completely disabled, so that highlighting a file and pressing the delete key, deletes the file fully.
I've been looking for the same functionality in ubuntu, and so far all I've found is shift-delete, and options to disable file deletion prompts, and to add an entry to the context menu for deletion.
Is there any option that allows just using the delete key to bypass Deleted Items?

---

### Post by heindsight on 2009-03-01
First in System>Preferences>File Management, on the Behavior tab, enable the option to "Include a Delete command that bypasses Trash". Next, go to System>Preference>Appearance, on the Interface tab, enable the "Editable menu shortcut keys" option. Then in a file browser, click on the Edit menu, move your mouse over the Delete option, press the delete key to clear the current shortcut key, and press the delete key again to set the new shortcut key to delete. 

Now when you have a file selected, you can just press the delete key and it will be deleted without going to Trash. You will still be presented with a dialog asking if you're sure you want to delete the file, I'm not sure if it is possible to disable that.

---

### Post by maff130 on 2009-03-01
> **heindsight said:**
> First in System>Preferences>File Management, on the Behavior tab, enable the option to "Include a Delete command that bypasses Trash". Next, go to System>Preference>Appearance, on the Interface tab, enable the "Editable menu shortcut keys" option. Then in a file browser, click on the Edit menu, move your mouse over the Delete option, press the delete key to clear the current shortcut key, and press the delete key again to set the new shortcut key to delete. 

Now when you have a file selected, you can just press the delete key and it will be deleted without going to Trash. You will still be presented with a dialog asking if you're sure you want to delete the file, I'm not sure if it is possible to disable that.

There is an option to disable the file deletion prompt, in the Behaviour tab of Nautilus' preferences.
Thank you very much, this worked perfectly. :D

---

### Post by heindsight on 2009-03-02
> **maff130 said:**
> There is an option to disable the file deletion prompt, in the Behaviour tab of Nautilus' preferences.
Thank you very much, this worked perfectly. :D

So there is. For some reason I thought that only removed the prompt for moving to trash, not deleting.

Of course another way to delete files without moving them to trash, is to open a terminal, and using the rm command...

---

