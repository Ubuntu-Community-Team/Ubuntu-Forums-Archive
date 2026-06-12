---
title: "wp_tray 5.1"
date: 2005-11-25
forum: Desktop Environments
---

### Post by cabbage on 2005-11-25
Dear all,

I have been trying to get the latest version of wp_tray working (v5.1 from [http://planetearthworm.com/projects/wp_tray/index.php)](http://planetearthworm.com/projects/wp_tray/index.php)). As there is no deb package for download I've compiled from source as guided by the wiki ([https://wiki.ubuntu.com/WallpaperTray?highlight=%28wallpaper%29)](https://wiki.ubuntu.com/WallpaperTray?highlight=%28wallpaper%29)).

All is well, until I try adding the applet. When it tries to start I get the following error:

> The panel encountered a problem while loading "OAFIID:wp_tray"

I have no idea what this means. Can anyone help?


Thanks...

---

### Post by rwabel on 2005-11-27
[quote=cabbage]Dear all,

I have been trying to get the latest version of wp_tray working (v5.1 from [http://planetearthworm.com/projects/wp_tray/index.php)]("http://planetearthworm.com/projects/wp_tray/index.php%29"). As there is no deb package for download I've compiled from source as guided by the wiki ([https://wiki.ubuntu.com/WallpaperTray?highlight=%28wallpaper%29)]("https://wiki.ubuntu.com/WallpaperTray?highlight=%28wallpaper%29%29").

All is well, until I try adding the applet. When it tries to start I get the following error:



I have no idea what this means. Can anyone help?


Thanks...[/quote]

unfortunately I get the same problem with that version too. I've no idea what the problem could be. The developer is unreachable and no new release has been made. It's really a pity as such a feature should be default in gnome

---

### Post by Dr. Nick on 2005-11-27
cant fix your wp_tray problems but this has some of the functionality
Credit to poptones in this thread [http://www.ubuntuforums.org/showthread.php?t=49336&page=7&highlight=gnome+wallpaper+changer](http://www.ubuntuforums.org/showthread.php?t=49336&page=7&highlight=gnome+wallpaper+changer)
Paste the below code in a new file and save as randombackground.sh Then run it and it picks a random wallpaper, I made a shortcut to it in my panel so clicking a panel icon picks a random picture, You can also use system-prefrences-session to add it to startup.

Other people have made similar scripts but this is the easiest i've seen so far. 

```
#!/bin/bash
WALLPAPERS=~/wallpapers

# find the identity of the current wallpaper...
# get the name...
THISONE=`gconftool-2 -g /desktop/gnome/background/picture_filename`

# Chop off the path
THISONE=${THISONE##*/}

# locate the filename by index in this directory
THISONE=`ls -1 $WALLPAPERS | grep -n $THISONE`

# make the grep string into a valid number
THISONE=0${THISONE%%:*}

# get a directory list
ALIST=( `ls -1 $WALLPAPERS` )

# get the number of lines in that list
RANGE=${#ALIST[@]}

# programmers trick to make a 'while' loop that runs at least once...
lastnum=1
number=1

while [[ "$lastnum" -eq "$number" ]]; do
# Now randomize until we have a new number that is not the same as the old one...
	let lastnum=$THISONE
	let "number = $RANDOM + $lastnum"
	let "number = $number % $RANGE"
done

# Set wallpaper to selection indexed by new "number"
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}

```

change /wallpapers to your directory of pics

---

### Post by rwabel on 2005-11-27
a nice alternative is [this]("http://www.ubuntuforums.org/showpost.php?p=278033&postcount=41") little to by geraldo5002. but you need mono for it. it's similar to wp-tray

---

