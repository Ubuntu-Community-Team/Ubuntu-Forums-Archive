---
title: "Script?"
date: 2009-02-17
forum: General Help
---

### Post by MichaelGriffin on 2009-02-17
Is it possible to make a script or something that can run commands through the terminal with me just having to click the script on my desktop?

Like I want to just click a file, have it open the terminal, and a preset list of command will be run, and have it close the terminal. If there is can someone teach me how to make it or post an example here? Thank you.

---

### Post by kerry_s on 2009-02-17
```
#!/bin/sh
xterm -hold -e command
```

don't forget to make it executable.

"man xterm" to learn more.

---

### Post by MichaelGriffin on 2009-02-17
Im confused I tried this

```
#!/bin/sh
xterm -hold -e command gnome-terminal
xterm -hold -e command cd TibiaWIN
xterm -hold -e command wine tibia.exe engine 1
```

and I tried this:
```
#!/bin/sh
xterm -hold -e command cd TibiaWIN
xterm -hold -e command wine tibia.exe engine 1
```

And lastly this:
```
#!/bin/sh
xterm -hold -e cd TibiaWIN
xterm -hold -e wine tibia.exe engine 1
```

Needless to say nothing happened, and I also made them executable. :S

---

### Post by mikewu on 2009-02-17
If its only a couple of commands, use gnome-terminal with the -x flag. 

#! /bin/sh
gnome-terminal -x xmessage "Hello World"; xmessage "Second String"; xmessage "Third String"

The shell will exit when the commands finish.

If you have a long list of commands, I would recommend putting them in another shell script and then executing that script in the desktop shortcut.

#! /bin/sh
gnome-terminal -x script.sh

---

### Post by kerry_s on 2009-02-17
> **MichaelGriffin said:**
> Im confused I tried this

```
#!/bin/sh
xterm -hold -e command gnome-terminal
xterm -hold -e command cd TibiaWIN
xterm -hold -e command wine tibia.exe engine 1
```

and I tried this:
```
#!/bin/sh
xterm -hold -e command cd TibiaWIN
xterm -hold -e command wine tibia.exe engine 1
```

And lastly this:
```
#!/bin/sh
xterm -hold -e cd TibiaWIN
xterm -hold -e wine tibia.exe engine 1
```

Needless to say nothing happened, and I also made them executable. :S

i see, details make the difference, i don't think you need a terminal for that.

```

#!/bin/sh
cd ~/.wine/drive_c/Program\ Files/TibiaWIN
wine tibia.exe engine 1

```

are you sure on your locations? on this thread it has different paths than your using in the scripts:
[http://ubuntuforums.org/showthread.php?t=515545](http://ubuntuforums.org/showthread.php?t=515545)

---

### Post by MichaelGriffin on 2009-02-17
Yeah that person just had his saved on his windows partition I have mine on my Ubuntu thats why the path is different. thanks though I think I might be able to get it now.

Solved:
```
#!/bin/bash
cd ~/TibiaWIN/
WINEDEBUG=-all wine Tibia.exe engine 1
```

Thanks :D

---

