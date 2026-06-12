---
title: "Shell script help - launching program"
date: 2009-06-15
forum: General Help
---

### Post by Aenima99x on 2009-06-15
Been tearing my hair out with this one and hoping for some help...

I'm just basically trying to launch a script that will kill XBMC and then restart it...
```

#!/bin/bash
killall xbmc
xbmc &

```

I have a button mapped on my remote to launch the script and it won't launch. However if I launch the script manually or run in a terminal, it works fine. I've got another script that does work, but it just calls eject -T. I've narrowed it down to that any actual graphical programs won't launch from the script (I've tried just putting firefox in the script). Any ideas? :(

---

### Post by munky99999 on 2009-06-15
so like.

sh mybashscript.sh

or whatever works fine. You simply want the script on your desktop which will be executable?

chmod it with u+x

In all honesty I have a couple bash scripts on my desktop I cant get to be executable neither. It's an odd thing. The closest I have come was getting them to work until reboot. Which kinda sucked :(

---

### Post by Aenima99x on 2009-06-15
Not exactly - here's how it goes...
1. LIRC daemon is running
2. IRexec daemon is running with the variable /home/xbmc/.lircrc
3. The "DVD" button on my Harmony remote calls the .lircrc file which has the following config set inside 
```

begin
prog = irexec
button = DVD
config = /home/xbmc/Scripts/XBMC.sh
end

```

I know it's not a problem with LIRC because I can see the button presses registering in IRW.
I know it's not a problem with the script because it works when I manually run it.

So for some reason, the script will not launch when called usign LIRC. I though it might be a rights problem, but the other script I use launches fine. So that's what led me to believe that for some reason when using LIRC to launch the script, it can't execute graphical programs?

---

