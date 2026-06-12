---
title: "Is there a KDE Control equivalent for Karmic?"
date: 2009-12-18
forum: Desktop Environments
---

### Post by deusdiabolus on 2009-12-18
OK.  I would like to turn off the single-click in K3B, and a search of the forums produced [this thread]("http://ubuntuforums.org/showthread.php?t=618401&highlight=K3b+single+click").  I did a whereis in terminal for Kcontrol and got no result, so I tried a sudo apt-get install, which returned the following:  

[I]Package kcontrol is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdelibs4c2a kdebase-workspace-bin
E: Package kcontrol has no installation candidate[/I]

So now I'm wondering if there is anything I can install that would allow me to disable the single-click option in KDE software.  I have tried all the phrases and keywords I can think of both in these forums and in Google.

---

### Post by aveightor on 2009-12-19
If your using kde 4.3, click on the K on the bottom left of the screen. Goto System Settings, Keyboard & Mouse, Select Mouse, check Double-click to open files and folders(select icon on first click)

---

### Post by Zorael on 2009-12-19
I'm assuming you're not using KDE now whatwith the **[COLOR="DarkOrange"][ubuntu][/COLOR]** tag.

You could manually edit **~/.kde/share/config/kdeglobals** and find the line '**SingleClick=true**' and set it to **false** instead. It should be under the **[KDE]** header, if memory serves.

The alternative is to install the new KDE4 settings manager, aptly named Settings Manager (package name **settingsmanager**), but that will pull a whole slew of dependencies you might not really need just to toggle this one setting.

---

### Post by deusdiabolus on 2009-12-19
I'm looking at my kdeglobals file and I don't see a [KDE] header in it.  Can I just add it anywhere in the file or does it need to be in a specific place (top, bottom)?

---

### Post by Zorael on 2009-12-19
Anywhere in it, I suppose. It's in the middle of mine.
```
...

[KDE]
AutoSelectDelay=-1
ChangeCursor=true
DoubleClickInterval=300
ShowDeleteCommand=false
ShowIconsOnPushButtons=true
**SingleClick=false**
StartDragDist=4
StartDragTime=400
WheelScrollLines=3

...
```

---

