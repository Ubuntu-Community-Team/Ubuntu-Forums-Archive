---
title: "wine + cedega shortcuts"
date: 2007-04-04
forum: Gaming &amp; Leisure
---

### Post by jrock2004 on 2007-04-04
Ok what I am looking for is when I install something with either of these apps how can I create a shortcut on my desktop and or add it to my kmenu? Thanks

---

### Post by lordhebe on 2007-04-05
With wine:

-Right click the desktop and click, Create Launcher (Although since you are using KDE, it should be something similar, so it shouldn't be too hard to work out)

-Name it whatever you want

-Find the icon you wish to use.

-In the command box type ```
wine <path/to/your/application/
```, so for example if I wanted to launch Morrowind, which is in my home/chris/morrowind folder, I type ```
wine /home/chris/morrowind/Morrowind_Launcher.exe
```


With cedega (Using Point2Play/Cedega GUI) -Method one


-Right click the desktop and click, Create Launcher (Although since you are using KDE, it should be something similar, so it shouldn't be too hard to work out)

-Name it whatever you want

-Find the icon you wish to use.

-In the command box, type ```
cedega --run "FolderName" "ShortcutName"
``` So for example, I wanted to launch City of Heroes, and it was in the "City of Heroes" folder and the shortcut in the GUI was call "City of Heroes" I would type ```
cedega --run "City of Heroes" "City of Heroes"
``` (Note than when launched from a terminal or a launcher, cedega uses global settings, not shortcut specific settings)



With cedega (Command line and GUI versions) Method 2:

-Right click the desktop and click, Create Launcher (Although since you are using KDE, it should be something similar, so it shouldn't be too hard to work out)

-Name it whatever you want

-Find the icon you wish to use.

-In the command box type ```
cedega <path/to/your/application/
```, so for example if I wanted to launch Morrowind, which is in my home/chris/morrowind folder, I type ```
cedega /home/chris/morrowind/Morrowind_Launcher.exe
```.




Putting these shortcuts in the K menu is a very similar process, open the K menu editor (Right click on the K) and choose "Add new item/Launcher", then follow the same instructions. Hope this helps! :)

---

### Post by jrock2004 on 2007-04-05
Thanks that is perfect

---

