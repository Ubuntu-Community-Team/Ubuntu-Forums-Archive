---
title: "cannot launch shellscript from desktop or unity"
date: 2012-05-15
forum: Desktop Environments
---

### Post by mashshuu on 2012-05-15
[Running 12.04 64 bit]
I am trying to launch a java app(Minecraft) and I have a shell script that works just fine.

```
#!/bin/bash
 
export LD_LIBRARY_PATH="/usr/bin/java/lib/amd64"
java -Xmx1024M -Xms512M -cp /home/[]/Games/minecraft.jar net.minecraft.LauncherFrame
```

when I open a terminal and go to the folder and run it everything works just fine. 
However if I double click on the file in nautilus and click either "run" or "run in terminal" nothing happens.

I also created a .desktop file for it(more of copied)
```
[Desktop Entry]
Name=Minecraft
GenericName=Game
Comment=Minecraft!
Keywords=craft;minecraft;mine;game;fun
Exec=/bin/bash /home/[]/Games/Minecraft
Terminal=false
Type=Application
StartupNotify=true
Icon=/home/[]/Games/minecraft.jpg
```
which also does not work

I can paste /bin/bash /home/[]/Games/Minecraft into a terminal and it will work just fine so I am certain its not an issue there.

---

### Post by billyseth on 2012-05-15
did you make it executable? if it is marked as executable, what output do you get when you just run /home/[]/Games/Minecraft?

---

### Post by mashshuu on 2012-05-15
> **billyseth said:**
> did you make it executable? if it is marked as executable, what output do you get when you just run /home/[]/Games/Minecraft?

yes it is and

> when I open a terminal and go to the folder and run it everything works just fine. 


[edit]

I slept on it and i realized my java path isn't being set correctly so I just used a direct link to it in the script and it works now.

---

