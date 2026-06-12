---
title: "lid.sh acpi event will not run xvattr cmd"
date: 2009-04-30
forum: General Help
---

### Post by otkaz on 2009-04-30
I use my laptop with a docking station. I didn't like the way the default lid.sh script woke my laptop screen up on mouse movement so made a new one, but I cant get one part of it to work. I want to run a xvattr command to switch my overlay to play video on my monitor. This is the script I'm using
```
#!/bin/sh
state=`cat /proc/acpi/button/lid/LID/state | awk '{print $2}'`
if [ "$state" = "closed" ]
then
xvattr -a XV_CRTC -v 1
radeontool light off
else
radeontool light on
xvattr -a XV_CRTC -v 0
fi

```
the radeontool part works fine, but it will not run the xvattr commands when I trigger the lid button. If I launch the script manually with sh /etc/acpi/lid.sh it works though??? Is there some kind of limit on what commands can be run with acpi events? whats really strange is I had it working at one point, but I can't figure out what in the world I did to break it or how it was working in the first place.

---

