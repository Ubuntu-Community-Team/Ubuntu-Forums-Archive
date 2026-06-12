---
title: "Stricks when opening firefox from task bar"
date: 2006-06-12
forum: Desktop Environments
---

### Post by wpshooter on 2006-06-12
Can anyone tell me why it is that when I open the Firefox browser from the task bar icon that I get some kind of weird video anomily in that little horizontal stricks flash down the screen from the top middle of the screen and go downwards to each of the bottom corners of the screen (this happens just for an instant (just a flash down the screen) and is not apparent after the browers opens) ?

I get this behavior on both of the computers I have setup so far.  One is an OLD 15" Samsung SyncMaster 15GL monitor being driven by an ATI Radeon 7000 card and the other is an 17" Viewsonic model VA702B LCD being driven by an ATI Radeon 9200 card.

This does NOT seem to happen, if I open the brower from the desktop icon shortcut I created on the desktop.

Thanks.

---

### Post by mcduck on 2006-06-12
It's just a crappy 'effect' that gnome's panel does.

To disable it, open Configuration Editor (if you can't find it, run 'gconf-editor' in terminal to open it), browse to apps/panel/global and disable the 'enable_animations' key.

---

