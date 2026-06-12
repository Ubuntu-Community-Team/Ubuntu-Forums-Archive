---
title: "a ripple when getting a new message in gaim?"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by Choad on 2007-08-21
saw this wicked video

[http://www.youtube.com/watch?v=IcOZMGuieDU](http://www.youtube.com/watch?v=IcOZMGuieDU)

any way i can get that for gaim/gnome?

---

### Post by aidanr on 2007-08-21
[http://forum.compiz-fusion.org/showthread.php?t=2191](http://forum.compiz-fusion.org/showthread.php?t=2191)

---

### Post by Choad on 2007-08-21
i followed the instructions but alas no dice. i am not using pidgin, and i am not using compiz-fusion... so there's 2 possible causes right there. using gaim 2.0.0beta6 and beryl

---

### Post by aidanr on 2007-08-21
so wherever it says pidgin replace it with gaim, and wherever it says compiz replace it with beryl, make sure you have the water plugin and dbus plugin loaded in beryl-settings

---

### Post by Choad on 2007-08-21
oh close! i got the ripple now, and it looks purty, but it's in the top left. i have read the thread and tried the fixes but alas it isn't working. here are my 2 files

senicon.sh
```
#!/bin/bash
#requires waterping.sh
WINFO=`xwininfo -root -tree | egrep ' (1[2-9]|2[0-4])x(1[2-9]|2[0-4])\+0\+0' | grep "$1" | cut -d ')' -f 2-`
WIW=`echo $WINFO | cut -d 'x' -f 1`
WIH=`echo $WINFO | cut -d 'x' -f 2 | cut -d '+' -f 1`
WIX=`echo $WINFO | cut -d '+' -f 4`
WIY=`echo $WINFO | cut -d '+' -f 5`
let WAX=WIX+WIW/2
let WAY=WIY+WIH/2
waterping.sh $WAX $WAY 2>/dev/null
```

waterping.sh
```
#!/bin/bash
#Panel layout - Top || Bottom || Left || Right
LAYOUT="Top"

if [ "x$1" == "x" ]; then
echo "Please specify the icon name, f. ex. 'gaim' as parameter 1";
exit 0
fi

WINFO=`xwininfo -root -tree -name "$LAYOUT Edge Panel"| grep "$1" | cut -d ')' -f 2-`
WIW=`echo $WINFO | cut -d 'x' -f 1`
WIH=`echo $WINFO | cut -d 'x' -f 2 | cut -d '+' -f 1`
WIX=`echo $WINFO | cut -d '+' -f 4`
WIY=`echo $WINFO | cut -d '+' -f 5`
let WAX=WIX+WIW/2
let WAY=WIY+WIH/2

dbus-send --type=method_call --dest=org.freedesktop.beryl /org/freedesktop/beryl/water/allscreens/point org.freedesktop.beryl.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'` string:'amplitude' double:1 string:'x' int32:$WAX string:'y' int32:$WAY
```

thanks for your help btw

---

### Post by aidanr on 2007-08-21
ok, first of all you only need the second file

now, in a terminal type xwininfo and click on your gaim icon, it'll spit out some info, look for
```
xwininfo: Window id: 0x1000020 "Xfce Panel"
```
and in the script where it says
```
WINFO=`xwininfo -root -tree -name "$LAYOUT Edge Panel"| grep "$1" | cut -d ')' -f 2-`
```

replace "$LAYOUT Edge Panel" with "Xfce Panel" (or whatever it is for gnome), that's what i had to do to get the ripple on the panel instead of the top left

---

### Post by Choad on 2007-08-21
sweet you are a hero!

---

### Post by cudds on 2007-08-25
I'm having problems getting the ripple in the correct place.

My two codes are
```
#!/bin/bash
#Panel layout - Top || Bottom || Left || Right
LAYOUT="Bottom"

if [ "x$1" == "x" ]; then
echo "Please specify the icon name, f. ex. 'Pidgin' as parameter 1";
exit 0
fi

WINFO=`xwininfo -root -tree -name "Xfce Panel"| grep "$1" | cut -d ')' -f 2-`
WIW=`echo $WINFO | cut -d 'x' -f 1`
WIH=`echo $WINFO | cut -d 'x' -f 2 | cut -d '+' -f 1`
WIX=`echo $WINFO | cut -d '+' -f 4`
WIY=`echo $WINFO | cut -d '+' -f 5`
let WAX=WIX+WIW/2
let WAY=WIY+WIH/2

dbus-send --type=method_call --dest=org.freedesktop.beryl /org/freedesktop/beryl/water/allscreens/point org.freedesktop.beryl.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'` string:'amplitude' double:1 string:'x' int32:$WAX string:'y' int32:$WAY
```


and

```
#!/bin/bash
#requires waterping.sh
WINFO=`xwininfo -root -tree | egrep ' (1[2-9]|2[0-4])x(1[2-9]|2[0-4])\+0\+0' | grep "$1" | cut -d ')' -f 2-`
WIW=`echo $WINFO | cut -d 'x' -f 1`
WIH=`echo $WINFO | cut -d 'x' -f 2 | cut -d '+' -f 1`
WIX=`echo $WINFO | cut -d '+' -f 4`
WIY=`echo $WINFO | cut -d '+' -f 5`
let WAX=WIX+WIW/2
let WAY=WIY+WIH/2
waterping.sh $WAX $WAY 2>/dev/null
```

I've locate my xwininfo as

```
xwininfo: Window id: 0x100001d "Xfce Panel"

  Absolute upper-left X:  0
  Absolute upper-left Y:  774
  Relative upper-left X:  0
  Relative upper-left Y:  774
  Width: 1280
  Height: 26
  Depth: 24
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+774  -0+774  -0-0  +0-0
  -geometry 1280x26+0-0

```

but still get the ripple in the top left corner - any help will be greatfully received.

---

### Post by cudds on 2007-08-27
This is still racking my brains - I have my panel on the bottom - but the ripple is still coming from 0x0!
Help please :(

---

### Post by Depressed Man on 2007-08-27
I believe in the script itself you can specify top-left, top-right, etc. I actually asked that question myself in the forums.

---

### Post by cudds on 2007-08-29
> **Depressed Man said:**
> I believe in the script itself you can specify top-left, top-right, etc. I actually asked that question myself in the forums.

Dude - i got mine to work - seems I mixed up two scripts.

```
#!/bin/bash
#./waterping.sh 0 0
#If you want to ping the coordinates x0, y0
dbus-send --type=method_call --dest=org.freedesktop.beryl /org/freedesktop/beryl
/water/allscreens/point org.freedesktop.beryl.activate string:'root' int32:`xwin
info -root | grep id: | awk '{ print $4 }'` string:'amplitude' double:1 string:'
x' int32:$1 string:'y' int32:$2
```

```
#!/bin/bash
#requires waterping.sh
WINFO=`xwininfo -root -tree | egrep ' (1[2-9]|2[0-4])x(1[2-9]|2[0-4])\+0\+0' | g
rep "$1" | cut -d ')' -f 2-`
WIW=`echo $WINFO | cut -d 'x' -f 1`
WIH=`echo $WINFO | cut -d 'x' -f 2 | cut -d '+' -f 1`
WIX=`echo $WINFO | cut -d '+' -f 4`
WIY=`echo $WINFO | cut -d '+' -f 5`
let WAX=WIX+WIW/2
let WAY=WIY+WIH/2
waterping.sh $WAX $WAY 2>/dev/null

```

---

