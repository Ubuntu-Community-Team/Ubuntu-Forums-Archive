---
title: "VLC opens instead of Nautilus"
date: 2010-07-05
forum: Desktop Environments
---

### Post by Linye on 2010-07-05
So, I watched a movie using VLC and close the app, then I try to open the file browser from the File Browser Launcher applet of AWN and VLC opens trying to play whatever is in the folder. Tried with Kupfer app launcher and same thing.

I'm laughing at how ridiculous this is. Please help!

---

### Post by CannibalZerg on 2010-07-06
1. right click Menu Bar and choose edit menu
2. highlight Other
3. right click "open folder" item and go to properties
"Command" field should contain: *"nautilus --no-desktop %U*" (without quotes)

---

### Post by engla on 2010-07-06
You can also change the program associations globally using Kupfer

1. Select any folder in Kupfer's first pane
2. Select 'Set Default Application...' (subject to translation in your locale) in the action pane
3. Select 'Open Folder' (subject to translation) in the third (indirect object pane) and press Return to run the command.

---

### Post by Linye on 2010-07-06
Thanks both of you! I was getting desperate because I didn't know how it got that way but it works now. :D

---

