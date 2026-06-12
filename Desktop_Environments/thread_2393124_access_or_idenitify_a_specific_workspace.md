---
title: "access or idenitify a specific workspace"
date: 2018-05-30
forum: Desktop Environments
---

### Post by Skaperen on 2018-05-30
now that i have most other things worked out with Unity, i'd like to resolve workspace issues.

1.  how can a program or script identify which workspace it is running in, or has a window in, or is the one being displayed?

2.  how can i start a program that opens a window to get it to open the window in a specific workspace?

3.  how can i have a program or script cause a change to which workspace is bring displayed.

i have learned that the way workspaces are done under Unity is that something (maybe compiz is doing this) keeps track of which windows belong in which workspace, and detects a change in workspace (maybe this is the thing that handles the user interface to workspaces) hides and exposes windows accordingly.  by comparison, an older method used a very large virtual buffer (using a lot of virtual memory), placed windows in many places, and changed what part of the big virtual buffer was being displayed. an example would be a 2x2 workspace arrangement of a 1920x1080 display.  the virtual buffer would be 3840x2160.

---

### Post by again? on 2018-05-31
Compiz is seen as 1 virtual desktop, the virtual size dependent on number of workspaces.
So to see what workspace you are on you can use screen coordinates.
This one identfies the workspace number for 4x1 config (can also work with 2x2).
**_desk-number-compiz.sh_**
```
#!/bin/bash

screen_dimensions=$(xdpyinfo | awk '$1=="dimensions:"{print $2}') # x*y
screen_width=${screen_dimensions%x*} # x
screen_height=${screen_dimensions#*x} # y

desktop_dimensions=( $(wmctrl -d | awk '{print $4}') ) # compiz virtual desktop dimensions
desktop_width=${desktop_dimensions%x*} # compiz virtual desktop x
desktop_height=${desktop_dimensions#*x} # compiz virtual desktop y


COORDINATE=$(wmctrl -d | awk '{print $6}')
#touch ~/.viewport-number.txt

## uncomment for 2x2 viewports
#if [ "$COORDINATE" == "0,0" ]; then
#		echo 1

#	elif [ "$COORDINATE" == "$screen_width,0" ]; then
#		echo 2 

#	elif [ "$COORDINATE" == "0,$screen_height" ]; then
#		echo 3

#	elif [ "$COORDINATE" == "$screen_width,$screen_height" ]; then
#		echo 4

## uncomment for 4x1 viewports
if [ "$COORDINATE" == "0,0" ]; then
		echo 1 

	elif [ "$COORDINATE" == "$screen_width,0" ]; then
		echo 2

	elif [ "$COORDINATE" == "$(( screen_width *  2 )),0" ]; then
		echo 3

	elif [ "$COORDINATE" == "$(( screen_width *  3 )),0" ]; then
		echo 4 


fi
```

Similarly, use wmctrl with the -o flag to switch desktops using coordinates.
From man wmctrl
> **-o x,y**
Change the viewport for the current desktop. The values x and y are numeric offsets that specify the position of the top left corner of the viewport. 
A window manager may ignore this request.
eg 
my screen size is 1680x1050
When compiz is configured 4x1 the total virtual desktop width is 6720 (4x1680)
To switch to the top left coordinate of each workspace I would use. 
[LIST=1]
[*]wmctrl -o 0,0
[*]wmctrl -o 1680,0
[*]wmctrl -o 3360,0
[*]wmctrl -o 5040,0
[/LIST]

---

### Post by Skaperen on 2018-05-31
it works!  i'll probably write some scripting around that in python.  to open a window in a specific workspace, i just need to switch to it, then open the window?

---

### Post by again? on 2018-06-01
If you understand Dbus you can also control compiz with commands when the compiz Dbus plugin is activated.
eg
```
dbus-send --print-reply --dest=org.freedesktop.compiz /org/freedesktop/compiz/wall/screen0/right_key org.freedesktop.compiz.activate
```

Have a look at d-feet.
> d-feet is a D-Bus debugger that allows you to:
 * View names on the session and system bus
 * View exported objects, interfaces, methods and signals
 * View the full command line of services on the bus
 * Execute methods with parameters on the bus and see their return values 

Not something I understand though.
See ----> [**Control Your Linux Desktop with D-Bus**]("https://www.linuxjournal.com/article/10455")

---

