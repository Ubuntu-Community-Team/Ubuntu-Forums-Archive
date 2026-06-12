---
title: "Nexuiz res. problem when loading from shortcut"
date: 2008-05-02
forum: Gaming &amp; Leisure
---

### Post by spadewarrior on 2008-05-02
Nexuiz loads fine if I manually enter its directory and load nexuiz-linux-686-sdl, but if I make a link for this, and put it on the desktop then it loads into a resolution I can't display and I have to restart GNOME. 

Any ideas why?

---

### Post by Perfect Storm on 2008-05-02
It can't properly find the path of the diffrent files.
Make a script and then link the script to eg. a launcher - also when you're at it you can put enable/disable compiz into the script to get better performance.

---

### Post by spadewarrior on 2008-05-02
Thanks for your response. I don't really know how to make a script. 

Is there a tutorial I can follow?

---

### Post by Perfect Storm on 2008-05-02
```
[size=1]cd <where you want the script placed>
nano Nexuiz-launch.sh[/size]
```

add:

[b][size=1] #!/bin/bash

metacity --replace &

cd <into nexuiz directory>
./nexuiz-linux-686-sdl

compiz --replace &[/size][/b]

save [ctrl]+[o] and Exit [ctrl]+[x]
Note the script will disable compiz, then run the game, when exiting the game it will start compiz up again (this script works only on gnome).

```
[size=1]chmod +x Nexuiz-launch.sh[/size]
```

---

### Post by spadewarrior on 2008-05-02
Excellent, that worked perfectly. Thanks!

---

