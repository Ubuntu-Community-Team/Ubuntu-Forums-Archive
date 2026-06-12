---
title: "CONKY: Window disappears when clicking on Desktop"
date: 2011-03-29
forum: Desktop Environments
---

### Post by aaaaalex on 2011-03-29
I can not imagine this is new and unresolved but i just cant find any answer as to why. 

After reading some old post about conky i decided to kill some time playing with it. 

Now every time i click on my desktop e.g. to fire up a launcher conky disappears. This is on Maverick. 

Attached is my current .conkyrc - mostly a copy of a version that came with conky via apt.

---

### Post by aaaaalex on 2011-03-30
After some toying around i got the solution:

```
own_window yes
own_window_class Conky
own_window_type normal 
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager  
own_window_transparent yes

```

---

### Post by SabreWolfy on 2011-04-05
See [here]("http://ubuntuforums.org/showpost.php?p=10639807&postcount=2"). Worked for me.

---

### Post by AlastairG on 2012-08-15
> **aaaaalex said:**
> After some toying around i got the solution:

```
own_window yes
own_window_class Conky
own_window_type normal 
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager  
own_window_transparent yes

```
This fixed the disappear-on-desktop-click for me in Ubuntu 12.04 using Cinnamon 1.4 except the "Hide all normal windows" keyboard shortcut of ctrl+Super+D hides Conky until it's re-launched. :mad:

The desktop-click was my main issue though - thanks! :-D

---

