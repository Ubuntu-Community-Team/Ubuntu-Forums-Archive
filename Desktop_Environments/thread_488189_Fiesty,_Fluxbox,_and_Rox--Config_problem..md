---
title: "Fiesty, Fluxbox, and Rox--Config problem."
date: 2007-06-29
forum: Desktop Environments
---

### Post by Adam_GUI on 2007-06-29
How-diddly-ooh, Neighborinos!

I tried out fluxbuntu the other day on my laptop and I've been trying to re-create that rox-desktop on my main Ubuntu box without a fresh install.  (That and I wanted something more up to date.)

Upon starting fluxbox, I have what looks to be Rox-filer giving me an icon for my home solder.  But it's just a white square on the background.

When I right-click the square, I get nothing.
When I right-click the desktop, I get no flux-menu.

I believe the problem to be in my startup file.  But I'm too much a noob to know exactly what I did wrong.

Here's my startup file:
```
#!/bin/sh

# fluxbox startup-script: 
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
fbsetbg -r ~/Pictures/
# This sets a black background

# /usr/bin/fbsetroot -solid black

# This shows the fluxbox-splash-screen
fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp "/home/kagerou/.fonts"
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap "/home/kagerou/.Xmodmap"



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#

unclutter -idle 2 &
wmnd &
wmsmixer -w &
idesk &
fbpager
# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/kagerou/.fluxbox/log"

# Start xscreensaver & numlocks
/usr/bin/xscreensaver &
/usr/bin/numlocks on &

# Play sound as login
# "play" is dependent on sox
# you will need to set "hw:1.0" for yourself (see how-to-play a login sound)
sleep 5 && play -d hw:1,0 /usr/share/sounds/login.wav > /dev/null 2>&1 &

#Start rox
exec /usr/bin/rox --pinboard=Default &

exec /usr/bin/startx /usr/bin/Fluxbox
```

While I know I don't need fluxbox.  I just like to tinker around with stuff.  I've had flux before when I used Mepis with Adesklets and YAB.  But I'd like to get Rox's pinboard working for me instead this go-round.

Can anyone with a working rox-filer setup file post their's up or point out what I've got wrong in my config?

I'd certainly appreciate it.

Thanks!

--Adam

EDIT:
I had iDesk and pinboard set at the same time.
Problem one solved.  I have flux-menus back.

Now there's no rox....

EDIT:
took out the "exec"s and now rox works.  But I can't get to my flux-menu.  What gives?  It's like rox takes over the screen.

EDIT #3!
Applied the "contribute mouse clicks to window manager" and "blackbox menu hacks" and everything is hunky-dory now!  w00t!

---

### Post by kerry_s on 2007-07-01
Man, your startup's a mess. add the app's you want to start under the examples.

```
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
# bsetbg -f ~/pictures/wallpaper.png
#
# This sets a black background

# /usr/bin/fbsetroot -solid black

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
# xset +fp /home/user/.font
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

unclutter -idle 2 &
wmnd &
wmsmixer -w &
idesk &
fbpager &
xscreensaver &
numlocks on &
sleep 5 && play -d hw:1,0 /usr/share/sounds/login.wav > /dev/null 2>&1 &
rox --pinboard=Default &


# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log ~/.fluxbox/log

```


I think i got all your settings? start your background from init, not the startup.

---

