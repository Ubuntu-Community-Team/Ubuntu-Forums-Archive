---
title: "Can't get joystick working"
date: 2006-01-19
forum: General Help
---

### Post by Sureshot324 on 2006-01-19
I have a MS sidewinder precision pro that plugs into the game port, which is on my audigy 2 zs.  I tried following this guide for analog joysticks:
[http://www.ubuntuforums.org/showthread.php?t=55173&highlight=joystick](http://www.ubuntuforums.org/showthread.php?t=55173&highlight=joystick)
The script seems to run fine and it does add the /dev/js0, but jscalibrator won't work (can't read /dev/js0) and the joystick doesn't do anything in tuxracer.  Can anyone help?

---

### Post by keithjr on 2007-02-11
I've tried the same instructions with my Sidewinder FF Pro joystick, and also had no good results.

Also this sounded like it should have worked:

[http://ubuntuforums.org/showthread.php?p=2071637](http://ubuntuforums.org/showthread.php?p=2071637)

Try that and see if manually loading all of those modules has any effect.  

Neither of these fixes helped me. If it doesn't help you either, I think it's safe to say that the Sidewinder joysticks are not supported in Ubuntu (I'm using 6.10). The kernel modules do not create the device nodes, and if manually created, they do not work. I haven't found anybody on the forum yet who has had this problem solved, and it seems to be fairly common.

---

