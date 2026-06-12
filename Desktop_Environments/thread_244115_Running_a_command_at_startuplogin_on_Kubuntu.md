---
title: "Running a command at startup/login on Kubuntu"
date: 2006-08-25
forum: Desktop Environments
---

### Post by srunni on 2006-08-25
Is there any easy way to run a command at startup or login in Kubuntu? I need to run ```
xmodmap -e "keycode 115=Menu"
``` so that I can use my Windows Key to open the KMenu. Unfortunately, this option gets reset every time I login. Is there any way to automatically run this command in KDE?

---

### Post by janhenderson on 2006-08-26
> **srunni said:**
> Is there any easy way to run a command at startup or login in Kubuntu? I need to run ```
xmodmap -e "keycode 115=Menu"
``` so that I can use my Windows Key to open the KMenu. Unfortunately, this option gets reset every time I login. Is there any way to automatically run this command in KDE?

I'm not sure if this would work but you could try to make changes to this text i just used to answer someone else about starting beagled on kde startup. Modify beagled for what you want. 

use conqueror to go to /home/<your-username>/.kde/Autostart

right-click and choose create link to application...
in the dialog that appears type under the general tab: beagled, then switch to the application tab, and type

Name: beagled
Application: beagled

Then click OK. You should see an icon that says beagled.desktop now in that folder

---

### Post by srunni on 2006-08-26
Well, that's for applications (which I might actually use it for later), but this doesn't seem to explain how I can just run a command. I know it's very simple to do in GNOME from the GUI, but I don't see anything like that in the KDE Control Center (System Settings).

---

### Post by srunni on 2006-08-27
Anyone there?

---

### Post by srunni on 2006-08-27
Hello?

---

### Post by ultranet on 2006-08-27
I had a similar question, and still don't know the answer:

[http://ubuntuforums.org/showthread.php?t=93773](http://ubuntuforums.org/showthread.php?t=93773)

You probably need to add this to some script in /etc folder.

Alternatively, looks like the prior response would let you run your command in a shell script.

---

### Post by janhenderson on 2006-08-27
> **srunni said:**
> Well, that's for applications (which I might actually use it for later), but this doesn't seem to explain how I can just run a command. I know it's very simple to do in GNOME from the GUI, but I don't see anything like that in the KDE Control Center (System Settings).

Just try it. See if it works for your command. I think the "applications" are run in there by a simple command. And post back on whether it does or not.

---

### Post by chavo on 2006-08-27
Just make a script. Paste this into an new file.

```

#!/bin/bash
xmodmap -e "keycode 115=Menu"

```

Now save it as ~/.kde/Autostart/xmodmap.

Next mark it as executable.

```

chmod +x ~/.kde/Autostart/xmodmap

```

You can put shortcuts, links or scripts in the Autostart folder. This script will now run at every KDE login. If there's more stuff you need to run, you can either just add it to this script or make a new one just like it. I like to keep one command per script, it's much easier to troubleshoot that way.

---

### Post by srunni on 2006-08-28
Actually, it was a lot easier than that. I wrote ```
xmodmap -e 'keycode 115=Menu'
``` in Kate, and then saved it as winkey.sh in ~/.kde/Autostart. It worked just fine without any of that bin/bash or chmod stuff.

---

