---
title: "Why does my window border disappeared?"
date: 2011-11-29
forum: Desktop Environments
---

### Post by yangzhyo on 2011-11-29
When I use keyboard shortcut Alt+Space+X to maximize window, the window border always disappeared, and I can't handle it. So what's going on? How can I fix it? My Ubuntu version is 11.10. Thanks!

---

### Post by BC59 on 2011-11-29
Maybe you have to reset compiz:

```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

May still have no window borders and you need to run this command again

```
compiz --replace & disown
```

---

### Post by yangzhyo on 2011-11-29
Thanks for your help.
I removed Compiz yesterday. Maybe it causes my trouble.
Is the latest version of Compize supported by Ubuntu 10.10?

---

### Post by BC59 on 2011-11-29
> **yangzhyo said:**
> Is the latest version of Compize supported by Ubuntu 10.10?
Usually nobody looks back, everybody tries to fix the bugs on the latest versions.

---

### Post by yangzhyo on 2011-11-29
I find the truth is system set keyboard shortcut 'Alt+Space' the meaning of 'Activate the window menu', so every time I used 'Alt+Space' combination will cause the window border problem. I can't understand why? What's the correct action should be when 'Activate the window menu'?

---

### Post by BC59 on 2011-11-30
A very good documentation about keyboard shortcuts is here:

[http://askubuntu.com/questions/28086/what-are-unitys-keyboard-and-mouse-shortcuts](http://askubuntu.com/questions/28086/what-are-unitys-keyboard-and-mouse-shortcuts)

---

