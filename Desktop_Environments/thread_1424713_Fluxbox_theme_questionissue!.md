---
title: "Fluxbox theme question/issue!"
date: 2010-03-08
forum: Desktop Environments
---

### Post by xdemo on 2010-03-08
Hey, been using fluxbox on karmic for past few weeks, and im really loving the experience, so dammmm fast.

However, i recently found out 2 weeks back how to set gtk themes via gnome-appearance-properties by using "gnome-settings-daemon" in my startup script.

My question is, how can i do the same for qt based appliactions?
I'm assuming the last.fm player is qt because my gtk theme never applies to the last.fm player it always stays white, whereas in GNOME desktop, it would change color/theme accordingly.

Screenshot to give an idea:
[IMG]http://i47.tinypic.com/2mfgkyp.png[/IMG]
As you can see last.fm is always white, whereas gtk apps such as PCManFM are using my gtk theme, is there a way to make qt apps use the same color scheme as the gtk one or whatever. Im not sure how GNOME does it, but thats what i'm posting to ask.

Heres my startup script if it helps:
```
#!/bin/sh
#
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# Change your keymap:
xmodmap "/home/demo/.Xmodmap"

# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
fbsetbg -f ~/Pictures/Wallpaper/edit1.jpg
aterm -name aterm -sl 3000 -tr +sb -si -sk -fn -misc-fixed-medium-r-normal -g 100x30-1200+10 -bl -fg cyan &
nm-applet --sm-disable &
update-notifier &
gnome-settings-daemon &
gnome-volume-manager &
tspc &
xscreensaver -nosplash &
checkgmail &
~/.conkystartup.sh &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

export LC_ALL=C
exec fluxbox

# or if you want to keep a log:
# exec fluxbox -log "/home/demo/.fluxbox/log"
```Thanks.

---

### Post by xdemo on 2010-03-09
Bump, does anyone know? I've been googling for the past few days and cannot find a how-to.

---

