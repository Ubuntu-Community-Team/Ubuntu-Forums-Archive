---
title: "Keyboard Shortcuts"
date: 2006-06-14
forum: Desktop Environments
---

### Post by seelk on 2006-06-14
Is there a file that saves the keyboard shortcuts from gnome's control panel?  Also, can I change my preferred multimedia application to amarok?  Currently it's pointing to Rythm and I was wondering if I can change that.  I did not find that entry under Preferred Applications.

---

### Post by aysiu on 2006-06-14
What do you mean by "save" them? They don't automatically save?

Changing your default music player from Rhythmbox to AmaroK isn't worth it.

You're better off changing the default application for .mp3, .ogg, .aac, etc. to AmaroK (right-click on the file and go to Properties > Open With) and then making a separate launcher keyboard shortcut for AmaroK.

---

### Post by seelk on 2006-06-14
The reason I want to change the preferred app is because I would like to map multimedia keyboard to open Amarok with the multimedia key.

---

### Post by aysiu on 2006-06-14
Try this: ```
sudo dpkg-divert --divert /usr/bin/rhythmbox.old --rename /usr/bin/rhythmbox
sudo ln -s /usr/bin/amarok /usr/bin/rhythmbox
```

---

