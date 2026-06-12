---
title: "KDE 4 Drag and Drop File Open?"
date: 2010-03-12
forum: Desktop Environments
---

### Post by jtslau on 2010-03-12
Just wondering if you could drag and drop a file to an Application in the panel to open the file, similar to Gnome, OS X (Drag and drop to Dock to open), and now even Windows 7 (drag and drop to taskbar while holding Shift).

---

### Post by benerivo on 2010-03-12
Yes, you can.

---

### Post by jtslau on 2010-03-12
Actually let me clarify the problem that I am having, since before dragging a file onto an application launcher in the panel actually executes the application, but there are some issues with that.

Usually, when you add an application to the panel (by right-clicking on the application and selecting "add to panel" in Kicker, the shortcut placed in the panel has a command followed by a job control identifier.  For example, if you add Firefox to the panel, the shortcut command is 'firefox %u'.  The problem lies in the job control identifier.  If say, you have a file 'index.html' in your Documents folder, and you drag it to the Firefox icon, KDE thinks that %u is also a file, and attempts to open %u, which is incorrect (I suspect KDE invokes 'firefox %u index.html' whenever I try to drag 'index.html' onto the panel).

Sure, the easy way of fixing this is to change the shortcut command to just 'firefox', and therefore the command invoked when dragging and dropping a file onto firefox would be 'firefox file'.  But since every application in the kicker has a job control identifier in their command, therefore every application added to the panel must have the job control identifier manually removed.  Either that is the way it must be done (which seems awfully broken), or is there some other proper way to add applications to the panel so as to allow files to be opened via drag and drop?

---

