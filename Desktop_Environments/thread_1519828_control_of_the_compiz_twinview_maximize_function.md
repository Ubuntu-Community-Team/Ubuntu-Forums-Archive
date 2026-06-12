---
title: "control of the compiz twinview maximize function"
date: 2010-06-28
forum: Desktop Environments
---

### Post by koekiemonster on 2010-06-28
Im running a dual monitor setup in gnome, with the closed nvidia drivers in twinview mode.
most of the times i want to be able to maximize windows to a single monitor (this is the default behavior in 10.04 lucid i believe), but sometimes i want to span a window on both screens.
compiz doesn't allow windows to resized past screenborders, and gdevilspie wasn't able to get past this.

after a lot of googling and toying around i came up with the following sollution, i'm posting it here so other people can enjoy it as well (and i'll be able to find it again after my next install ;) ).

i made a script to switch between the streched mode and the doublescreen mode
to use it, you'll have to stop the autodetection of the outputs in compiz. this option is found in compiz config settings manager under general settings > display settings
or though the gconf-editor in /apps/compiz/general/screen0/options/detect_outputs

this script switches between the two modes, but you need to edit the resolutions of your monitors! (i have a double 1280x1024 setup)
```

#!/bin/bash

THESCREENSETUP=`gconftool-2 -g /apps/compiz/general/screen0/options/outputs`

echo $THESCREENSETUP

if [[ ${THESCREENSETUP:1:9} == "1280x1024" ]] ; then
 echo "double output detected, switching to a single large one"
 gconftool-2 -s /apps/compiz/general/screen0/options/outputs -t list --list-type string "[2560x1024+0+0]"

else
 echo "single large output detected, switching to a double setup"
 gconftool-2 -s /apps/compiz/general/screen0/options/outputs -t list --list-type string "[1280x1024+0+0,1280x1024+1280+0]"
fi


```my way of using this:
1. use the script to switch to the span mode
2. start photo/video edit software
3. work
4. close the software
5. use the script to switch back

---

### Post by koekiemonster on 2010-06-28
after some more scripting and google-searching with the magic word (ultramon) i came up with a new script.

it allows you to span a window over 2 monitors

```

#!/bin/bash

# insert your own values here!
DUALSCREEN_HOR=2519
DUALSCREEN_VER=1023


#switching to a single large output"
gconftool-2 -s /apps/compiz/general/screen0/options/outputs -t list --list-type string "[2560x1024+0+0]"

sleep 1

#get the active window ID
activeWinLine=$(xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)")
activeWinID="${activeWinLine:40}"

#unmiximize the window
wmctrl -i -r $activeWinID -b remove,maximized_horz,maximized_vert
wmctrl -i -r $activeWinID -b remove,fullscreen
#resize the window
wmctrl -i -r $activeWinID -e 0,0,0,$DUALSCREEN_HOR,$DUALSCREEN_VER

#returning to two monitor output
gconftool-2 -s /apps/compiz/general/screen0/options/outputs -t list --list-type string "[1280x1024+0+0,1280x1024+1280+0]"

```save it somewhere, make it executable and give it a keybind (for instance with the compizconfig settings manager)

select the window you want to maximize, hit the keybind and wait 2 seconds.

---

### Post by purecharger on 2010-07-26
I have the exact opposite problem: after upgrading to 10.04 all my windows maximize across both monitors instead of snapping to a single one!

---

### Post by koekiemonster on 2010-07-30
> **purecharger said:**
> I have the exact opposite problem: after upgrading to 10.04 all my windows maximize across both monitors instead of snapping to a single one!

try this command, but make shure you edit the last part for your own screen resolutions (mine are 2x 1280x1024)
let me know if it doesn't work, then i'll get back to you when i'm home (thats 5 days from now)
sudo gconftool-2 -s /apps/compiz/general/screen0/options/outputs -t list --list-type string "[1280x1024+0+0,1280x1024+1280+0]"

---

### Post by celafon on 2010-08-23
You should probably change the grep command and patter to following:

```

activeWinLine=$(xprop -root | egrep '^_NET_ACTIVE_WINDOW\(WINDOW\)')

```

As the one you use does not always work (somehow the pattern was used in another property in my case).

---

