---
title: "Compiz/AWN Toggle script"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by Dgurion on 2007-07-08
I'm trying to write a script that will turn off compiz and AWN and load metacity, and will also turn compiz and awn back on when I run it again.

I have gotten it to the point that it will close AWN and load metacity, but I cant get it to load compiz and then AWN, I think that the script stops since the "compiz --replace" command never actually ends so that it cant go on to the next step and load AWN, is there a way to do that ?

Any help would be appreciated I'm new to Linux and especially to any kind of script writing...

Here is the script I've got so far:

```
#!/bin/sh

# click to start, click to stop
if pidof compiz.real avant-window-navigator awn-applet-acti; then
 killall avant-window-navigator awn-applet-acti
 exec metacity --replace
else
 exec compiz --replace
 exec avant-window-navigator
fi
```

---

### Post by kirkquitar on 2007-10-18
I realize that this is an old post, but if you use the exec command, the script stops once that command has been complete, try this

```
#!/bin/sh

# click to start, click to stop
if pidof compiz.real avant-window-navigator awn-applet-acti; then
 killall avant-window-navigator awn-applet-acti
 exec metacity --replace
else
 compiz --replace
 exec avant-window-navigator
fi
```

Kirk

---

