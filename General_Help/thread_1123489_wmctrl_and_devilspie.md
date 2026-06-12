---
title: "wmctrl and devilspie"
date: 2009-04-12
forum: General Help
---

### Post by keisangi on 2009-04-12
hi there,
i'm trying to make a script that does his:
- "minimize all  windows except the active one"
i tryed with wmctrl and devilspie and i have little problem with both.

first with wmctrl:
i've found that script that find out the name of the active window:
```

wmctrl_activewindow() {
        echo $(wmctrl -l | grep -E '^0x0*'$(xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)"  | awk -F ' window id # 0x' '{print $2}') | awk '{for (i=4;i<=NF;i++) {printf "%s%s",sep,$i;sep=" "}}')
}

ACTIVEWINDOW=$(wmctrl_activewindow)
echo $ACTIVEWINDOW

```
so it output the currently active window name,
so far so goodbut then i wasn't able to find out how to minimize a window with wmctrl. what i wanted to do was findout the name of the active window, save it's name in a variableand then minimize all windows whose name aren't the same..
for example..
but i was unable to minimize a window with it so i stopped with wmctrl..

then devilspie:
with devilspie i was able to minimize all sort of windows, but then i had problems  to create a rule to find out which window is the active one..

as i was tryig stuffs i did that:
```

(begin 
	(print (application_name) "  " (window_property "_NET_WM_STATE"))
	(print "\n")
)

```

but then in the output i saw some windows have the property "_NET_WM_STATE" set and
some other don't have anything.
here's an example of the output i get:

```

Quassel IRC - #ubuntu
Slayer - Point  ::  Amarok 2  _NET_WM_STATE_MAXIMIZED_VERT, _NET_WM_STATE_MAXIMIZED_HORZ, _NET_WM_STATE_HIDDEN
all.ds - Kate
Firefox-3.5
Oblivion : bash
Avatar - Dolphin  _NET_WM_STATE_HIDDEN
Plasma  _NET_WM_STATE_BELOW
Plasma

```
so i was wondering what could i use to detect the state of a window with devilspie.
since it seems we cannot use variable inside devilspie script, i cannot import a window_name from an external variable..

anyone got an idea?

tnx

---

