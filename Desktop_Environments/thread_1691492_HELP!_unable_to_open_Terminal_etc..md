---
title: "HELP! unable to open Terminal etc."
date: 2011-02-20
forum: Desktop Environments
---

### Post by DrKerberos on 2011-02-20
i was playing around trying to install various themes etc, then ran into the animated pointer problem with 10.04
Tried a couple of tutorials and none worked. restarted and now i'm unable to open much of anything except firefox. (no terminal, no system monitor, can't modify screenlets which i just installed, can't modify themes, etc - the icons are there and the panel says its starting the app but it never happens) I think it may be a result of trying to add cursor theme to usr/share/icons or possibly ldconfig

so uh...yeah HELP!!

---

### Post by PaulReaver on 2011-02-20
you can do some serious damage with ldconfig :(

start smallest one first....
do you know exactly where you installed the cursor theme???

---

### Post by DrKerberos on 2011-02-20
tried /usr/share/icons and /home/kerb/.icons
already removed the one from /usr/share/icons by going through 10.04 cd boot

---

### Post by DrKerberos on 2011-02-20
was able to change theme (right click backgroud>change background>theme>ambient) once theme changed from custom cursors, I then deleted folder with cursor theme (but left /.icon)

---

