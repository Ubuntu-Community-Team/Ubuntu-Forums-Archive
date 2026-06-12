---
title: "launch without terminal"
date: 2006-01-07
forum: General Help
---

### Post by drop_d33 on 2006-01-07
ive installed limewire and azureus. and they are running great. but i have to launch these programs via the terminal.. anybody knows how to create a shortcut so that i would no longer need to go to the terminal to launch these programs... step-by-step please...

---

### Post by akiro.yamamoto on 2006-01-07
Try this...
CODE:
sudo gedit /usr/local/bin/azureus
This will create a file called azureus...
Put this in it 
#!/bin/bash
cd /where/you/have/azureus  [eg. cd /opt/azureus/]
./azureus

Save the file.... then type... sudo chmod +x /usr/local/bin/azureus
To make the file exacutable.
At this point if you <ALT>+<F2> (This is a shortcut to the run dialog)
and type azureus in the run dialog azureus should start.
If you want to create a menu item for it...
sudo gedit /usr/share/applications/azureus.desktop
Input something similar to this...

[Desktop Entry]
Name=Azureus
Comment=Azureus Bittorent Client
Exec=azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;

Modify as necessary. Your Icon entry may not be the same as mine for example.
At this point you should now have a menu entry for Azureus under Applications>Internet.

I hope this helps....
For more in depth help of setting up your Ubuntu System check the links in my sig..

---

### Post by akiro.yamamoto on 2006-01-07
Of course you could use alien to change the azureus.rpm file from the azureus website to a .deb file and then install that... ;)

---

### Post by truthfatal on 2006-01-07
or you could use the "Create Launcher..." command from the right-click menu

---

### Post by MakubeX on 2006-01-07
Or how about using "smeg" or the Application Menu Editor?

---

