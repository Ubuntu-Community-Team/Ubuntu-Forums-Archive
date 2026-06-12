---
title: "Portal 2 not working under ubuntu 14.04"
date: 2016-03-10
forum: Gaming &amp; Leisure
---

### Post by Flying_Lynx on 2016-03-10
Every time I try to load Portal, I get the following errors:
[TABLE="class: outer_border, width: 500"]
[TR]
[TD][I]libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  80
  Current serial number in output stream:  81
Game removed: AppID 620 "Portal 2", ProcID 6158 [/I][/TD]
[/TR]
[/TABLE]

I have heard that there are something like colliding drivers from mesa and old steam libs, so I applied the solution posted below, because the errors seems to be pretty alike and it was the only relevant help that showed up in google...
[URL="http://askubuntu.com/questions/614422/problem-with-installing-steam-on-ubuntu-15-04"]
http://askubuntu.com/questions/614422/problem-with-installing-steam-on-ubuntu-15-04[/URL]

But no change, the errors remain the same. By the way I only changed to Ubuntu Linux a few months, so I'm pretty newbie.

---

### Post by efflandt on 2016-03-12
I don't have anything with modern AMD graphics, so I cannot help you on that with specifics. But I had heard that initially for Steam itself to work easiest with proprietary AMD drivers you had to install Steam before installing AMD drivers or you might be missing some 32-bit libraries (".so" files that are similar to ".dll" files in Windows). And in general, Steam may contain older libs that may conflict with newer libs in Linux or with graphics drivers, even though Linux Steam was originally developed in Ubuntu (12.04).

Have you checked the Steam for Linux forum [http://steamcommunity.com/app/221410/discussions/](http://steamcommunity.com/app/221410/discussions/) which has a sub forum for AMD Graphics Cards?

Nvidia graphics and drivers seem to work best for Linux Steam currently. But even that trips up sometimes. In one case a Linux kernel update did not work with Steam and a temporary solution was to boot an older kernel until a newer kernel was released that corrected the problem. And more recently Source games would fail when they could not figure out which GL version a new nvidia driver was (thought GL version was 0.0.0 when looking for at least 2.0.0). Although, that was an easy fix (once you found it) to add a launch option for the game to ignore the GL version.

One way to tell if your graphics drivers are installed correctly is to look through the output of glxinfo (glxinfo | less) in a terminal window and see if that shows "direct rendering: Yes" and your graphics driver farther down. If you do not have glxinfo command, install mesa-utils (blindly type your password when sudo asks for it):```
sudo apt-get update && sudo apt-get install mesa-utils
```

---

