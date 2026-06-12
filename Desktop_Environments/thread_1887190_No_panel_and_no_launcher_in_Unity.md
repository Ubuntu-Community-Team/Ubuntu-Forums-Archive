---
title: "No panel and no launcher in Unity?"
date: 2011-11-26
forum: Desktop Environments
---

### Post by deskman on 2011-11-26
when i log in i can see only desktop wallpaper and i'm able to right click the desktop and bring the right click menu. i tried to click on "change background", the window that opened had no close or minimize buttons. something to do with compiz? when i log in to the gnome shell there is no such problem. the problem appeared just recently. any one any ideas?

os: oneiric 64
nvidia proprietary driver enabled

---

### Post by BC59 on 2011-11-26
Open a terminal CTRL+ALT+T and write

```
unity --reset
```

and if is not working write

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

---

### Post by stinkeye on 2011-11-26
> **BC59 said:**
> Open a terminal CTRL+ALT+T and write

```
unity --reset
```

and if is not working write

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```
Just a note.
When you run
```
gconftool-2 --recursive-unset /apps/compiz-1
```
Compiz is set back to default and in this state the unity plugin is not enabled.

Then running
```
unity --reset
```
just reloads compiz without enabling the unity plugin.

So you will still need to enable the unity plugin in ccsm.

**or**
this command will set back to defaults,enable the unity plugin and then reload compiz.
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

Sometimes after running you may still have no window borders and you need to run 
this command again
```
compiz --replace & disown
```

---

### Post by BC59 on 2011-11-26
> **stinkeye said:**
> Just a note.
When you run
```
gconftool-2 --recursive-unset /apps/compiz-1
```
Compiz is set back to default and in this state the unity plugin is not enabled.

Then running
```
unity --reset
```
just reloads compiz without enabling the unity plugin.

So you will still need to enable the unity plugin in ccsm.

**or**
this command will set back to defaults,enable the unity plugin and then reload compiz.
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

Sometimes after running you may still have no window borders and you need to run 
this command again
```
compiz --replace & disown
```

Very good point.

---

