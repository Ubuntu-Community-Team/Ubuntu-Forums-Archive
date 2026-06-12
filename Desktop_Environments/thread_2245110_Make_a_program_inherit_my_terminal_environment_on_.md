---
title: "Make a program inherit my terminal environment on startup"
date: 2014-09-21
forum: Desktop Environments
---

### Post by dev-c on 2014-09-21
Hi everybody,
 
I  just upgraded to phpstorm version 8 as I was very keen on trying out  the new build-in grunt task runner, but to my great disappointment I  don't seem to be able to get it to work [IMG]http://devnet.jetbrains.com/images/emoticons/sad.gif[/IMG]

 
Whenever  I start phpstorm from my ubuntu 14.04 launcher it complains that grunt  isn't in my system's $PATH. Printing out $PATH in the build-in terminal  confirms this.
However if I start phpstorm directly from a  terminal it seems to inherit the terminal's environment and the $PATH is  set correctly.
 
How can I tell phpstorm to inherit my terminal environment?
 
Here is my phpstorm.desktop file:
 
[Desktop Entry]
Version=1.0
Type=Application
Name=PhpStorm
Icon=phpstorm
Exec=phpstorm
Comment=Develop with pleasure!
Categories=Development;IDE;
Terminal=false
StartupWMClass=jetbrains-phpstorm
NoDisplay=false

 

Anyone has an idea on how to fix this?

 
Much appreciated!
 
mrmister

---

### Post by ian-weisser on 2014-09-21
What is the full path to your phpstorm application?

---

### Post by tgalati4 on 2014-09-21
You could create a script to run the program with the correct environment:

```

#!/bin/bash
#
# Cheesy script to  run phpstorm
# Put in the correct path to phpstorm
/usr/local/bin/phpstorm
exit 0

```

Then create a launcher for the script.

---

### Post by dev-c on 2014-09-23
> **tgalati4 said:**
> You could create a script to run the program with the correct environment:

```

#!/bin/bash
#
# Cheesy script to  run phpstorm
# Put in the correct path to phpstorm
/usr/local/bin/phpstorm
exit 0

```

Then create a launcher for the script.

Unfortunatelly that doesn't seem to work for me. Whenever I try to run a task it still gives me 

```
Cannot run program "grunt" (in directory "/var/www/grunt/"): error=2, No such file or directory
```

Running the same task through the console works fine though. 

These are my .desktop and my launch.sh files:

```

[Desktop Entry]
Version=1.0
Type=Application
Name=PhpStorm
Icon=/home/myusername/.local/share/icons/hicolor/64x64/apps/phpstorm-custom2.svg
Exec=/usr/lib/phpstorm8/launch.sh
Comment=Develop with pleasure!
Categories=Development;IDE;
Terminal=true
StartupWMClass=jetbrains-phpstorm
NoDisplay=false

```

```

#!/bin/zsh
#cheesy script to  run phpstorm
# Put in the correct path to phpstorm
/usr/lib/phpstorm8/bin/phpstorm.sh
exit 0

```

Is it possible the error stems from a bad zsh configuration? Anything I can check?

Thanks for your help guys!

---

### Post by tgalati4 on 2014-09-24
Look through phpstorm.sh and see if there is a configuration problem.  I'm not familiar with the program nor the differences in how zsh and bash handle environment variables.  I do know that anything using /var/www has to have very specific user and permission conditions--part of overall web security.  If you are not the correct user or don't have the correct permissions on /var/www/grunt, then it won't run.

Also what is the difference between *launch.sh* and *phpstorm.sh*?

---

### Post by dev-c on 2014-09-24
I got it to run! Kinda... I got fed up with trying to make it work in my zsh environment so I slapped my PATH variables on every bashrc or profile file I could get my hands on and behold... it works. 
It's not pretty and I still need to source my .zshrc file so I won't have to update my PATH in several files, but that I can manage :)

Thank you!

---

