---
title: "gconftool-2 does not refresh background image"
date: 2011-01-24
forum: Desktop Environments
---

### Post by Zilioum on 2011-01-24
I'm currently writing a little script that gets a random image from the xkcd website and then sets it as the desktop background. I grab the picture with wget, and to prevent the script from spamming by creating a new file for each image the new picture always gets downloaded to "wall.png".
Apparently this is a problem for gconftool-2. When I run the following command for the first time, the background changes:
```
gconftool-2 --set --type=string /desktop/gnome/background/picture_filename /home/zilioum/wall.png
```
But if I run my script, and then run the same command again nothing happens. It seems like gconftool-2 does not change the background if the filename stays the same even though the picture changes.

Things I tried but that don't work:
[LIST]
[*]setting the backround to a dummy location and then setting it to wall.png
[*]unsetting the value first, and then setting wall.png as background
[/LIST]

I could always download it to the actual filename, set that file as the background and then move that file to wall.png or delete it. But I'm wondering if there is a way to "smart up" gconftool-2.

Any ideas?

---

### Post by Krytarik on 2011-01-24
I use the "dummy" way and it works, I guess because I added an export of "DBUS_SESSION_BUS_ADDRESS" to the gconftool command, since after upgrading to Lucid gconf-tool sometimes doesn't worked without it. The following script I have running at my mum's machine, so don't wonder.;) You may well skip the "temp" part, I added it because of some unreliability of the server.
```
#!/bin/sh

# Get the pid of nautilus
nautilus_pid=$(pgrep -u $LOGNAME -n nautilus)

# If nautilus isn't running, just exit silently
if [ -z "$nautilus_pid" ]; then
exit 0
fi

# Grab the DBUS_SESSION_BUS_ADDRESS variable from nautilus's environment
eval $(tr '\0' '\n' < /proc/$nautilus_pid/environ | grep '^DBUS_SESSION_BUS_ADDRESS=')

# Check that we actually found it
if [ -z "$DBUS_SESSION_BUS_ADDRESS" ]; then
#echo "Failed to find bus address" >&2
exit 1
fi

# export it so that child processes will inherit it
export DBUS_SESSION_BUS_ADDRESS

# delete temp image
rm -f ~/Bilder/WHV-temp.jpg
# get image and save in my HOME
wget -o /dev/null -q -t 3 -T 8 -O ~/Bilder/WHV-temp.jpg http://hotel-seerose.dyndns.org:8001/record/current.jpg

# check if image is valid
if [ -s ~/Bilder/WHV-temp.jpg ]; then
# copy temp image over original image
cp ~/Bilder/WHV-temp.jpg ~/Bilder/WHV.jpg
# reset background with a non-existent image
# if you don't use this, then next line will not update the wallpaper
gconftool -s -t string /desktop/gnome/background/picture_filename /usr/share/backgrounds/dummy.jpg
# load new desktop background image
gconftool -s -t string /desktop/gnome/background/picture_options centered
gconftool -s -t string /desktop/gnome/background/picture_filename ~/Bilder/WHV.jpg
else
# reset background with a non-existent image
# if you don't use this, then next line will not update the wallpaper
gconftool -s -t string /desktop/gnome/background/picture_filename /usr/share/backgrounds/dummy.jpg
# load new desktop background image
gconftool -s -t string /desktop/gnome/background/picture_options scaled
gconftool -s -t string /desktop/gnome/background/picture_filename ~/Bilder/WHV/KW-Brücke-2.jpg
fi
```

---

### Post by Zilioum on 2011-01-25
Thanks a lot for your nice anser. I tried out the "export" trick, but I couldn't get it to work.

```
export DBUS_SESSION_BUS_ADDRESS

 gconftool-2 --set --type=string /desktop/gnome/background/picture_filename /usr/share/backgrounds/dummy.jpg
 
gconftool-2 --set --type=string /desktop/gnome/background/picture_filename $(pwd)/wall.png
```

This did not change the background, even though wall.png changed.
What is the purpose of "export DBUS_SESSION_BUS_ADDRESS" supposed to be?

---

### Post by Krytarik on 2011-01-25
> **Zilioum said:**
> 
What is the purpose of "export DBUS_SESSION_BUS_ADDRESS" supposed to be?
I'm not really sure, since I've not researched it enough. But I believe it passes the "address" of the running session to the command you run after it.

I know, one wouldn't expect it to be necessary regarding gconftool, me neither, but it definetely didn't work without it when run from crontab, after I upgraded to Lucid, although I'm not sure if it is still necessary, or if it was just a temporary error after the upgrade. The time I searched for a fix to that matter, this solution was proposed, and it worked.

I've just yet extensively tested a similar script at my machine, but only from within a terminal. I removed the DBUS part, removed the "delete old image" part, and even created a real dummy image: it worked in either case.

Sorry, seems that Gnome is buggy in your case. As a workaround you could have 2 images, which get used alternately.

---

### Post by Zilioum on 2011-01-28
I got it to work now, I download it to the actual filename, set it as background and then move it to always the same filename - like that I don't clutter the directory with unused files.

```

#Downloads the image and saves it under its appropriate name.
wget --output-document="$name_pic"  "$url"

#Sets the desktop background
gconftool-2 --set --type=string /desktop/gnome/background/picture_filename $(pwd)/"$name_pic"

mv "$name_pic" current_xkcd_wallpaper.png


```
The last problem I have now, is that the script only works if I run it with a launcher or with a compiz keyboard shortcut. If I use normal keyboard shortcut, it doesn't work.

Thanks for your help anyway!

---

### Post by Krytarik on 2011-01-28
Glad that it works now. But I'm surprised that the desktop background doesn't get lost after renaming the file you just set before as background! Who would think of that?! I just yet tested it at my machine.

---

### Post by vmarceau on 2012-03-14
I recently ran into the same problem in 11.10.

To solve it, I installed **dconf-tools**. In the **dconf-editor**, I just set the path to my current wallpaper file (for example ~/Pictures/wallpaper.jpg) in org.desktop.gnome.background.picture-uri.

Now when I modify my wallpaper file (~/Pictures/wallpaper.jpg), my background image automatically refreshes.

---

### Post by Krytarik on 2012-03-14
> **vmarceau said:**
> I recently ran into the same problem in 11.10.

To solve it, I installed **dconf-tools**. In the **dconf-editor**, I just set the path to my current wallpaper file (for example ~/Pictures/wallpaper.jpg) in org.desktop.gnome.background.picture-uri.
You know, this thread is from a time well before Gnome 3, so no DConf back then, buddy. :P

Regards.

---

### Post by jabuci on 2012-04-05
Try this:

```
gsettings set org.gnome.desktop.background picture-uri file:///path/to/img.jpg
```More info [here]("http://askubuntu.com/questions/66914/how-to-change-desktop-background-from-command-line-in-unity").

---

### Post by Krytarik on 2012-04-05
> **jabuci said:**
> Try this:

```
gsettings set org.gnome.desktop.background picture-uri file:///path/to/img.jpg
```More info [here]("http://askubuntu.com/questions/66914/how-to-change-desktop-background-from-command-line-in-unity").
Yeah, that's again for Gnome 3 - maybe we should stick to the original topic. ;-)

---

### Post by EvolutionByMemes on 2012-05-10
> **Krytarik said:**
> Yeah, that's again for Gnome 3 - maybe we should stick to the original topic. ;-)

Worked for me :), I don't care how old the original post was, I found it today, so apparently it is still relevant! :) Thanks again! (I used this to modify the Random NASA Wallpaper script so it would work on Ubuntu 12.04) :guitar:

---

