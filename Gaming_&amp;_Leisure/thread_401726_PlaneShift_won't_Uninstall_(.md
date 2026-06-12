---
title: "PlaneShift won't Uninstall :("
date: 2007-04-04
forum: Gaming &amp; Leisure
---

### Post by puppyfarts on 2007-04-04
I managed to install PlaneShift (+2 points for me), but when I try to open it in Applications > Games, I get the following:

Failed to execute child process "/opt/PlaneShift/psclient" (Permission denied)

I managed to install it again and could actually open it, but I decided to uninstall that, too.

How do I get it out of opt?

---

### Post by puppyfarts on 2007-04-05
Bump. :(

---

### Post by GiantRobot on 2007-04-05
It looks like the permissions are messed up for your installation.  I know I had the same thing with Vendetta Online.

Just go in as root and uninstall the game.  There also might be an uninstall script with your game aswell so you could just run that as root.

---

### Post by Feba on 2007-04-05
try ALT+F2 "gksudo nautilus", put in your password at the prompt, then navigate to your PS directory and click "PS Uninstall" or whatever the name is.

---

### Post by puppyfarts on 2007-04-06
I did ALT+F2.
The PlaneShift uninstall thing says, 
There was an error launching the application.
Details: Failed to execute child process "/opt/Planeshift/uninstall" (No such file or directory)

Yesterday I think I finally got it uninstalled by going into terminal doing chmod 777 to the entire folder, but there's still a few folders and the uninstall/client/setup file.

Is it maybe already uninstalled, and these are just some leftover files?
It still shows up in Applications > Games, though.

---

