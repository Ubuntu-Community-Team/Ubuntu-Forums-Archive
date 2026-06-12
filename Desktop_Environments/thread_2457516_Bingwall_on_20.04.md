---
title: "Bingwall on 20.04"
date: 2021-02-03
forum: Desktop Environments
---

### Post by hornetster on 2021-02-03
Anyone managed to get Bingwall working on vanilla 20.04 (up-to-date)?
Have it installed, but when I run, get:
```
(bing-wall:6843): Gtk-WARNING **: 10:44:24.466: Theme parsing error: gtk.css:1566:23: 'font-feature-settings' is not a valid property name

(bing-wall:6843): Gtk-WARNING **: 10:44:24.471: Theme parsing error: gtk.css:3616:25: 'font-feature-settings' is not a valid property name

(bing-wall:6843): Gtk-WARNING **: 10:44:24.472: Theme parsing error: gtk.css:4078:23: 'font-feature-settings' is not a valid property name
Gtk-Message: 10:44:24.517: Failed to load module "canberra-gtk-module"
Gtk-Message: 10:44:24.518: Failed to load module "canberra-gtk-module"
Qt: Session management error: Could not open network socket
QApplication: invalid style override passed, ignoring it.
propsReply "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.131\" (uid=1000 pid=6843 comm=\"bing-wall \" label=\"snap.bing-wall.bing-wall (enforce)\") interface=\"org.freedesktop.DBus.Properties\" member=\"GetAll\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.NetworkManager\" (uid=0 pid=1006 comm=\"/usr/sbin/NetworkManager --no-daemon \" label=\"unconfined\")"
nmReply "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.131\" (uid=1000 pid=6843 comm=\"bing-wall \" label=\"snap.bing-wall.bing-wall (enforce)\") interface=\"org.freedesktop.NetworkManager\" member=\"GetDevices\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.NetworkManager\" (uid=0 pid=1006 comm=\"/usr/sbin/NetworkManager --no-daemon \" label=\"unconfined\")"
"Object path cannot be empty"
```

Gui then comes up OK, and 'seems' to work, but never get a wallpaper.
Have tried installing everything "canberra-gtk...etc", no firewall, equivalents work on other systems on the network, just seems to be Ubuntu....
Installed using: ```
sudo snap install bing-wall
```

Thanks.

---

### Post by TheFu on 2021-02-04
Ignoring Gtk-warnings is what I do.  In the business, some programs have what are known as "standard warnings" that developers sometimes forget to silence.  The Gtk guys never seem to remember to silence their stuff. In a commercial app, that would be embarrassing. They don't seem to care.  

The AppArmor thing is above my pay grade.  Looks like you are trying to use a Qt program on a Gtk system.

I've never heard of bing-wall, BTW.  Bing makes me run away, but I'm easily scared.  For rotating backgrounds, I use **feh** in typical Unix fashion.

---

### Post by Frogs Hair on 2021-02-05
Testing this application on the UB development release and the application opens. The only way I could set a wallpaper was to enter settings, select go to downloads, select one of two images found there, right click and set as wallpaper. It fails to run on startup or select a daily image.

Edit: There maybe better options in the software center such as variety , wallpaper down-loader hydra paper, and Fondo .

---

### Post by Holger_Gehrke on 2021-02-05
The warnings about 'font-feature-settings' in gtk.css mean that there's something wrong with the GTK-theme you're using; it's trying to set a property that isn't known to the GTK CSS engine. The rules for parsing CSS are that unknown properties should be discarded, so this isn't important. 
The warnings about canberra can be disregarded, too. libcanberra is used to assign sounds to user-interface interactions. Yes, that is as silly as it sounds. No, that should not be the problem.
The AppArmor messages are probably the reason why it doesn't work. I'd look at the permissions given to the snap in the Software app (gnome-software,snap-store, ... whatever it's called on your system).

I had a good look at the code of the app at [https://github.com/keshavbhatt/BingWall/](https://github.com/keshavbhatt/BingWall/) and found that the functionality of it could be achieved with a few lines of shell scripting; download the list of wallpapers in JSON format using 'wget' and pipe that list through 'jq' (a tool to process JavaScript Object Notation in the shell; package 'jq' in the Ubuntu repositories) to filter out just the URLs, select one of the images at random and set it as a wallpaper. More than 90% of the code of BingWall is dealing with all the GUI stuff. 
```

#!/usr/bin/env bash
# get the JSON file, pull out just the URLs and put them in an array
a=($(wget -qO- https://peapix.com/bing/feed|jq '.[].fullUrl'))
# random number between 0 and number of elements in the array -1
b=$((RANDOM % ${#a
[*]}))
# remove the quotes and the '?attachment' parameter from the selected URL
c=${a[$b]%%\?attachment\"}
c=${c##\"}
# get the image and write it to /tmp/bg.jpg
wget $c -O /tmp/bg.jpg
# set the image as background
gsettings set org.gnome.desktop.background picture-uri file:///tmp/bg.jpg

```

Put that in a file in ~/.local/bin/, make that file executable, create a .desktop-file for this script and put it in ~/.config/autostart.

Holger

---

### Post by hornetster on 2021-02-06
> **Holger_Gehrke said:**
> 
Put that in a file in ~/.local/bin/, make that file executable, create a .desktop-file for this script and put it in ~/.config/autostart.

Holger
Thanks.
As it turns out (further testing needed...) it would appear that if you turn of the setting for "show image detail on wallpaper" it seems to work...

---

