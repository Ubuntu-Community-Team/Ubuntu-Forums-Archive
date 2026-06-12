---
title: "Exaile launch keyboard sortcut"
date: 2007-02-01
forum: Desktop Environments
---

### Post by bartzitz on 2007-02-01
hello,

this is my first post on ubuntuforums.org, so exuse me if i picked a wrong thread or broke some other rule :)

i've recently installed Exaile media player and i'm happy with it. I want to make it my default player in Ubuntu. There's a shortcut in System -> Preferences -> Keyboard shortcuts -> Sound: Launch music player. However i failed to find a way to point it to Exaile. Any suggestions?

thanks,
Bob

---

### Post by stuporglue on 2007-03-09
Long time to wait for a response...maybe this will still help someone. 

The shortcut is hardcoded to rhythmbox, but we can trick it by placing a link named rhythmbox before the real rhythbox in the path. 

eg. If you like banshee

```
sudo ln -s /user/bin/banshee /usr/local/bin/rhythmbox
```

That should trick Gnome into thinking it's running rhythbox, but it will really run banshee.

---

