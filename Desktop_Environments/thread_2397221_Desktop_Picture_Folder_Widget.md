---
title: "Desktop Picture Folder Widget"
date: 2018-07-26
forum: Desktop Environments
---

### Post by Taylz on 2018-07-26
Hi all,

Does anyone know of a widget or desktop thing that will act like a small viewer for pictures stored in your pictures folder, rotating through them at certain intervals (set within the settings). I seen something similar on the KDE desktop environment but I didn't get on well with that environment because it felt very buggy and slow. However I did love the widget features for it!

Don't suppose XFCE has a similar widget system or option does it? So far I haven't managed to find it/one.

Regards,

Tayl.

---

### Post by Holger_Gehrke on 2018-07-27
To the best of my knowledge there no such thing as a desktop widget in XFCE. You can have the desktop "wallpaper" change among files from a specific directory at specifiable intervals.

Holger

---

### Post by again? on 2018-07-27
You could achieve this using conky and a script to select a random file from a directory.

_slideshow.sh_ (set your [COLOR="#FF0000"]pics directory[/COLOR] and make script executable)
```
#!/bin/sh

dir="[COLOR="#FF0000"]$HOME/Pictures[/COLOR]" # Directory
file=$(find "$dir" -type f -iname '*.jpg' -or -iname '*.jpeg' -or -iname '*.png' | shuf -n1)

cp "$file" ~/.currentpic
echo '${image ~/.currentpic -p 0,0 -s 400x300}'
exit 0
```


_conky config_ Save as **.conkyrc** in your home folder.  
(on last line set [COLOR="#FF8C00"]your path to slideshow.sh[/COLOR] and set slideshow [COLOR="#800080"]interval[/COLOR] in secs).
```
background no
update_interval 1
total_run_times 0

use_xft yes
xftfont Droid Sans:bold:size=12
alignment tr
xftalpha 1.0
own_window yes
own_window_title conkyslideshow
own_window_type normal
own_window_transparent no
own_window_colour blue
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky

double_buffer yes
draw_shades yes
draw_outline no
draw_borders yes
#stippled_borders 10
gap_y 60
gap_x 20

default_shade_color blue
default_outline_color blue
default_color blue
use_spacer none
no_buffers yes
uppercase no



text_buffer_size 512
override_utf8_locale yes

minimum_size 400 300  
maximum_width 400
#use_spacer left

max_user_text 4000


imlib_cache_size 0
imlib_cache_flush_interval 900

TEXT
${execpi [COLOR="#800080"]10[/COLOR] [COLOR="#FF8C00"]$HOME/scripts/slideshow.sh[/COLOR]}
```


to run
```
conky
```

**[COLOR="#FF0000"]EDIT:[/COLOR]** 
Been playing around and wrote an alternate slideshow.sh script to try. (Chooses random image without repetition)
As before....(set your [COLOR="#FF0000"]image directory[/COLOR] and make script executable)
```
#!/bin/sh

## Randomly selects images without repetition

## If you change Image Directory delete the ~/.piclist file 
## to create a new list on first run

dir="[COLOR="#FF0000"]$HOME/conky/slideshow[/COLOR]" # Image Directory
files=$(find "$dir" -type f -iname '*.jpg' -or -iname '*.jpeg' -or -iname '*.png')
uniquefiles=$(cat $HOME/.piclist | sort | uniq -u | wc -l)

## create list of images @ ~/.piclist 
if [ ! -f "$HOME/.piclist" ] ; then	
	notify-send -i info "Created list" "$HOME/.piclist"
	echo "$files" > ~/.piclist
fi

## checks for unique files ~/.piclist. Refreshes list if none
if [ "$uniquefiles" = "0" ] ; then	
	echo "$files" > ~/.piclist
fi

## select a pic and duplicate path in ~/.piclist so no longer unique   
currentpic=$(cat $HOME/.piclist | sort | uniq -u | shuf -n1)
echo "$currentpic" >> $HOME/.piclist

## copy selected pic to ~/.currentpic
cp "$currentpic" $HOME/.currentpic

## output parsed by conky
echo '${image ~/.currentpic -p 0,0 -s 400x300}'
exit 0
```

---

