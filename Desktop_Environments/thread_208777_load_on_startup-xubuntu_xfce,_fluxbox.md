---
title: "load on startup-xubuntu xfce, fluxbox"
date: 2006-07-04
forum: Desktop Environments
---

### Post by blacknyx on 2006-07-04
Okay so I'm running xubuntu now.  I'm loving it.  I'm able to switch between fluxbox, openbox, and xfce at will (yes I know I don't need all of these, I'm obsessive).

But one question, since I don't have gnome, how do I autoload certain applications such as conky?  I was reading the conky tutorials and it wasn't mentioned how to do it if you don't have gnome.

I'd really like conky and chbg to load on startup of my GUI, whether it be fluxbox, openbox, or xfce.

Thanks for you help again guys.  I seriously need to make myself a book to remember how to do all of these little things, I just can't remember them all.

---

### Post by Ramses de Norre on 2006-07-04
For fluxbox:
```
vi .fluxbox/startup
```

And add the programs with an & after them, this is my startup file for reference: ```
ramses@icarus:~$ cat .fluxbox/startup
#!/bin/sh
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
#fbsetbg -f ~/images/wallpapers/140154main_image_feature_481_ys_4.jpg
#
# This sets a black background

/usr/bin/bsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp /home/ramses/.font
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap ~/.Xmodmap



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

#Monitoring tool
gkrellm &
kmix &
#insert Gnome
GSDPID=`pidof gnome-settings-daemon`
if [  "x$GSDPID" == "x" ]; then
gnome-settings-daemon &
fi
#makes the gnome-theme-manager work
gnome-settings-manager &
#Automount volumes
gnome-volume-manager &
#keep this export line just before "exec fluxbox &" !
export LC_ALL=C
# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.
exec /usr/bin/fluxbox &
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log ~/.fluxbox/log

#Following lines execute programs after fluxbox is started
fbpid=$!

sleep 3
{
   fbpager -w &
   tilda &
} &

wait $fbpid

```

---

