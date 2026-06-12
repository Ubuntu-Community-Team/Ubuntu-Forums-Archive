---
title: "How do you uninstall compiz/xgl?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by mental_drummer on 2006-06-17
Hello,
I installed compiz/xgl and it works but its buggy n, i think, more trouble than its worth. Can anyone tell me how to uninstall it? Theres plenty on how to install it out there but i cant find any on how to unistall it!
Cheers in advance

---

### Post by nythrix on 2006-06-17
Carefully undo the changes in /etc/X11/xorg.conf file. Depending on your installation method remove/edit any other files you have created/changed (or save them somwhere in case you change your mind), also check System/Preferences/Sessions for leftovers. If you don't remember which files you've added/altered check the guide you've followed during install.

After restart you should be running Xorg. Now launch synaptic and completely remove gnome-compiz, and xserver-xgl.

---

### Post by mental_drummer on 2006-06-17
hmmm, well i thought u might say that! ive restored my xorg.conf file, weirdly, i restarted gnome and compiz was off and everything was back to normal. however, next time i started the computer compiz was back (!). Unfortunately i have forgotten where the guide i used was and i downloaded a script that did it anyway...
its annoying that it was disabled for one session and then its come back again
any ideas? Is there not just some line i can comment in a file somewhere that tells compiz to start - or is that just wishful thinking

---

### Post by nythrix on 2006-06-23
are you sure you can't find that guide anymore? I don't know what that script removed so it's hard to tell. tell me at least what do you run on startup. go to system/preferences/sessions and have a look at the "startup programs" tab. then we'll see...

---

