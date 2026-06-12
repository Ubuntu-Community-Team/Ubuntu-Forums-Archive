---
title: "Can't change pointer 10.10 / compiz wont let you..."
date: 2011-02-23
forum: Desktop Environments
---

### Post by prylux on 2011-02-23
Thought I would just let anyone who may need help with this know. I had issues with changing the pointer when compiz was active in ubuntu 10.10. I tried some other suggestions but it would not change when on the desktop, only when hovering over a window. 

 I solved this issue by doing the following:

Hit alt f2 and enter-> gconf-editor

Then goto-> /->apps->compiz->general->allscreens->options

Then in "cursor_themes" type in the name of the pointer theme 
(Eg. DMZ-White)

 This should resolve the issue with compiz. 
There is allot of help on how to change your pointer. I am not going to go over that here. Just hope this helps someone out with this specific issue.
Oh yea don't forget to **logout/login** or press **ALT F2** and enter **compiz - -replace** to refresh the pointer...  ):P

---

### Post by prylux on 2011-02-23
One more thing...

If the settings don't seem to be holding...

Make sure you are selecting **"Close Window"** in gconf-editor not **"Quit"** or else the setting will not stick.

---

