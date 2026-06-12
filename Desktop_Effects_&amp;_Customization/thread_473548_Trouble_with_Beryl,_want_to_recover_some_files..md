---
title: "Trouble with Beryl, want to recover some files."
date: 2007-06-14
forum: Desktop Effects &amp; Customization
---

### Post by Pathfinder007 on 2007-06-14
Hi, 
I installed Beryl and it wasn't crashing my computer or anything.
I fiddled around with the settings and disabled the nvidia video driver, coz it wasn't fully working and I wanted to update it. The problem with the Nvidia driver was that whenever I enabled 3D desktop manager, compiz or Beryl I just lose all the title bars, everything else work great though.
Now every time I login to Ubuntu I get a white cube and nothing else, just pure white. :(
I want to switch back to metacity and backup some files and reinstall Ubuntu.
What can I do?
I am a bit of a noob at linux.
Please help me!
Thank you.

---

### Post by zero244 on 2007-06-15
Put this line in the Screen section of your xorg.conf file
Option "AddARGBGLXVisuals" "True
Usually just under your Monitor line but before you color depth line.
Also make sure Window Decorator is checked in beryls window manager settings.

---

### Post by zero244 on 2007-06-15
oops this is the line
Option "AddARGBGLXVisuals" "True"
Some people dont need this line some people do.

---

