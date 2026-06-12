---
title: "Cannot delete misplaced doubled &quot;desktop&quot; folder"
date: 2020-11-12
forum: Desktop Environments
---

### Post by maurizioferreira on 2020-11-12
(ubuntu 20.04.01)

After my mouse went crazy, due to discharged battery, I found a "Desktop" folder inside my "Downloads" folder.
The regular Desktop folder still exists in my home directory, and it seems to work properly.

The doubled "desktop"  seems a link to the regular one, since adding or removing things to the first results in the same action being carried on the second.


I tried to delete it via Nautilus, and via command line, both as a regular user than as admin, but in any case nothing happens.
I don't even have any error message.


Any suggestion ?

After further testing, I found that the misplaced folder is the "real" desktop folder, so that adding /removing link to it causes them to appears on the screen.
the folder in homed dir seems not working anmore.

Now I've got worse.

Trying to solve the problem , I've deleted the home/Deskop folder, and via nautilus I dragged the "desktop" folder from Dowloads to the screen.
then I created a link to a file an placed it on the screen.
Now I cannot even delete it from the screen. the systen doesn't find it !.

Please help

OK,  I SOLVED the problem
I've rebooted in text mode, deleted the extra folder, and recreated the correct folder in my home, then, after having rebooted in graphic mode I adjusted the file .config/user-dirs.dirs to set the correct path.
Probably working from the graphic mode, the system recreates the invalid folder as soon es it is deleted

---

### Post by TheFu on 2020-11-12
> **maurizioferreira said:**
>  
Probably working from the graphic mode, the system recreates the invalid folder as soon es it is deleted

Only certain GUIs do that, let me assure you.  There are 20-50 other GUIs available, each with good and bad points.
BTW, it would really help the community if you use the "Thread tools" button and marked this thread "SOLVED". This prevents wasted effort.

---

