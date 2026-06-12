---
title: "Annotation tool for Metacity?"
date: 2011-03-10
forum: Desktop Environments
---

### Post by rylleman on 2011-03-10
My workstation has a Nvidia Quadra FX550 graphics card which affects compiz in a very bad way; movies is often just black screened, Blender runs extremely slow etc. Switching to Metacity makes the computer much more robust without any glitches.

I would gladly move to Metacity if not for a big BUT; the **annotation** tool in Compiz which I use all the time. Not having that makes me a handicapped animator.

So, is there some sceen annotate tool that works in Metacity?

---

### Post by An Sanct on 2011-03-10
As far as I know, metacity and compiz can live together. You also don't need to use all the glitter in compiz, you can use just the annotation, if you like.

PS. How about gromit? the annotation tool from GTK.

---

### Post by rylleman on 2011-04-06
Ok, they can live together but can they run together?

How can I use Metacity as Window manager but still run Compiz tools?

Gromit seems interesting. Didn't get it working though. Might have to do some more experimenting with it.

---

### Post by stinkeye on 2011-04-06
I just tried grommit and it works in Metacity if you turn off compositing.
```
gconf-editor /apps/metacity/general/compositing_manager
```


Gromit gives an error when starting
```
could not grab Hotkey. Aborting... 
```

It uses Pause as the Hotkey by default.
You can change the Hotkey by starting with
gromit --key <keyname>
eg
```
gromit --key Home
```
works for me.Now press home to start annotating.

The default keys of
> 
[COLOR="Magenta"]Pause[/COLOR] 
toggle painting
 
SHIFT-[COLOR="#ff00ff"]Pause[/COLOR] 
clear screen
 
CTRL-[COLOR="#ff00ff"]Pause[/COLOR] 
toggle visibility
 
ALT-[COLOR="#ff00ff"]Pause [/COLOR]
quit Gromit

now become
> [COLOR="#ff00ff"]Home [/COLOR]
toggle painting
 
SHIFT-[COLOR="#ff00ff"]Home[/COLOR] 
clear screen
 
CTRL-[COLOR="#ff00ff"]Home[/COLOR] 
toggle visibility
 
ALT-[COLOR="#ff00ff"]Home[/COLOR] 
quit Gromit

See **man gromit**

---

### Post by rylleman on 2011-04-06
Thank you. I got  gromit working!

Although the line I'm getting is kind of splotchy, thin line with larger lumps on it. This seems to be the way gromit interpret the pressure from my wacom tablet. Like it's not smooth enough.

If I can solve this issue this is definitely the path to go with this work station.

---

### Post by stinkeye on 2011-04-06
Hi rylleman,
Ok good. Don't know much about the app. Just had a read of the man page 
to see if I could get it to work.
It writes really fluently with a mouse.
Goodluck.
:)

---

