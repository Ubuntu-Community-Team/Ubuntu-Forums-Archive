---
title: "Adding entries to the Applications menu"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Junosix on 2006-08-18
I'm trying to add a game, Tumiki Fighters, to the Games section of the Applications menu.  At the moment, the game is sitting in /opt/tf and is an executable called tf.  The game needs to have "-res 1024 768" passed to it to run fullscreen so I've made a one-line shell script to call the tf executable with those options added, and that works a treat.  So at the moment, in order to run the game I do this from Terminal:

cd /opt/tf
./tf.sh

I've created a file called tf.desktop and it appears in the Applications menu under Games, but when I click on it I get thrown back out into Gnome and the mouse locks.  If I try to run the game from Terminal without changing directory into /opt/tf and just type "/opt/tf/tf.sh" I get an error saying it can't find a directory (which is a directory that's sitting in /opt/tf)

This is my tf.desktop file:

[Desktop Entry]
Encoding=UTF-8
Name=Tumiki Fighters
Comment=Tumiki Fighters
Exec=/opt/tf/tf -res 1024 768
Icon=/opt/tf/tf_1l.gif
Terminal=false
Type=Application
Categories=Application;Game;

Is there anything that needs to be different in the tf.desktop file to get it to change directory before it runs the program, or do I need to add it elsewhere?

Thanks in advance!

---

### Post by meng on 2006-08-18
I'm not sure, but I'd try two changes to your .desktop file:
1. add
Path=/opt/tf
2. change
Exec=/opt/tf/tf.sh
(I figure you can't break anything by trying.)

---

### Post by crackseller on 2006-08-18
```

[Desktop Entry]
Encoding=UTF-8
Name=Tumiki Fighters
Comment=Tumiki Fighters
Exec=/usr/bin/tf.sh
Icon=/opt/tf/tf_1l.gif
Terminal=false
Type=Application
Categories=Application;Game;
```
I am assuming your start script is in /usr/bin.

---

### Post by Junosix on 2006-08-18
That works a treat :D  Many thanks.

Bizarrely, my machine locked totally after adding the path statement initially.  However, I went back and changed the Exec line to read Exec=/opt/tf/tf -res 1024 768 so totally bypassing the shell file I'd created, and that works perfectly.

Although it does work now, just out of interest why did the machine lock when I tried to open it with the shell file?  The content of tf.sh is simply:

#!/bin/bash
/opt/tf/tf -res 1024 768

Thanks again!

---

### Post by meng on 2006-08-18
I'm not 100% sure from your description if the path statement helped in the end or not. Sorry it locked your machine.

---

### Post by Junosix on 2006-08-18
meng - adding the Path= statement did the trick so thank you for that!  I also had to point the Exec= line to the original executable rather than the tf.sh one I'd created.

---

### Post by Junosix on 2006-08-18
crackseller - the tf.sh file is in /opt/tf along with the game.

All sorted now, but am interested to understand why the machine locked when I asked it to run the executable via the shell file.

---

### Post by Junosix on 2006-08-18
Ah - just realised I might have confused things a bit.  My post listed my Exec= line as reading Exec=/opt/tf/tf -res 1024 768, but prior to that it read Exec=/opt/tf/tf.sh, when I thought that doing it via a shell file would help.

---

