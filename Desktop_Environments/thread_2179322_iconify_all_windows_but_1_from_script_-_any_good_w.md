---
title: "iconify all windows but 1 from script - any good way to?"
date: 2013-10-07
forum: Desktop Environments
---

### Post by Dreamer Fithp Apprentice on 2013-10-07
I want a script to reversibly iconify or somehow make invisible all but one window or to do it to all windows and allow me to restore the one I want visible. Here is the relevant portion of the script wherein I tried to do it with wmctrl:```
wmctrl -k on
# The final " &" is necessary. Without it no more commands are processed until dclock is killed.
dclock -bg black -fg red -led_off black -noblink -fade -geometry =600x300+500+200 &
wmctrl -a "dclock"
```That doesn't work. Dclock remains invisible. I believe that's because ```
wmctrl -k on
``` isn't really iconofying the windows as is often said but rather "showing the desktop" which I think means more or less that the desktop is above everything else. So while ```
wmctrl -a "dclock"
```works fine if the window was iconofied by hand clicking the "-" in the window border windows made invisible by ```
wmctrl -k on
``` are obscured by the desktop on "top" of them, regardless of whether they are iconofied, restored or maximised. And that state apparently can't be overriden by any command I've found, short of reversing it which restores ALL windows.

At the moment I see 3 more ways that may work:

1-Do one of those "for window in . . ." things and find a command that iconifies them individually and then restore the one I want with ```
wmctrl -k on
```. If nobody suggests anything more elegant that's probably what I'll try next.

2-There is a thread on a German ubuntu forum that seems to deal with this. I could try machine translation but I haven't had much luck with machine translation in the past.

3-Try to do it with openbox commands. The presence of ```
--sm-save-file <FILE>
            Specify file to load a saved session from.
```in the man page seems to indicate I can somehow save a session, though it doesn't say how, do```
 openbox --exit
```,load openbox again and open dclock in it, then later kill openbox again and reload from the saved session file.

Method 1 would probably work though it seems surprisingly inelegant and makes me wonder if there is some simpler command I just haven't found, which is why I'm asking.

Method 2 doesn't sound at all promising but I'll try it as a last resort.

Method 3 seems a bit like swatting flies with a sledge hammer.

So if anybody thinks I've missed something obvious, plese let me know. Thanks.

---

### Post by vasa1 on 2013-10-07
I hope this isn't regarded as derailing your thread, but why do you use dclock? 

And what exactly are you trying to achieve? Do you simply want a shortcut (key or mouse combination) to "toggle" dclock's visibility?

And though you initially indicate you want a general solution, later you only mention dclock.

---

### Post by Dreamer Fithp Apprentice on 2013-10-08
Thanks, Vasa1.
> **vasa1 said:**
> why do you use dclock?Because it can be easily tweaked to have precisely the appearance I want - low total screen luminance, numerals large enough to be easily read from several feet away by an extremely nearsighted person, numerals that fade gradually through a transition without an annoying flicker effect, red numerals against a featureless black background. Red light impairs night vision less and is more conducive to sleep. It makes a much easier to read clock than any hardware clock I can buy and none of the other nix clocks I've looked at seem quite as suitable. It is the ideal bedroom clock to read in a dark room.

> **vasa1 said:**
> And what exactly are you trying to achieve?A menu item, or perhaps I'll put it on the panel, that will leave whatever I have the computer doing alone and just let it run, will lock the keyboard and mouse with xtrlock and display only the time until I unlock xtrlock with my password. If I bump the keyboard or a cat walks across it it won't affect whatever I left the machine doing in the background. Kind of like a screenlocker except it will be displaying useful information instead of a logo or screensaver art. All of which is easy enough to do by hand with a series of some gui and some cli actions. But I want to automate it so I only have to click a button or a menu item. Because I'm lazy. Because it would be cool. For the mental exercise. For the fun of it. And because I really would like to have a clock that's easy to read at 3:00 a.m.

> **vasa1 said:**
> And though you initially indicate you want a general solution, later you only mention dclock.I AM interested in the general case. At the moment I am trying to do this PARTICULAR script. Doing this PARTICULAR script is what made me WONDER about the general case. And this script is a perfectly good EXAMPLE of the general case. Doing it with a "for window_title in . . . " type of construction shouldn't be that hard but I figured there is probably some more elegant way built into openbox to minimise all windows. After all, even Windows has a keyboard shortcut for that. And there is way to script issuing control-this or alt-that if there isn't an actual command. I can't be the first person using openbox to think of a use for something like this. So probably it's already there and I just haven't found it. But now I'm thinking maybe not. I've been looking and I haven't found it. Guess I'll have to do it the longer way.

---

### Post by stinkeye on 2013-10-08
**@ Dreamer Fithp Apprentice**

Have you looked at conky at all.
You can pretty much display what you like and you can set the window properties in the config.
I have various conkys I toggle on and off with scripts.

---

### Post by Dreamer Fithp Apprentice on 2013-10-08
> **stinkeye said:**
> **@ Dreamer Fithp Apprentice**

Have you looked at conky at all . . . Not until now. Looks like a pretty useful program. I'll install and study it. Thanks a bunch, Stinkeye.

---

### Post by stinkeye on 2013-10-08
> **Dreamer Fithp Apprentice said:**
> Not until now. Looks like a pretty useful program. I'll install and study it. Thanks a bunch, Stinkeye.
Ok. Here's a config for a digital clock.
When you run "conky" it will look for a config @ **~/.conkyrc** and if this file doesn't exist 
it will use a sample config from **/etc/conky/conky.conf**

Save as **.conkyrc** to your home directory.
```
###  Begin Window Settings  ##################################################
## Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent no
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky
own_window_class Conky
own_window_title desk-clock
own_window_colour black

## ARGB can be used for real transparency
## NOTE that a composite manager is required for real transparency.
## This option will not work as desired (in most cases) in conjunction with
## own_window_type normal
# own_window_argb_visual yes # Options: yes or no

## When ARGB visuals are enabled, this use this to modify the alpha value
## Use: own_window_type normal
## Use: own_window_transparent no
## Valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity.
# own_window_argb_value 200

## Use the Xdbe extension? (eliminates flicker)
## It is highly recommended to use own window with this one
## so double buffer won't be so big.
double_buffer yes

minimum_size 100	## width, height
maximum_width 	## width

gap_x 0	## horizontal
gap_y 250	## vertical

alignment tm
####################################################  End Window Settings  ###
###  Font Settings  ##########################################################
## Use Xft (anti-aliased font and stuff)
use_xft yes
xftfont ubuntu:bold:size=12

## Alpha of Xft font. Must be a value at or between 1 and 0 ###
xftalpha 1
## Force UTF8? requires XFT ###
override_utf8_locale yes

uppercase no
######################################################  End Font Settings  ###
###  Color Settings  #########################################################
draw_shades no #no # amplifies text if yes
default_shade_color 000000

draw_outline no # amplifies text if yes
default_outline_color 000000

default_color DCDCDC #220 220 220 Gainsboro
#default_color C0C0C0 #192 192 192 Silver
#default_color B0E0E6 #176 224 230 PowderBlue
color0 8FBC8F #143 188 143 DarkSeaGreen
color1 778899 #119 136 153 LightSlateGray
color2 B0E0E6 #176 224 230 PowderBlue
color3 9ACD32 #154 205  50 YellowGreen
color4 FFA07A #255 160 122 LightSalmon
color5 FFDEAD #255 222 173 NavajoWhite
color6 00BFFF #  0 191 255 DeepSkyBlue
color7 5F9EA0 # 95 158 160 CadetBlue
color8 BDB76B #189 183 107 DarkKhaki
color9 CD5C5C #205  92  92 IndianRed
#####################################################  End Color Settings  ###
###  Borders Section  ########################################################
draw_borders no
## Stippled borders?
stippled_borders 0
## border margins
border_inner_margin 9
border_outer_margin 0
## border width
border_width 0
## graph borders
draw_graph_borders #no
#default_graph_size 15 40
#####################################################  End Borders Secton  ###
###  Miscellaneous Section  ##################################################
## Boolean value, if true, Conky will be forked to background when started.
background no

## Adds spaces around certain objects to stop them from moving other things
## around, this only helps if you are using a mono font
## Options: right, left or none
use_spacer none

## Default and Minimum size is 256 - needs more for single commands that
## "call" a lot of text IE: bash scripts
text_buffer_size 512

## Subtract (file system) buffers from used memory?
no_buffers yes

## change GiB to G and MiB to M
short_units yes

# Like it says, ot pads the decimals on % values
# doesn't seem to work since v1.7.1
pad_percents 2

## Imlib2 image cache size, in bytes. Default 4MiB Increase this value if you use
## $image lots. Set to 0 to disable the image cache.

imlib_cache_size 0

##   Maximum size of user text buffer, i.e. layout below TEXT line in config file
##  (default is 16384 bytes)
# max_user_text 16384

## Desired output unit of all objects displaying a temperature. Parameters are
## either "fahrenheit" or "celsius". The default unit is degree Celsius.
# temperature_unit Fahrenheit
##############################################  End Miscellaneous Section  ###

update_interval 1

#lua_load ~/conky/lua/draw_bg_vindsl2.lua
#lua_draw_hook_pre draw_bg

[COLOR="#FF0000"]TEXT[/COLOR]

${color CB3030}${font LCDMono:size=200}${time %l:%M}${font LCDMono:size=60}${time %S}${font}
${voffset 40}${font LCDMono:size=20}${alignc}${time %A %e %B}${voffset -10}
```

In the conkyrc above [COLOR="#FF0000"]"TEXT"[/COLOR] are the configuration settings and below "TEXT" are the variables to determine what is displayed.

The above conkyrc includes a brief explanation of some of the configuration settings.
See **man conky**
This conky is set to below other windows with the setting in the conkyrc....
```
own_window_hints undecorated,**below**,skip_taskbar,skip_pager,sticky
```
Change to **above** if that's what you want.

You will need [**_[COLOR="#B22222"]this font[/COLOR]_**]("http://www.dafont.com/lcd-lcd-mono.font").


This script can be used to toggle conky on/off.
```
#!/bin/bash

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
	exec killall conky 
else
	conky
fi
```

---

### Post by Dreamer Fithp Apprentice on 2013-10-08
OK, lads, I got it. For the benifit of anyone interested, including future visitors dropping in via a search service:

Somebody else was trying to do something similar with openbox under crunchbang and Kaokao posted a python script to minimise all but the active window here:
[http://crunchbang.org/forums/viewtopic.php?id=28195](http://crunchbang.org/forums/viewtopic.php?id=28195)
Realizing that if I invoked the window I wanted showing last, I could do without the exception and the restore step, so I modified it to remove the exception:```
#!/usr/bin/env python
import wnck
import gtk

screen = wnck.screen_get_default()

while gtk.events_pending():
    gtk.main_iteration()

windows = screen.get_windows()

for w in windows:
    w.minimize()

```I called that script with this one:```
#!/bin/bash

# To minimise stuff visible on the screen
/custom/scripts/minimise_all_windows.sh
killall lxpanel

# The final " &" is necessary. Without it no more commands are processed until dclock is killed.
dclock -bg black -fg red -led_off black -noblink -fade -geometry =600x300+500+200 &

#This locks keyboard and mouse buttons.
xtrlock

#This command won't run until xtrlock is unlocked. Having it here makes killing dclock happen automatically as a consequence of unlocking. Otherwise it hang on until I killed it from a cli.
killall dclock
lxpanel --profile Lubuntu
```And I put an entry pointing that script in my openbox menu.

So it works. Thank you both. Now I just need to figure out how to hook the alarm functon to a firehose and I'll be up in the morning . . .

---

### Post by Dreamer Fithp Apprentice on 2013-10-08
Sorry, Stinkeye. I hadn't seen your last post when I posted that. I get interrupted a lot. Probably I locked the screen for a while to tend to something else and came back to it. I'll study your method. Conky looks like something I'd want to learn anyway. Thanks much.

Here's a screenshot, btw.[IMG]http://postimg.org/image/xjzs2lwvf/[/IMG]

---

### Post by Dreamer Fithp Apprentice on 2013-10-09
Now why didn't that work? I'll try again.

[http://postimg.org/image/xjzs2lwvf/](http://postimg.org/image/xjzs2lwvf/)

[IMG]http://postimg.org/image/xjzs2lwvf/[/IMG]

---

