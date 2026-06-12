---
title: "XGL+Compiz and Frozen Bubble."
date: 2006-08-16
forum: Gaming &amp; Leisure
---

### Post by andrek on 2006-08-16
I'm new here, so I would like to say Hello! :)
I've got a problem with Frozen Bubble. Just look at screenshot : [[IMG]http://img147.imageshack.us/img147/466/zrzutekranucw5.th.png[/IMG]](http://img147.imageshack.us/my.php?image=zrzutekranucw5.png)
 I'm running on ubuntu 6.06 with XGL+Compiz installed.

---

### Post by reacocard on 2006-08-16
yeah, that happens with a lot of games and compiz. easiest solution is to run the game like this:
```
export XLIB_SKIP_ARGB_VISUALS=1
name_of_game
```
that fixes this problem for most games, but does force you to use a terminal to launch it each time.

---

### Post by mrazster on 2006-08-16
> **reacocard said:**
> but does force you to use a terminal to launch it each time.

Well...nahh...not really m8.

Just do a bin/bash script...and it's all fine.

1. creat a file called *_frozen-bubble_* with a texteditor of you chooice:
```
gedit ~/frozen-bubble
```

2. paste this in to that file:
```
#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1 
frozen-bubble
```
save the file and exit.

3. then make it executable:
```
chmod -x ~/frozen-bubble
```

This way it even got the frozen-bubble icon automaticlly.
You can move the file where ever you want...or make link to it from the menu if you want.

---

### Post by spvo on 2006-09-10
I ended up having to use that same command for several differnt games and mathematica, so I found it was easier to just write a script that just appends "export XLIB_SKIP_ARGB_VISUALS=1" right before it runs the program.  Anyway, the script I wrote is 

```

#!/bin/bash        
if [ -z "$1" ]; then 
  echo usage: $0 program_location
  exit
fi
FLOC=$1
export XLIB_SKIP_ARGB_VISUALS=1
$FLOC
```

Just name and save that file anywhere, make it executable, and then you can just run it with the name of the program you want to run next as a parameter.  This way you can just make a simple fix to the program in Alacarte Menu Editor, without having to mess around with icons.  Example:

```

./transparencyfix frozen-bubble
./transparencyfix /usr/local/bin/mathematica
```

---

### Post by vyruss on 2006-09-14
Many thanks for the info & script guys!

---

### Post by ShirishAg75 on 2006-09-14
somebody give a screenshot with the fixed thing too guys. Thnx in advance.

---

