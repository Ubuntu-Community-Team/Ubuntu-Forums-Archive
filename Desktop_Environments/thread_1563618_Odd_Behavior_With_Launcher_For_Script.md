---
title: "Odd Behavior With Launcher For Script"
date: 2010-08-29
forum: Desktop Environments
---

### Post by ubernerd2048 on 2010-08-29
I have a launcher that I made to run the game FEAR in wine. I wanted to add it to the gnome menu, so I wrote the following:

#!/bin/sh

cd ~/.wine/drive_c/Program\ Files/Sierra/FEAR/
taskset -c 1 padsp wine FEAR.exe

and placed it into the directory where FEAR was installed. I set permissions on the file to a+x and verified that it worked perfectly from the terminal. I then added a launcher for the application in the menu with the command "/home/james/.wine/drive_c/Program Files/Sierra/FEAR/launcher".

Here's the weirdness for me. When I run the script from the terminal it works great, when I run it from the launcher in the menu, the game starts but it doesn't share sound so it seems the padsp command is not working then and it's very erratic in performance which is fixed if that taskset command works correctly.

Am I doing something horribly wrong? I've has little to absolutely zero luck getting shell scripts working from the GNOME menu but it seems a bit weird that in the terminal it works perfectly, but in the menu it still somehow runs the game while ignoring all the other commands in that line?

---

