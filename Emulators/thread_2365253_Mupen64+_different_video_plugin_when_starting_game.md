---
title: "Mupen64+ different video plugin when starting games than by console"
date: 2017-07-04
forum: Emulators
---

### Post by alexander46 on 2017-07-04
-Kubuntu 16.10-

When starting Mupen64+ and selecting game from the console, the plugin chosen in the configuration (glide64) starts.
But when I instead run a gamefile without the console a different video plugin is chosen (rice), which apparently doesn't work for the games

Any suggestions appreciated!

Many thanks

---

### Post by deadflowr on 2017-07-04
Never tried it, but how do you start a game without a console?
(Or maybe I have, but never knew!)

---

### Post by alexander46 on 2017-07-05
As far as I remember, i just double-clicked the .n64 file and the mupen window -video (not the console) opened immediatly, 
or
i chose: open this type of file with mupen64+ and then the described event happened...

Greetings

---

### Post by deadflowr on 2017-07-06
So I guess by console do you mean mupen64plus-qt?
Or another frontend, maybe?

I see they added a launcher desktop files to 16.04 which allows you to simply start any n64 file.
It runs the simple mupen64plus command, which takes on whatever the mupen64plus.cfg has set for configurations.

Mupen64plus-qt has it's own configuration file which uses it's own settings.
Both configuration settings are in ~/.config/mupen64plus.

---

### Post by alexander46 on 2017-07-06
Yeees!!... it worked!
Brilliant. 
Mupen64plus-qt has got two config. files! One is for the -qt interface and one is separate Mupen64plus without the suffix.
Was guessing thats the physics but didnt know accessing the non-interface settings would be that easy/obvious. Many thanks!

...just hope know, the controller config is not non-adapted (from -qt interface launching to plain non-qt software) as well. :)

Thanks a lot! Nice help!
Greetings

[PS: pls check my other topics
1) [https://ubuntuforums.org/showthread.php?t=2365094](https://ubuntuforums.org/showthread.php?t=2365094)
2) [https://ubuntuforums.org/showthread.php?t=2364739](https://ubuntuforums.org/showthread.php?t=2364739)
3) ["]https://ubuntuforums.org/showthread.php?t=2365168 ]]("https://ubuntuforums.org/showthread.php?t=2365168)

This topic is closed then.

---

