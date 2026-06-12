---
title: "How to lock Gnome panel?"
date: 2009-05-03
forum: Desktop Environments
---

### Post by rogerdean on 2009-05-03
Hello all

I've been using Ubuntu Tweak for some time, but realised that I now know how to do almost everything I need without it. But I still need to be able to lock (and unlock!) the Gnome panel (so launchers etc don't get deleted accidently). Could anyone post the commands for that please?

Many thanks!
Roger

---

### Post by hictio on 2009-05-03
> **rogerdean said:**
> Hello all

I've been using Ubuntu Tweak for some time, but realised that I now know how to do almost everything I need without it. But I still need to be able to lock (and unlock!) the Gnome panel (so launchers etc don't get deleted accidently). Could anyone post the commands for that please?

Many thanks!
Roger

I don't know about Ubuntu Tweak, never used it myself, but, you can lock the Gnome Panel, once you are satisfied with its contents, settings, etc, by using 'gconf-editor' (typa Alt + F2 and type that to execute it), and then, navigate to:

Apps > Panel > Global

And then check the option 'locked_down'. You'll see that the context menu that pops up when you do a right click on the menu changes right away.
Hope this is what you mean.

---

### Post by rogerdean on 2009-05-04
Hi, yes, exactly what I meant, thanks! But I'd like to make quick launchers for the lock and unlock commands. Do you know what the CLI commands would be?

Cheers
Roger

---

### Post by hictio on 2009-05-04
> **rogerdean said:**
> Hi, yes, exactly what I meant, thanks! But I'd like to make quick launchers for the lock and unlock commands. Do you know what the CLI commands would be?

Cheers
Roger

Piece of cake ;)
Type this, or place it on a script, and make it executable, etc...

```

gconftool-2 --type bool --set /apps/panel/global/locked_down true
gconftool-2 --type bool --set /apps/panel/global/locked_down false

```

The first one locks the Panel down, and the second one "frees" it :D

---

### Post by Wiebelhaus on 2009-05-04
Ubuntu tweak is good and harmless and anything it does can be reversed  , Good tool for newcomers , I use it for the scripts.

---

### Post by rogerdean on 2009-05-04
Magic, many thanks indeed hictio

Yes, Ubuntu Tweak has served me well for a couple of years. I'm just now getting to the point where I don't need it any more. Highly recommended though...

Allbest
Roger

---

### Post by kaibob on 2009-05-04
I found this thread interesting, as I seem to have a knack for messing up my computer's carefully-arranged panel icons. I wrote the following script--which toggles panel-lock off and on--and assigned it to a panel launcher. It seems to work OK, but I wondered if writing to the gconftool database could corrupt it in some way. I know nothing as to how the data is kept, but I recall that corrupted Windows registries could be a major problem.

Anyways, thanks hictio for information.

```
#!/bin/bash

STATE=$(gconftool-2 --get /apps/panel/global/locked_down)

if [ $STATE = true ] ; then
   gconftool-2 --type bool --set /apps/panel/global/locked_down false
else
   gconftool-2 --type bool --set /apps/panel/global/locked_down true
fi
```

---

### Post by hictio on 2009-05-04
> **kaibob said:**
> I found this thread interesting, as I seem to have a knack for messing up my computer's carefully-arranged panel icons. I wrote the following script--which toggles panel-lock off and on--and assigned it to a panel launcher. It seems to work OK, but I wondered if writing to the gconftool database could corrupt it in some way. I know nothing as to how the data is kept, but I recall that corrupted Windows registries could be a major problem.

Anyways, thanks hictio for information.

```
#!/bin/bash

STATE=$(gconftool-2 --get /apps/panel/global/locked_down)

if [ $STATE = true ] ; then
   gconftool-2 --type bool --set /apps/panel/global/locked_down false
else
   gconftool-2 --type bool --set /apps/panel/global/locked_down true
fi
```

Amazing, man, thanks.
I wasn't aware that you could query the state.

---

