---
title: "Panel stuck in middle of screen compiz &amp; emerald not working on startup"
date: 2010-11-22
forum: Desktop Environments
---

### Post by valhemmer on 2010-11-22
upon restart my panel is stuck in the middle of the screen. Compiz wont run on start up and running it in the terminal gives me this output

________laptop:~$ compiz
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png


but it does work. and running compiz fixes the docky/conky problems i also had, obviously. I can also run emerald --replace to get emerald running and that works fine.

[ATTACH]176305[/ATTACH]

The panel stuck in the middle is the problem causing me the most trouble. Any ideas?
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by valhemmer on 2010-11-22
ok I kinda fixed it by changing the expand value in properties. I liked it better the otherway but this works until i get the actual problem fixed

---

