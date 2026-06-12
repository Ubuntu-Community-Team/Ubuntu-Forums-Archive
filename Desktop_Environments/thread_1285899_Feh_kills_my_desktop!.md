---
title: "Feh kills my desktop!"
date: 2009-10-08
forum: Desktop Environments
---

### Post by LoREZ on 2009-10-08
Hi, everyone, and thanks in advance for any help. I looked around and couldn't find this problem anywhere, although I know the root cause (I think).

I wrote this small script so I could change my wallpaper randomly by double-clicking an launcher on my gnome-panel:

```
#!/bin/bash

#rWall is licensed under GPL v2.0 (queue inflated sense of self-importance).
#A script to select random images from the specified directories and tile them to the background with feh.
#Feh stores background settings in $HOME/.fehbg.  Use the following options to change feh's behavior.
#feh --bg-center
#feh --bg-scale

#this sets a variable for later use.
wallpaper=$(find $HOME/Pictures/custom_backgrounds/1680/ -name "*1680*.j*g" | sort -R | head --lines=1)

#this sets the output in quotes, in case the target image has gaps or other problem characters in its name.
feh --bg-tile "$wallpaper"

exit
```

Go easy: I'm just learning bash scripting.

Anyhow, when I employ this little gem, it kills my icons and I can't use the right mouse button on the desktop, nor can I launch conky.  Of course, they are all still there, but the wallpaper is covering them!  I know conky writes to the root window when "own_window no" is set, so I changed that, but now I get trails when I move windows around.

Is this normal behavior for feh, and is there a switch to have it write to the same space nautilus is using for the wallpaper?

In a related problem, when I launch uTorrent with wine or (conky without using feh), my desktop icons disappear, but they come back briefly while I mouseover them.  Any solutions for that one would be appreciated as well.

---

### Post by LoREZ on 2009-10-08
Bump...

Any thoughts?

---

### Post by LoREZ on 2009-10-08
Wow.  That took a while for something this apparently simple, but I found out how to make it happen.  The only thing missing is to keep it from ever repeating the last image, although I found a code snippet that seems like it might work.

Here is the final script, unless I feel like adding the snippet mentioned above.  It will work for either GNOME or openbox -- all you have to do is choose either gconftool or feh, depending on your desktop environment/windows manager:

```
#!/bin/bash

#rWall is licensed under GPL v2.0 (queue inflated sense of self-importance).
#A script to select random images from the specified directories and tile them to the background.
#requires either feh or gconftool.
#Feh stores background settings in $HOME/.fehbg.
#The key for gconftool is /desktop/gnome/background/picture_filename.


#set wallpaper directory.
bgfolder=$HOME/Pictures/custom_backgrounds/1680/

#set wallpaper random.
wallpaper=$(find $bgfolder -name "*.j?g" | sort -R | head --lines=1)

#use feh
#feh --bg-center "$wallpaper"
#feh --bg-scale "$wallpaper"
#feh --bg-tile "$wallpaper"

#or use gconftool, which will prevent hiding of icons and desktop right-click menu in GNOME.
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$wallpaper"

exit
```

I'm using this with about 350 wallpapers at present. I heard the bash shell has a 32k memory limit, but I don't know if it applies to a find command, which is what this script is calling.

My next challenge is to put a different wallpaper on each of my two monitors, although I really don't know if GNOME handles that, since the appearance tool doesn't allow it, and I don't know of a key that would do this in gconftool.

I only use four lines of actual code. This seems a lot shorter than the other scripts floating around, although I don't make use of arrays.  From what I can figure, most of the value in that is that you don't have to worry about per-file path notations in the output, but I don't know...

I may include KDE, so the script will grow some more.

Okay, I'm still having touble wth conky disappearing my desktop icons.

---

