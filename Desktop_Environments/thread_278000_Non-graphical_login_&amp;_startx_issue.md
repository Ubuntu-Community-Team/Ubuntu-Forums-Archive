---
title: "Non-graphical login &amp; startx issue"
date: 2006-10-15
forum: Desktop Environments
---

### Post by Tangent on 2006-10-15
I have a couple of questions reguarding non-graphical login.

I can disable graphical login just fine, but when I get to the text, it's way off center, I have the correct video drivers installed, and it's fine in X, but it's kind of something that annoys me, because I prefer to not be in X at all times. My screen is already as far over to the left as I can have it to compensate, but it's not enough. Any suggestions would be greatly appreciated.

The other thing is that I'd like to have startx start fluxbox by default, but I can't find a good way to do that, since there isn't a .xinitrc file in ubuntu.

---

### Post by jpkotta on 2006-10-15
> **Tangent said:**
> I have a couple of questions reguarding non-graphical login.

I can disable graphical login just fine, but when I get to the text, it's way off center, I have the correct video drivers installed, and it's fine in X, but it's kind of something that annoys me, because I prefer to not be in X at all times. My screen is already as far over to the left as I can have it to compensate, but it's not enough. Any suggestions would be greatly appreciated.

The other thing is that I'd like to have startx start fluxbox by default, but I can't find a good way to do that, since there isn't a .xinitrc file in ubuntu.

There is an ~/.xinitrc if you make one.  What I do is have an ~/.xinitrc and link it to ~/.xsession, so that the same works for both GDM and startx.

```
ln -s ~/.xinitrc ~/.xsession
```

Here is my ~/.xinitrc.  Pardon the mess.
> echo "Starting X..."
echo
echo "PARAMETERS TO .xinitrc"
echo "$@"
echo "END OF PARAMETERS TO .xinitrc"
echo 

# set the wallpaper
# do this first because it can take a while
Esetroot -fit -center $HOME/tmp/current_wallpaper

# setup xmodmap, because certain programs (e.g. Mathematica and fvwm) require
# certain settings

# add some special keys
xmodmap -e "keycode 115 = Super_L"
xmodmap -e "keycode 116 = Super_R"
xmodmap -e "keycode 117 = Menu"
xmodmap -e "add mod4 = Super_L Super_R"
xmodmap -e "remove lock = Caps_Lock"

# disable caps lock and add keysyms for emacs
#xmodmap -e "remove Lock"
#xmodmap -e "keysym CapsLock = Undo Redo"

# volume keys for laptop
if [ x`hostname` = x"goedel" ] ; then
    xmodmap -e "keycode 160 = XF86AudioMute"
    xmodmap -e "keycode 174 = XF86AudioLowerVolume"
    xmodmap -e "keycode 176 = XF86AudioRaiseVolume"
fi 

# here's some old stuff that was once useful; can't remember why though...
#add mod4 = Multi_key
#clear mod3
#add mod1 = Mode_switch
#clear mod2
#add mod3 = Num_Lock

# make sure my X resources are updated
if [ -r "$HOME/.Xresources" ] ; then
    #xrdb -merge $HOME/.Xresources
    xrdb -load $HOME/.Xresources
fi

# turn on numlock
numlockx

# start screensaver daemon
exec xscreensaver &

# load nvidia settings
nvidia-settings -l

# start the sound server(s)
exec artswrapper -s 2 &
sleep 3
exec artsdsp esd -nobeeps -as 2 &

if [ x`hostname` = x"euler" ] ; then 
    # xcompmgr is more stable without gnome-panel
    exec xcompmgr -n &
fi    

# start my slick radar script
#exec $HOME/.fvwm/scripts/radar &

# postit notes
#exec xpad &

# start instant messenger
#exec gaim &

# I use this in various scripts
# it's the screen resolution in WxH format, e.g. 1280x960
export SCREEN_RES=`xdpyinfo | grep dimensions | grep -o '[0-9]*x[0-9]*[[:space:]]*pixels' | sed -e 's/pixels//' -e 's/[[:space:]]//'`
export SCREEN_RES_X=`echo $SCREEN_RES | sed -e 's/x.*//'`
export SCREEN_RES_Y=`echo $SCREEN_RES | sed -e 's/.*x//'`

# cd to $HOME, so that all programs started from X start there
cd

# just execute the parameters
# if the command fails, start an xterm as a failsafe
#if [[ -z "$@" ]] ; then 
#    xterm
#else 
#    "$@" || xterm
#fi
sleep 1
disp=`echo $DISPLAY | sed -e 's/://g' -e 's/[.][0-9]*//'`
#xterm
fvwm >$HOME/.X-log-${disp} 2>&1
#fvwm -f /dev/null >$HOME/.X-log-${disp} 2>&1
#twm >$HOME/.X-log-${disp} 2>&1
mv -f $HOME/.X-log-${disp} $HOME/.X-log-${disp}-old

echo 
echo "Shutting Down X..."
echo

```

```

---

### Post by Tangent on 2006-10-18
Thanks, that did the trick after a little tweaking. Thank you for the help.

---

