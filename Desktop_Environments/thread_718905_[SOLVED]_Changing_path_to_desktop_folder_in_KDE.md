---
title: "[SOLVED] Changing path to desktop folder in KDE?"
date: 2008-03-08
forum: Desktop Environments
---

### Post by Zorael on 2008-03-08
For some reason I can't change the path to the KDE desktop folder. 

I go into System Settings -> About Me -> Paths and set it to whatever I want. I hit apply, it asks me if it wants to move files from old folder to new one, and it's saved. If I close the settings app and reopen it, the new path is displayed. But the desktop itself still only shows files from the old folder! (~/Desktop, want it to be ~/ or at the very least ~/desktop; caps are bad)

Is there a settings text file I could manually change this in, perhaps?

---

### Post by nosneros on 2008-05-02
Hi,

Are you running Hardy? Maybe you are interested in "~/.config/user-dirs.dirs".

HTH,
nos

---

### Post by Zorael on 2008-05-04
Aye, found it myself, that's indeed the file. Thanks though.

---

