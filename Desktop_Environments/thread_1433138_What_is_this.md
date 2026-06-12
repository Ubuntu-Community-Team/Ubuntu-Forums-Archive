---
title: "What is this?"
date: 2010-03-18
forum: Desktop Environments
---

### Post by havoc783 on 2010-03-18
I've included a picture, but what I'm looking at live is a green, horizontal cursor that moves back and forth at the top of my desktop. What is it and how do I get rid of it?  This was one of the things I came across after the 9.10 upgrade I did, I also lost sound, if you know anything about fixing that. This is my audio device: 00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2).

Thanks ahead of time. [IMG]http://lh4.ggpht.com/_xGg5BmHbKI4/S6KSLbqMf5I/AAAAAAAAAGY/nlsLJf7aYO4/s800/Green_lines.png[/IMG]

---

### Post by 3Miro on 2010-03-18
Can you right-click and remove it? It should be attached to the panel. You can also try

```
gconf-editor
```

int he terminal for specific options on all panels and applets that you have running.

---

### Post by havoc783 on 2010-03-19
Hi, thanks for the reply, but it's not the panel. I moved the panel to the bottom of the screen and those lines are still there. Any other ideas as to what the lines might be?

---

### Post by stinkeye on 2010-03-19
Someone had similar situation here: [**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1417071&highlight=green+line[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1417071&highlight=green+line")
and solved it by booting into recovery mode and repairing broken packages.

---

