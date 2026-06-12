---
title: "Gnome-Do and stalonetray"
date: 2009-04-23
forum: General Help
---

### Post by Knad on 2009-04-23
Hello everyone!

I have been trying to use stalonetray (stand alone tray) with Gnome-Do, with Do set to have its own space (maximised windows do not cover it).

I am wondering how do I get stalonetray to go down into this area, and sit in the bottom right corner. I have attached a screenshot, with my stalonetray config below.

Also, stalonetray hides when I use SUPER+D (shortcut to go to desktop), how to I stop it from doing this?

Thanks all

.stalonetrayrc
```
geometry 104x20-0-0
sticky 1
transparent 0
skip_taskbar 1
window_type dock
grow_gravity W
icon_gravity SE
ignore_icon_resize TRUE
respect_icon_hints false
max_height 20
icon_size 20
```

---

### Post by erik.roelofs on 2009-05-13
Hi Knad,

I was looking for exactly the same and found a perfect alternative in "trayer". I'm using it like this and am totally happy! 

```
# trayer --SetDockType true --distance 5 --padding 10 \
        --transparent true --alpha 240 \
        --edge bottom --align left --expand false \
        --widthtype request --heighttype pixel --height 30

```

Getting rid of my panels... ;)

(ps: align left because I have 2 monitors and using the left as primary...)

Cheers,
ER(ik)

---

### Post by nonanano on 2009-12-16
I'm pretty much a Linux noob, but this is my tray script that I put in my /home/<username>/bin. In case there is anybody out there who know's even less than me, it allows you to call the script every time you make a change and that update will be applied. For me it fits neatly in the title bar just to the left of the other buttons I have there and is quite minimal, which is what I was looking for. I used to use standAloneTray but found that it would often be missing a lot of the tray icons until I reset it. The only thing I miss from it was being able to set a background image for the tray. In trayer you are restricted to one color and an alpha transparency which link other trays is only a pseudo transparency which is applied to your current background image at load time.

[IMG]http://img121.imageshack.us/img121/5677/trayer.png[/IMG]

```
killall trayer
trayer \
	--edge top \
	--align right \
	--margin 100 \
	--widthtype request \
	--heighttype pixels \
	--height 23 \
	--SetDockType true \
	--SetPartialStrut false \
	--transparent true \
	--alpha 120 \
	--tint 0x000000 \
	--distance 0 \
	--expand true \
	--padding 0 &

# edge left|right|top|bottom|none
#	Specifies a screen edge to use.
#
# align left|center|right
#	Specifies an align of the icons.
#
# margin <size>
#	Specifies length of margin (in pixels)
#
# widthtype request|pixel|percent
#	Specifies method of calculating trayer's window width:
#
#	request - Follow application icons' size, so trayer may shrink or expand dynamically.
#	pixel - Set a fixed size, given with --width option in pixels.
#	percent - Set a fixed size, given with --width option in percentage of a lenght of screen edge.
#
# width <size>
#	Width of trayer's window. Ignored when --widthtype is set to request.
#
# heighttype request|pixel|percent
#	Specifies method of calculating trayer's window height:
#
#	request - Follow application icons' size, so trayer may shrink or expand dynamically.
#	pixel - Set a fixed size, given with --height option in pixels.
#	percent - Set a fixed size, given with --height option in percentage of a lenght of screen edge.
#
# height <size>
#	Height of trayer's window. Ignored when --heighttype is set to request.
#
# SetDockType true|false
#	Identify panel window type as dock (ie. always ontop).
#
# SetPartialStrut true|false
#	Reserve panel space so that it will not be covered by maximized windows.
#
# transparent true|false
#	Use transparency.
#
# alpha <value>
#	Percentage of transparency (0 - nontransparent, 255 - fully transparent)
#
# tint <color>
#	Color  used  to  tint transparent background. Color is given as a 24-bit C hexadecimal integer, for example:
#	0xff0000 is red, 0xff8800 is orange and 0x00ff00 is green.
#
# distance <length>
#	Specifies distance between trayer's window and screen edge (in pixels)
#
# expand true|false
#	Specifies whether trayer may accomodate extra space when there is too much icons.
#
# padding <size>
#	Extra space between icons and trayer window's border.
```

---

### Post by msrinath80 on 2010-07-13
nonanano :) Thanks so very much for your elaborate script. It is thanks to folks like you that life becomes so much easier in the community. Once again, thanks very much for sharing.

---

