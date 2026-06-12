---
title: "Troublle with 3D acceleration"
date: 2006-10-02
forum: Desktop Environments
---

### Post by kamillozo on 2006-10-02
I've got problem with 3d acceleration. Every time I try to run a game that uses acceleration it crasches.
The problem have started when x-moto game crushed during playing. The only thing I could do at that time was 'hard reset'. After that the x-server couldn't get to work properly after every startup - it showed black screen only.
I've managed to get it to work by reconfiguring xserver (sudo dpkg-reconfigure xserver-xorg).
After that reconfiguration the xserver started to work properly but I didn't have an acceleration in 3D games like x-moto, planet-penguin racer. I've decided to use an earlier copy of xorg.conf (backuped before this event with x-moto crush). It seemed that it worked because i could play x-moto for a while... but then it crushed again. Fortunatelly the xserver is still alive :) That happens every time I run a 3D game.

My question is: howto reconfigure/enable acceleration (I used Ati driver included in repos)?

---

