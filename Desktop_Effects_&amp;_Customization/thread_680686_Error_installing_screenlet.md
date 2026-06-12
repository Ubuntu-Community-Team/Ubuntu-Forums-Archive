---
title: "Error installing screenlet"
date: 2008-01-28
forum: Desktop Effects &amp; Customization
---

### Post by TRANQU111TY on 2008-01-28
I downloaded the Net Monitor screenlet [http://gnome-look.org/content/show.php/Net+Monitor+%28Screenlet%29?content=72013](http://gnome-look.org/content/show.php/Net+Monitor+%28Screenlet%29?content=72013) and when I get to System --> Preferences --> Screenlets ,click on 'Install Screenlet ...' inside the Screenlets Manager and direct it to the '72013-Netmonitor.tar.gz' I get this error:
```

Invalid archive. Archive must contain a directory with the screenlet's name.
```
Everything seems to be in the archive and I'm running Screenlets Manager 0.1.

EDIT: I also have another problem with Screenlets. This error comes up only the first time on every boot when I open Screenlets Manager:
```

Unable to connect or launch daemon. Some values may be displayed incorrectly.
```

And my screenlets don't load up on startup even though I have ticked 'Automatically start at login'.

---

### Post by Ub1476 on 2008-01-28
Install Screenlets-manager 0.0.12. The previous developer doesn't have time to work on it, so another guy grapped it and has been working on it since then. You can get it [here]("http://gnome-look.org/content/show.php/Screenlets+0.0.12+?content=73346"). Remember to remove Screenlets-manager 0.0.10 before installing this one.

---

### Post by TRANQU111TY on 2008-01-28
OK just to make sure I'm uninstalling correctly:
```
cd <name of directory I untarred 0.0.10 screenlets>
sudo make uninstall
sudo make menu uninstall
```
Seemed to go well except in the 'Applications' and 'System' --> 'Preferences' menu the Screenlets folders and shortcuts are still there. Have I done it correctly? Is it safe to install 0.0.12?

---

### Post by Ub1476 on 2008-01-28
You can test by running screenlets-manager in the terminal:

```
screenlets-manager #might be without s
```

If you receive errors like could not find "...",  then it's removed!:)

---

### Post by jryprt on 2008-01-28
[This](http://ubuntuforums.org/showthread.php?t=614031) guide help me install screenlets . After you get the Screenlets Manager  & The  .screenlets folder 
then download the screenlet & right click it & extract it than move it to the .screenlets folder it will show up in the manager.

---

### Post by TRANQU111TY on 2008-01-29
How do I remove the shortcuts in the Applications menu for good? They were just left over from the 0.0.10 Screenlets.

EDIT:Also I have this error when I'm opening Screenlets Manager:
```
Automatic creation failed. Please manually create the directory:
/home/j/.config/autostart/
```
I have tried to create the folder using the terminal but it's telling me it already exists. I have check the hidden folders but there is still no autostart dir. It's really bugging me, what to do?

---

