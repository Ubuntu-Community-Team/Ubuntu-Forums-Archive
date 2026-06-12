---
title: "Compiz-fusion is not working"
date: 2007-09-01
forum: Desktop Effects &amp; Customization
---

### Post by superbenny on 2007-09-01
I installed compiz-fusion using the guide on

[http://ubuntuforums.org/showthread.php?p=3255930](http://ubuntuforums.org/showthread.php?p=3255930)

one thing was mistyped (said to apt-get upgrade, instead of update after editing sources.list) and i changed that, and i have everything all set up

all the effects work fine with the exception of desktop cube. under system settings>desktop i have 3 desktops setup. under compizconfig i have vertical and horizontal set to 1 and # of desktops set to 3. it wont turn when i switch. however it does fade.

superkaramba isnt working either. it says i have Zebra system monitor on my desktop (worked fine before compiz), but now its not there.

one other thing: my title bars are gone on all my apps.. absolutely gone, no trace of them.

please help, this is really aggravating me

---

### Post by hidden_leaf_sasuke on 2007-09-01
pleasy specify your graphic card..:) what type of graphic card do you use?

---

### Post by superbenny on 2007-09-01
Tungsten Graphics Inc.

Mesa DRI Intel 945GM

if thats incorrect, its whatever the standard graphics card for IBM ThinkPad R60 is.

---

### Post by Inxsible on 2007-09-01
open a terminal and type in this command```
lspci | grep "VGA compatible"
```Post your output here.

---

### Post by superbenny on 2007-09-01
> **Inxsible said:**
> open a terminal and type in this command```
lspci | grep "VGA compatible"
```Post your output here.



00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by superbenny on 2007-09-01
ok i think i may have gotten it. i installed compiz-gnome by accident instead of -kde

im gonna restart and give it a try

---

### Post by superbenny on 2007-09-01
>  ok i think i may have gotten it. i installed compiz-gnome by accident instead of -kde

im gonna restart and give it a try


ok i got the title bars back. however the cube still refuses to work.

and whenever i quit something, the titlebars disappear again

when i restart compiz

(kwin --replace
 then
compiz --replace)

it goes back to normal


ughh this is aggravating

---

### Post by psyopper on 2007-09-01
To get a cube in Compiz (and Beryl) you need...

Horizontal Virtual Size: 4
Vertical Virtual Size: 1
Number of Desktops: 1

---

### Post by superbenny on 2007-09-01
> **psyopper said:**
> To get a cube in Compiz (and Beryl) you need...

Horizontal Virtual Size: 4
Vertical Virtual Size: 1
Number of Desktops: 1
ok i did that. i got the cube to work. thank you. still one more issue. when i close the konsole session that i started compiz in, the taskbars disapear.

it prints

"A handler is already registered for the path starting with path[0] = "org""

a bunch of times and is unusable.

---

### Post by Inxsible on 2007-09-02
> **superbenny said:**
> ok i did that. i got the cube to work. thank you. still one more issue. when i close the konsole session that i started compiz in, the taskbars disapear.

it prints

"A handler is already registered for the path starting with path[0] = "org""

a bunch of times and is unusable.
do not use the terminal/konsole to start compiz. press alt + F2 and type in 
```
compiz --replace
``` or if you have installed the compiz fusion icon then type in ```
fusion-icon
```

---

### Post by superbenny on 2007-09-02
got it...i ended up using the command thing that i added to bar at the bottom.

thanks!

ill probably end up screwing something else up though...:(

---

