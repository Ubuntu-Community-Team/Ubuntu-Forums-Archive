---
title: "No icon for running Java application in Unity"
date: 2011-05-16
forum: Desktop Environments
---

### Post by cdysthe on 2011-05-16
Hi, 

I'm running a Java application (JBidWatcher) quite often. I've added it to the menu using the main menu editor using a custom icon. It can be launched from the Unity launcher and the correct icons shows there, but there's no icon for the running task in the launcher, only a question mark. How can I get the application icon to show for the running task as well?

---

### Post by wojox on 2011-05-16
How was it installed in the system? Your home directory or in the system?

---

### Post by cdysthe on 2011-05-16
> **wojox said:**
> How was it installed in the system? Your home directory or in the system?

It's simply a jar file downloaded from the JBidWatcher site. They do not have an installer for Linux (as far as I know). I put it in a folder in my home directory and launch it from a menu entry with a custom icon pointing to a script containing:

java -Xmx512m -jar ~/.jbidwatcher/JBidwatcher.jar

This has worked fine for years under Gnome, but not in Unity it seems. It launches fine and show up with the icon in Unity, but the running task doesn't have the icon.

---

### Post by wojox on 2011-05-16
Go into 
```
.local/share/applications/
```

See if there is a .desktop file for your Launcher. If there is what ever name it is, open with gedit and post the results.

---

### Post by cdysthe on 2011-05-16
> **wojox said:**
> Go into 
```
.local/share/applications/
```

See if there is a .desktop file for your Launcher. If there is what ever name it is, open with gedit and post the results.

There's a desktop file called "JBidWatcher" in that directory. It contains the following:

[http://pastebin.com/kachAdQk](http://pastebin.com/kachAdQk)

---

### Post by wojox on 2011-05-16
```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Name[en_US]=JBidWatcher
Exec=/home/christian/.jbidwatcher/jbidwatcher.sh
Comment[en_US]=eBay Auction Sniper
Name=JBidWatcher
Comment=eBay Auction Sniper
Icon=/home/christian/Pictures/Graphics/Icons/jbidwatcher.png
```

You had two icon references in there. I took one out so edit that file again and put this code in and save. Then take the file and drag and drop into the Dock.

---

### Post by cdysthe on 2011-05-17
> **wojox said:**
> ```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Name[en_US]=JBidWatcher
Exec=/home/christian/.jbidwatcher/jbidwatcher.sh
Comment[en_US]=eBay Auction Sniper
Name=JBidWatcher
Comment=eBay Auction Sniper
Icon=/home/christian/Pictures/Graphics/Icons/jbidwatcher.png
```

You had two icon references in there. I took one out so edit that file again and put this code in and save. Then take the file and drag and drop into the Dock.

Thanks. That worked!

---

