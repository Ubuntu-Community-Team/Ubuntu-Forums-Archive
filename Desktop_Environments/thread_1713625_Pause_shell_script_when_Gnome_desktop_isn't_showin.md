---
title: "Pause shell script when Gnome desktop isn't showing"
date: 2011-03-24
forum: Desktop Environments
---

### Post by treacl on 2011-03-24
Does anyone know of a way, in a shell script, to pause execution whenever the Gnome desktop isn't showing, and resume it again as soon as the desktop is displayed again?

I'm using a short script that I found online (somewhere; can't find the source again now) to periodically fetch an image from a webcam feed (see code below). Out of respect for the webcam maintainer's resources, I would like to pause downloading of the image whenever the Gnome desktop isn't actually showing. This would happen under the following circumstances:

[LIST]
[*]The screen is locked
[*]The display is put to sleep per power settings
[*]The screensaver is activated
[*]Another application window is entirely obscuring the desktop
[/LIST]
Any ideas about how to test for these circumstances in a shell script?

Many thanks,
treacl

The code:

```
#!/bin/sh

URL=http://www.example.com/webcam.jpg
DIR=~/webcam/
FILE=${URL##*/}

while true; do
  wget -N $URL
  gconftool-2 -t str --set /desktop/gnome/background/picture_filename $DIR$FILE
  sleep 1m
done

```

---

