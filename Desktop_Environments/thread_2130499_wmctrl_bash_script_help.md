---
title: "wmctrl bash script help"
date: 2013-03-29
forum: Desktop Environments
---

### Post by CubicleInmate on 2013-03-29
Having some trouble with wmctrl / bash and I'm really not sure why.  I am confident that once someone replies and points out the stupid thing I'm missing I will:

A) be thankful
and
B) feel silly.

This works, to hide/unhide my terminal (which I set a static window name for)
I include it only because it was the basis for my attempt to keybind the same sort of functionality for Thunderbird.
```

#!/bin/sh

# Unshade and bring to front
if [ -f ~/.appstatus/term.shaded ]; then
    wmctrl -r 'Term' -b remove,below
    wmctrl -r 'Term' -b remove,shaded
    rm ~/.appstatus/term.shaded
# Shade and send to back
else
    wmctrl -r 'Term' -b add,shaded
    wmctrl -r 'Term' -b add,below
    touch ~/.appstatus/term.shaded
fi
```

This somewhat works:
It will launch Thunderbird if the application is not running, and it will bring it to the forefront maximized, but it does not re-shade or minimize it.
```
#!/bin/sh

# Check for Thunderbird running
if [ -f ~/.thunderbird/Profiles/default/lock ]; then
	# Unshade and bring to front
	if [ -f ~/.appstatus/thunderbird.shaded ]; then
		wmctrl -r Thunderbird -b remove,below
		wmctrl -r Thudnerbird -b remove,shaded
		rm ~/.appstatus/thunderbird.shaded
	# Shade and send to back
	else
		wmctrl -r Thunderbird -b add,shaded
		wmctrl -r Thunderbird -b add,below
		touch ~/.appstatus/thunderbird.shaded
	fi
else
	rm ~/.appstatus/thunderbird.shaded
	thunderbird
fi
```

Also, since I have so few posts I cannot update my profile information - but if it helps any I'm on Ubuntu 12.10 with a very minimal install, living in Openbox.

---

### Post by CubicleInmate on 2013-03-30
Solved like so:

```
#!/bin/sh

twindow=`wmctrl -l | grep -i thunderbird | awk '{print $1}'`;

# Check for Thunderbird running
if [ -h ~/.thunderbird/Profiles/default/lock ]; then
	# Unshade and bring to front
	if [ -e ~/.appstatus/thunderbird.shaded ]; then
		wmctrl -i -a $twindow
		wmctrl -i -r $twindow -b add,maximized_vert,maximized_horz
		rm ~/.appstatus/thunderbird.shaded
	# Shade and send to back
	else
		wmctrl -i -r $twindow -b add,hidden
		touch ~/.appstatus/thunderbird.shaded
	fi
else
	rm ~/.appstatus/thunderbird.shaded
	thunderbird
fi
```

---

