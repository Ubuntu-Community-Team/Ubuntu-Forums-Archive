---
title: "Auto change screen res?"
date: 2007-01-14
forum: Gaming &amp; Leisure
---

### Post by PisstMSTRCHIEF on 2007-01-14
Frozen throne runs beautifully under wine. 

But, I use a wide screen monitor; 1440x900, witch is not an option in frozen throne.

My question is- Is there a way for the resolution automatically change back to wide once frozen throne is closed? 

Or, a way for wide screen res in Frozen throne?

I'm running Ubuntu Edgy 6.10, if you need any more info don't hesitate to ask.

Any and all help/comments are appreciated.

---

### Post by Fitzy_oz on 2007-01-15
Not really, I have this problem with CS:S and with GTA:Vice City if it crashes I'm stuck with the resolution that the game was runnning in and have to manually change it.

Which version of wine are you using? the Ubuntu (09.22) or the latest from winehq.org (0.927)?

---

### Post by blackened on 2007-01-15
Have you tried running your games through a shell script and then at the end of the script, after the game exits, use xrandr to change back to your preferred resolution? This isn't gonna be exact because everyone's xorg is different, but this is basically what I mean. I don't even know if this will work, but it's worth a shot:
```
#!/bin/sh

#First start the program:
wine /path/to/windows/executable

#Wait until after the program exits to finish the script:
wait

#After the program exits it should fire off this code to reset
#your screen resolution:
xrandr -s 0
```

Type xrandr in the terminal to see a list of possible resolutions.  Change the script to reset it to the proper number with xrandr -s *number of proper resolution*

If this doesn't work properly, then you might try changing the resolution to one of the non-optimum first, then back to your preferred resolution.

---

### Post by Fitzy_oz on 2007-01-15
> **blackened said:**
> Have you tried running your games through a shell script and then at the end of the script, after the game exits, use xrandr to change back to your preferred resolution? This isn't gonna be exact because everyone's xorg is different, but this is basically what I mean. I don't even know if this will work, but it's worth a shot:
```
#!/bin/sh

#First start the program:
wine /path/to/windows/executable

#Wait until after the program exits to finish the script:
wait

#After the program exits it should fire off this code to reset
#your screen resolution:
xrandr -s 0
```

Type xrandr in the terminal to see a list of possible resolutions.  Change the script to reset it to the proper number with xrandr -s *number of proper resolution*

If this doesn't work properly, then you might try changing the resolution to one of the non-optimum first, then back to your preferred resolution.

Seems like everyday I'm learning a sneaky new trick - Cheers man :)

---

### Post by blackened on 2007-01-15
No worries, hope it was useful.

---

### Post by PisstMSTRCHIEF on 2007-01-15
LoL, I think I did something wrong-

The resolution changed to Frozen throne's default then, immediately after, back to wide while the program was still running-:lol:

---

### Post by blackened on 2007-01-16
I figured that might be a problem. The wait command in the script waits till all background processes started by that shell have exited and then continues with the script. The problem with this is that some programs start, but then immediately give a return code like they have exited when they really haven't. This means that what the shell sees is that all subprocesses have closed and the script continues. I'm sure there's a workaround. I'll just have to poke for it.

---

### Post by PisstMSTRCHIEF on 2007-01-16
Thanks though, I always like to learn new commands; I'll be messing with it as well.:)

---

### Post by Phesto on 2007-01-16
Try changing the winecfg to run in windowed mode at the resolution you have warcraft III set to. I use a script to change my resolution then launch wow and then change my resolution back. This should work for warcraft3 as well. I run wine in windowed mode with a resolution of 1280x1024, since i use twinview and two monitors wow doesn't like what it thinks is one widescreen display. So this is what i use:
```
#!/bin/sh

xrandr -s 2560x1024

wine /games/World\ of\ Warcraft/WoW.exe -opengl

xrandr -s 3200x1600
```

that sets my resolution to two 1280x1024 displays which is what i run wow at. Then wow starts up on the screen windowed but at what looks like fullscreen. It doesn't process the next part changing my resolution back to two 1600x 1200 screens until wine actually stops since it's windowed.

---

