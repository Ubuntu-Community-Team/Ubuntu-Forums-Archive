---
title: "Setting VLC as default media player"
date: 2005-08-09
forum: Desktop Environments
---

### Post by glowstick on 2005-08-09
When I go to a video files properties and try to add VLC into the "Open With" tab it always says "Could not add application to the application database"

So everytime I want to play something with VLC I have to open VLC up first then open the video through it. 

Is there any other way I can make VLC as my media player?

---

### Post by johannes on 2005-08-09
You need to choose "Use a custom command" in the "Add Application" window and type in "vlc". For some reason the "wxvlc" you get from choosing "VLC for Gtk+" in the list doesn't work.

---

### Post by Tristan9669 on 2005-08-13
thanks

---

### Post by Cyberkef on 2005-08-14
[QUOTE=johannes]You need to choose "Use a custom command" in the "Add Application" window and type in "vlc". For some reason the "wxvlc" you get from choosing "VLC for Gtk+" in the list doesn't work.[/QUOTE]
Thank you very much for that :)
I searched a long time to get a fix for this ;)

---

### Post by Proleter on 2006-02-26
This happens with every application. For example I want to open some text file with Open Office. I go to Open with... and select the application. It gives me error:
**Could not add application to the application database**
I didn't had that problem before.
Can I fix this problem without reinstalling the system. It's fresh install.

---

### Post by Proleter on 2006-02-28
A solved the problem with giving 777 permissions to all /.local subfolders.
Although it works I'm not shure that these are the right permissions for this folder. Can somebody explain more?

---

