---
title: "FLUXBOX :: proper alt-tab howto"
date: 2006-11-19
forum: Desktop Environments
---

### Post by vermaden on 2006-11-19
fluxbox uses two functions to switch between windows: 
[INDENT][B]:NextWindow <int>
:NextGroup <int>[/B][/INDENT]

but if you minimize/iconify window no matter what argument/number you give to one of these functions, the alt-tab will always omit minimized/iconified windows. there are two sollutions to this. to make alt-tab "seeing" and switching between all windows including minimized/iconified you must add one of the six lines below to your **~/.fluxbox keys** configuration file:
```
# for switching only windows choos one of these
Mod1 Tab :MacroCmd {Deiconify All OriginQuiet} {NextWindow 0}
Mod1 Tab :MacroCmd {Deiconify Last OriginQuiet} {NextWindow 0}
_**Mod1 Tab :MacroCmd {Deiconify LastWorkspace} {NextWindow 0}**_
# for switching only groups choose one of these
Mod1 Tab :MacroCmd {Deiconify All OriginQuiet} {NextGroup 0}
Mod1 Tab :MacroCmd {Deiconify Last OriginQuiet} {NextGroup 0}
_**Mod1 Tab :MacroCmd {Deiconify LastWorkspace} {NextGroup 0}**_
```


**_bold underline_** options should work best and should be most predictible, but all of these make fluxbox to switch between minimized/iconified/sticky windows.

remember to reload fluxbox configuration or restart it.

there is another way to acomplish this target. you will have to grab cvs version of **bbkeys** and use it to switch windows but i think that the first approach is better and cleaner, HF ;)

---

### Post by cmulax on 2007-03-07
hey thanks for this howto!  this was one of the reasons i hadnt switched to fluxbox yet.  however, is there any way to minimize the window again if you are still holding alt and switch to another window (i.e. beryl)?  or something like an app switcher where you choose which window and after the choice it will maximize it?

Thanks in advance!

---

### Post by vermaden on 2007-03-31
> **cmulax said:**
> however, is there any way to minimize the window again if you are still holding alt and switch to another window

ALT TAB works properly now in 1.0RC3 version.

---

