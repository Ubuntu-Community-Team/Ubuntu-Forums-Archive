---
title: "XGL/Compiz problem"
date: 2006-09-12
forum: Desktop Environments
---

### Post by jman2807 on 2006-09-12
I recently installed xgl on ubuntu dapper drake 6.06 and I followed the guide located here: [http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)


And when I start linux with the xgl session gnome just loads normally so I went to /usr/bin/startcompiz and it gave me this error

gnome-window-decorator: no process killed
compiz: Couldn't load plugin 'gconf'

Any ideas what exactly is wrong?

Thanks in advance.

---

### Post by The Pinny Parlour on 2006-09-12
First make sure you have the latest updates

Firstly, open Synaptic Package Manager and go to "Settings/Preferences/Columns and Fonts"  Put a tick (if it doesn't already) in "Install Version" and Available Version"
Now search for "compiz" Make sure "csm" is 0.10 and compiz-plugins are 0.22, if not update them and try again.

BTW it's: /usr/bin/start-compiz

---

### Post by frequenicity on 2006-09-12
(sudo) gedit your /usr/bin/start-compiz and take out (listed with the other plugins) "gconf" since compiz no longer uses that plugin.

---

### Post by jman2807 on 2006-09-12
Ok everything is up to date and i edited out the gconf thing but now when i rush start-compiz all the windows just lose the title bar and nothing will move. This is my start-compiz file:

#!/bin/sh
killall gnome-window-decorator
wait
gnome-window-decorator & DISPLAY=:1 LD_PRELOAD=/opt/mesa/libGL.so.1.2 compiz --replace

---

### Post by frequenicity on 2006-09-12
Try terminal command 

Code:
nohup cgwd --replace

---

