---
title: "How to make a Hot Key for Displaying Time?"
date: 2013-03-13
forum: Desktop Environments
---

### Post by gibxam on 2013-03-13
Hello all,

I'd like to make a hot key (say <FN>T or something of the sort) that toggles the time display in the upper right hand corner. I've never written a script for my daily tasks before and am not even sure if this is the direction I should be looking. Any ideas? Your help is appreciated.

max

---

### Post by Frogs Hair on 2013-03-13
Do you want something independent of the existing applet ?  There is software in the sw center for daily scheduling of tasks also.

---

### Post by gibxam on 2013-03-13
I'd like to be able to hot key the checking and unchecking of the box that says "show a clock in the menu bar"

---

### Post by stinkeye on 2013-03-14
Save as **toggle-clock.sh**
```
#!/bin/bash 
#
# Script to toggle visibilty of clock in Unity Panel
# Tested in Ubuntu 13.04
#

hide="gsettings set com.canonical.indicator.datetime show-clock false"
show="gsettings set com.canonical.indicator.datetime show-clock true"
test=$( gsettings get com.canonical.indicator.datetime show-clock )

if [ $test = "true" ]; then
	eval $hide
else
	eval $show
fi
```

Right click on toggle-clock.sh.... **Properties > permissions** and tick execute.
While your there, also right click on toggle-clock.sh and choose copy.

Open keyboard in the dash.
Add a custom shortcut using the path to toggle-clock.sh as the command.
The path should be in your clipboard ready for pasting in the command box.

---

### Post by gibxam on 2013-03-14
Thank you for your time stinkeye. Perfect directions and result.

---

