---
title: "Problem with USDF's random wallpaper script"
date: 2006-11-01
forum: Desktop Environments
---

### Post by PriceChild on 2006-11-01
Used this guide here: [http://doc.gwos.org/index.php/Randomizing_Wallpaper](http://doc.gwos.org/index.php/Randomizing_Wallpaper)

and here is my script (placed in /usr/local/bin) without all the quotes so easier to make sense of:```
#!/bin/sh

NIMGS=`find /home/pricechild/photos -iname '*.jpg' | tr -d ' '`
IMGS=`find /home/pricechild/photos -iname '*.jpg' -printf "%p#"`

N=`echo $NIMGS | wc -w`

((N=RANDOM%N))

BGNAME=`echo $IMGS | cut -d '#' -f $N`

gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$BGNAME"

gconftool-2 -t str --set /desktop/gnome/background/picture_options "stretched"
```The script will choose a photo and set it as background perfectly... but its always the same photo!```
$ ls /home/pricechild/photos
DoE Gold 05    DoEGold06  glyderai        NZ
DoE Gold 05 p  feeder05   gold06assessed  snowdon06
```Atm there's just folders full of photos there... but i've tried with a couple of photos in there, and its chosen one the whole time... something's not working in the "random" department... any ideas anyone?

---

### Post by CatKiller on 2006-11-01
This is the one I use:

```
#!/usr/bin/env python

BACKGROUND_DIRS = ['/usr/share/backgrounds', '~/backgrounds']

import os, glob, random, itertools, gconf

files = list(itertools.chain(*[[os.path.join(dirpath, name)
                                for name in filenames]
                               for dirpath, dirnames, filenames in
                               itertools.chain(*[os.walk(os.path.expanduser(d))
                                                 for d in BACKGROUND_DIRS])]))
gconf.client_get_default().set_string(
    '/desktop/gnome/background/picture_filename',
    random.choice(files))

```

---

### Post by PriceChild on 2006-11-01
Perfect :)

Thanks... i'll see about getting that into the USDF instead... Is there an original source i can quote?

---

### Post by mbeierl on 2006-11-01
Okay, I went way nuts and modified the script to adapt to my ever changing xorg layouts and whether or not I am currently running Beryl.

The nicest part that I like about this is that I have a hack that puts different images on each of my two displays using the "montage" command from the "imagemagick" package.

This assumes three directories are present:

~/downloads/wallpaper/normal (for 4:3 aspect)
~/downloads/wallpaper/widescreen (16:9)
~/downloads/wallpaper/montage (re-written temporary storage for dual image montages - don't store anything in here!)

```

#!/bin/sh 

if [ -z `pidof beryl` ]
then
        grep Xinerama /etc/X11/xorg.conf > /dev/null
        if [ $? -eq 0 ]
        then
                option=stretched
                dir=widescreen
                montage=true
                tile=2x2
                geometry=1280x800
                option=wallpaper
                dir=normal
        else
                #grep MergedFB /etc/X11/xorg.conf > /dev/null
                grep Above /etc/X11/xorg.conf > /dev/null
                if [ $? -eq 0 ]
                then
                        montage=true
                        tile=1x2
                        geomtery=1280x966
                        option=wallpaper
                        dir=normal
                else
                        option=scaled
                        dir=normal
                fi
        fi
else
        # beryl is running
        option=centered
        dir=normal
fi

cd ~/downloads/wallpaper/$dir

if [ -z $1 ]
then
#Just one location allowed, sorry

        IMGS=`find . -iname '*.jpg' -o -iname '*.png' -o -iname '*.svg'`
        N=`echo $IMGS | wc -w`
        #Find out how many pictures we got

        ((N=RANDOM%N))
        #Take a random number between 1 and N
        N=`expr $N + 2`

        BGNAME=`echo $IMGS | cut -d '/' -f $N | cut -d ' ' -f 1`
        #We have to cut twice to get rid of an irritating " ." at the 
        #end after the first cut

else
        BGNAME=$1
fi

if [ ! -z $montage ]
then
        N=`echo $IMGS | wc -w`
        #Find out how many pictures we got

        ((N=RANDOM%N))
        #Take a random number between 1 and N
        N=`expr $N + 2`

        BGNAME2=`echo $IMGS | cut -d '/' -f $N | cut -d ' ' -f 1`
        #We have to cut twice to get rid of an irritating " ." at the 
        rm -f ~/downloads/wallpaper/montage/*
        nice montage -background black -tile $tile -geometry $geometry $BGNAME $BGNAME2 ../montage/img_$$.jpg
        BGNAME=img_$$.jpg
        dir=montage
fi

gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/home/mark/downloads/wallpaper/$dir/$BGNAME"
gconftool-2 -t str --set /desktop/gnome/background/picture_options "$option"
#Possible values are "none", "wallpaper" (eg tiled), "centered", "scaled", "stretched"

echo Background set to $BGNAME

```

---

### Post by CatKiller on 2006-11-01
> **PriceChild said:**
> Is there an original source i can quote?

[This]("http://ubuntuforums.org/showthread.php?t=18163&highlight=ranwp.py") looks like a fairly original source. I got it from a different thread on this forum somewhere though.

---

### Post by CatKiller on 2006-11-16
> **PriceChild said:**
> i'll see about getting that into the USDF instead...

Very nice. The cunning thing that I did with my launcher was to create a launcher that had the generic name for the icon of the Gnome utility that changes the background, so when you change theme, the launcher's icon changes to match. Commands you could use, then, might be

```
gedit Desktop/wallpaper.desktop
```

Then paste the following into it:

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Change your desktop wallpaper at random
Type=Application
Exec=wallpaper
TryExec=
X-GNOME-DocPath=
Terminal=false
GenericName=
Comment=
Icon=gnome-settings-background

```

Possibly you don't need all the lines in there - I cribbed it from something else. Of course, it's ugly on the Desktop, since it's got that ludicrous "Change your desktop wallpaper at random" name plastered across it. You can drag-and-drop it to the panel to make a copy there, and then the name becomes a tooltip in case you forget what it's for. The launcher can be safely deleted from the Desktop then. I just don't know a prettier way to make a launcher on the panel with a non-specific icon.

Well, you could make it with a specific icon, and then change it afterwards by changing the appropriate .desktop file in ~/.gnome2/panel2.d/default/launchers, but then you'd have to isolate which of the ludicrously-named .desktop files is the one you want to fiddle with. But no one wants to do that.

Hopefully these 5am ramblings are useful to someone.

---

