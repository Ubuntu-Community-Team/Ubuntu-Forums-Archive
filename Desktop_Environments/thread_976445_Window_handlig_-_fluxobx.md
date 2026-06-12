---
title: "Window handlig - fluxobx"
date: 2008-11-09
forum: Desktop Environments
---

### Post by kortelainen on 2008-11-09
I'm having a little problem.
I'm running fluxbox and im not a great fan of the toolbar, so my final goal would be not to have it at all. To make this possible I need some things to work without it.

My main problem is the open windows I use. When I minimize them, obviously, they go to the toolbar.What is need is somekind of terminal command/script to make them rise again. With this command I'd want to write wich window I'd like to have back up. Exampel; Typing "rise mozilla" would rise the mozilla window from being minimized.

Is there anyway to do this?

Another thing would be the text colors of the toolbar, somehow they are transparent so when I try to make my toolbar transparent, they disappear with it. How can I change these colors?

Sorry if I posted in the wrong section.
Thx for reading 'n helping

---

### Post by RedSquirrel on 2008-11-09
> **kortelainen said:**
> Another thing would be the text colors of the toolbar, somehow they are transparent so when I try to make my toolbar transparent, they disappear with it. How can I change these colors?

That is controlled by the style's theme file. If you want to modify one of the default styles, copy it from /usr/share/fluxbox/styles to ~/.fluxbox/styles.

You might want to look at the man page for fluxstyle.

```
man fluxstyle
```

---

### Post by kerry_s on 2008-11-09
move it to your right click:
```
[workspaces] (Workspace List)
```

---

### Post by RedSquirrel on 2008-11-09
removed

---

### Post by spupy on 2008-11-09
```

winname=`wmctrl -l | grep -o "$1" | tail -n 1 `

winid=`wmctrl -l | grep -m 1 "$1" | awk '{print $1}'`
if [[ $3 = last ]]
then
	winid=`wmctrl -l | grep "$1" | tail -n 1 | awk '{print $1}'`
fi

if [[ $winname = "$1" ]]
	then
		wmctrl -i -a $winid
		wmctrl -i -r $winid -b remove,shaded
	else
		$2 &
fi
```

This script requires the little program called **wmctrl**.
Type
```
scriptname Firefox
```
to bring up the first window with Firefox in the name. You can also call it like that:
```
scriptname Firefox firefox
```
Now if it doesn't find a window with "Firefox" it will execute the command given as the second argument - firefox. Effectively that means that if firefox is not open, the script starts it, but if it is running, it shows you the window.

---

