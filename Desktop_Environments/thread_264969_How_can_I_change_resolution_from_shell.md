---
title: "How can I change resolution from shell?"
date: 2006-09-25
forum: Desktop Environments
---

### Post by jeppester on 2006-09-25
I installed a nice little game called "Soldat" on my ubuntu via wine, it works fine but when I quit the game, the resolution is 640*480 which is kinda irritating.
I made a shell-script for the game so if there is a way to change the resolution via the shell, I can fix the problem. I just need to know how to change resolution via a shell-command.

---

### Post by Jasper84 on 2007-01-26
Hi i was also trying to get soldat to work. Found for changing resolution:
xrandr -s 1280x1024
(xrandr -q gives available resolutions)

I didnt get soldat to work properly though. It installed well, and started up fine, but framerate is horrendously bad, and text during play is screwed up. I think its not using the graphics card properly. (Also sound messed up, but i think a consequence of other problems)
Can anyone help with that? I am planning to do some more websearching also.

---

