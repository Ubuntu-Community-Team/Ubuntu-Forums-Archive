---
title: "Fluxbox error"
date: 2006-06-17
forum: Desktop Environments
---

### Post by ESPOiG on 2006-06-17
first of all... i used this to install fluxbox [http://www.ubuntuforums.org/showthread.php?t=116759]("http://www.ubuntuforums.org/showthread.php?t=116759")

and i have it all set up correctly, i have my username in the GDM session which i didnt have... and all the paths are correct, now when i try to get it running when i logout it fails and says it cant find "startup" even though i have checked and changed everything over and over again, i dont know why it wont work, it should do it is pretty simple stuff but it fails, :(

ty for any help, ESPOiG

---

### Post by Ramses de Norre on 2006-06-17
What's in your ~/.fluxbox/startup?
This should be in there to start fluxbox: ```
exec /usr/bin/fluxbox &

```
Add ```
export LC_ALL=C
``` to the line just before the exec if fluxbox loads too slow.

For information, this is my whole startup file: ```
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

