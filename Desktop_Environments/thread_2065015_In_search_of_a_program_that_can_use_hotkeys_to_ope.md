---
title: "In search of a program that can use hotkeys to open multiple applications at once."
date: 2012-09-30
forum: Desktop Environments
---

### Post by Gut on 2012-09-30
I've been using Ubuntu 12.04 LTS for about 5 months now and I'm trying to find a program that can allow me to use a hotkey to open several applications at once, such as Thunderbird, Firefox, etc. and have them placed on specifed desktops that I move them on and it can remember what desktop I had them set to. Are there any applications like this?

---

### Post by stinkeye on 2012-09-30
For compiz set the workspace for an app with...
ccsm > place windows > fixed placement
[ATTACH]224907[/ATTACH]  [ATTACH]224906[/ATTACH]

For the shortcut key just create a bash script something like...
```
#!/bin/bash
firefox &
gedit
```

Then add a keyboard shortcut pointing to the script.
[ATTACH]224905[/ATTACH]


You could also create a launcher for the script by adding it to alacarte (main menu)
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=11458230&postcount=4[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11458230&postcount=4")

---

