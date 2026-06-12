---
title: "fluxbox startup fails"
date: 2008-01-17
forum: Desktop Environments
---

### Post by danifodor on 2008-01-17
Hi!

I have the following problem: I try to start adesklets automatically and not shure whether ~/.fluxbox/startup is in use. I have the conky & line in the startup file and if I comment it out it does not start. This is fine so far. But... 
I added adesklets & below conky and it does not run automatically. I have to run in from terminal and then it works fine. I also cannot set background form this file (fbsetbg -f ... does not work, only form init file). I also tried to make a simple .xsession file with the following content:
```

#!/bin/sh
conky & # and/or adesklets &
exec startfluxbox

```
It does not work. Apparently this file is (also?) not used.

Could anyone help please?

Cheers 

Daniel

---

### Post by TeaSwigger on 2008-01-17
Hello Daniel,

I'm still a novice in things Fluxbox (and Linux for that matter) but to comment... When you create ~/.fluxbox/startup, it should be ran, yes. I don't know the proper method to start specific adesklets.

Here is my ~/.fluxbox/startup at the moment:

```
fbsetbg -f /home/teaswigger/Pictures/wallpapers/fluxbox/fluKbuntu2.png

/usr/bin/klipper &

exec /usr/bin/fluxbox
```

That's it, and all works as specified. The image set in startup is only visible as Fluxbox loads after login; it is then replaced by the last used image, as specified in the init file. In my case this spans several seconds but on a much faster system or different config, it may go so quickly as to not be worth setting.

Maybe post the startup file as you're wanting it to work? Luck to ya :)

---

### Post by danifodor on 2008-01-18
Well, meanwhile I figured out that it runs indeed (by adding an extra line aterm & -> terminal appeard) so it should be some adesklets specific problem. I can run it from terminal and then all of my desklets appear properly but I cannot run them automatically.

My startup file has changed almost nothing:
```

fbsetbg -f ~/.fluxbox/backgrounds/wp.jpg
conky &
# adesklets &
exec /usr/bin/fluxbox

```
(I commented out adesklets because it was useless)

Any idea?

Daniel

---

### Post by danifodor on 2008-01-18
OK, it is solved.
The problem was that I use mpd controller desklet and additional python modules should have been installed. I did it but used a custom directory in /home/user/.python_mpd and added the correct value of $PYTHONPATH in .bash_profile. This file is loaded after adesklets (and any other custom programs in the startup file) so adesklets did not know the value of this environment variable and therefore did not load any of the desklets. I compiled again the python modules used by mpd controller but this time without custom path (I simply do not like to compile sources because I cannot handle them any more) and $PYTHONPATH became unnecessary. Now if I add the adesklets & line in startup file it runs properly.

That was tricky :D

Daniel

---

