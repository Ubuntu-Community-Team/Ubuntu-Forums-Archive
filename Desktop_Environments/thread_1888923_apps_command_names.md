---
title: "apps command names"
date: 2011-11-30
forum: Desktop Environments
---

### Post by mIXpRo on 2011-11-30
hi, 
i'm using xubuntu 11.10 , and my problem is with : apps command names , 
how can you find them ?? for example the command for chrome is google-chrome %U which i had to google to find it out .

and something else how to move the upper xfce bar down ?


thnx

---

### Post by LewisTM on 2011-11-30
Hello again!

To find the command, you can install a menu editor in XFCE following this [thread]("http://ubuntuforums.org/showthread.php?t=1875258"). It's not trivial.
 
You can also use the Application Finder in Applications/Accessories, also found in the default Xubuntu bottom panel. It's too clumsy to be used like Synapse but it does allow you to drag and drop launchers to the desktop or a panel. From there, you can look a their properties.

To move a panel, you have to go to it's preferences, unlock it and then drag it using the handle on the left.

Cheers!

---

### Post by mIXpRo on 2011-11-30
i have a better idea , 
>  /var/log/dpkg.log 
lists all the packages you've installed , just look for the 
line that says : 
```

"year" "time" status installed [COLOR="Red"]"the binary name"[/COLOR] "version"

```

so now i just have to write some script to list those clearly , maybe i'll write an app :D

---

### Post by LewisTM on 2011-11-30
You don't get the executable name with that, just the package name.

You could go into Synaptic Package Manager, right-click your package and see what file it has installed. That will bring you closer but you will still be uncertain and you will be missing any commandline parameter added in the launcher.

You could also search for .desktop files and look inside with a text viewer/editor.

---

