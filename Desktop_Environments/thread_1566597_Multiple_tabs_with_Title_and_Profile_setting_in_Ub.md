---
title: "Multiple tabs with Title and Profile setting in Ubuntu GNOME Terminal"
date: 2010-09-02
forum: Desktop Environments
---

### Post by tkhans on 2010-09-02
To get multiple tabs, with different Title on Tabs using Profiles within a single Gnome Terminal do the following:

You can create a Profile to be loaded with the Script as well so that the same setting of the Gnome terminal can be loaded, example how large the screen you want, etc.

Creating Profile:
Open Gnome Terminal
File, New Profile, Profile name: = example R1
change the setting as required:
You can change Default size of the screen as well - (Within General Tab)

Once the Profile setting are done, Select Close to return back to the Gnome Ternimal.

Create a Text file and save this with ".sh" extension, e.g. telnet.sh

Enter the following script:
###################

#Done by TK 26 Sug 2010
gnome-terminal  --tab-with-profile=R1 --title=R1 --tab-with-profile=R2 --title=R2

###################

When the above file is saved, clicking on the file will open a Terminal with multiple tabs.

PS: If you using Dynagen and want to load say Router R1 within the localhost  4001 enter the following within the "Title and Command" tab within the  Gnome Terminal:  telnet localhost 4001
Repeat the above for other routers:
Also, if you configure the above, make sure Dynagen is running and the router have been started within Dynagen.

---

