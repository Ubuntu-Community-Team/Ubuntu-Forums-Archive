---
title: "how to make fvwm work with ubuntu"
date: 2005-12-30
forum: Desktop Environments
---

### Post by shanmuha on 2005-12-30
is there any how-to on running fvwm2 in ubuntu as the desktop environment?

Thanks,
Shanmu.

---

### Post by jpkotta on 2006-01-08
I use FVWM by itself.  You can run it as GNOME's wm, but I've never bothered with that.  I can tell you that you need to run gnome-theme-manager to get the icons to show up in Nautilus.  I also run gnome-panel.  I needed a few styles to get it to behave (I want it to let itself be covered).```
Style gnome-panel   StaysOnBottom, GNOMEIgnoreHints

```

Obviously you have to install FVWM.  ```
sudo apt-get install fvwm
```

I believe all you have to do is make a script called ~/.xsession and run fvwm from it.  If you use startx instead, you need to call it ~/.xinitrc.  I just have a symlink from ~/.xinitrc to ~/.xsession.  Not sure if it needs to be executable or not, mine is for some reason.  Here is my ~/.xinitrc:
```
echo "Starting X..."
echo
echo "PARAMETERS TO .xinitrc"
echo "$@"
echo "END OF PARAMETERS TO .xinitrc"
echo 

# set the wallpaper
# do this first because it can take a while
Esetroot -fit -center `cat $HOME/tmp/current_wallpaper`

# setup xmodmap, because certain programs (e.g. Mathematica and fvwm) require
# certain settings

# add some special keys
xmodmap -e "keycode 115 = Super_L"
xmodmap -e "keycode 116 = Super_R"
xmodmap -e "keycode 117 = Menu"
xmodmap -e "add mod4 = Super_L Super_R"
xmodmap -e "remove lock = Caps_Lock"

# disable caps lock and add keysyms for emacs
xmodmap -e "remove Lock"
xmodmap -e "keysym CapsLock = Undo Redo"

# volume keys for laptop
if [[ `hostname` == "goedel" ]] ; then
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

# start gnome-panel
if [[ -z `ps -ef | grep '[g]nome-panel'` ]] ; then
    exec gnome-panel &
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

# experimental
xcompmgr &

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
fvwm >& ~/.X-log-${disp}
mv -f ~/.X-log-${disp} ~/.X-log-${disp}-old

echo 
echo "Shutting Down X..."
echo

```

It's full of hacks and I wouldn't recommend just copying it.  Look on the [Wiki]("https://wiki.ubuntu.com/CustomXSession") for more.

---

### Post by linkunderscore on 2006-01-08
[QUOTE=shanmuha]is there any how-to on running fvwm2 in ubuntu as the desktop environment?

Thanks,
Shanmu.[/QUOTE]
```
sudo apt-get install fvwm
```

That SHOULD install fvwm and place it in your gdm login menu. Just select it on login and voila! You will have to write your own config for it, but I might be able to post my config for you if you want it.

---

### Post by jpkotta on 2006-01-09
One thing I forgot: Debian has a really slick menu system that works for many WMs and packages.  From what I understand, packages can provide a menu entry for the menu system, and WMs can provide translator scripts.  FVWM has a script and it is provided with the Ubuntu fvwm package.  All you have to do is load the generated menu file ```
Read /etc/X11/fvwm/menudefs.hook
``` and create the menu when you want it ```
Menu /Debian
``` or ```
Popup /Debian
```  The menu file is automatically updated everytime you install/remove a package, so all you have to do is re-read the file in FVWM.

---

### Post by linkunderscore on 2006-01-09
jokotta,

Thats really sweet. I didn't realize that Ubuntu(Debian) had this feature.

---

### Post by shanmuha on 2006-01-10
Thanks a lot jokotta and linkunderscore.. will test it out and let you know the results!!!

---

### Post by druvoid on 2006-05-06
What about fvwm2?  Does setting that up work the same way as fvwm?  I am new to Ubuntu, but used fvwm2 under Solaris at work a few years ago and fell in love with it then.

---

### Post by jpkotta on 2006-05-07
Do people still use fvwm1?  It looks like both versions are in the repos.  I always compile from source anyway, because I like to have the latest version of fvwm.

---

### Post by druvoid on 2006-05-07
Thanks, **jpkotta**.  After doing some more searching yesterday, I learned that in Ubuntu, fvwm is the same as fvwm2.

---

### Post by ThomasAdam on 2006-05-09
[QUOTE=linkunderscore]jokotta,

Thats really sweet. I didn't realize that Ubuntu(Debian) had this feature.[/QUOTE]

It's even supplied in the default menu that FVWM provides you, if it detects you're on Debian.

-- Thomas.

---

### Post by ThomasAdam on 2006-05-09
[QUOTE=jpkotta]Do people still use fvwm1?[/QUOTE]

Yes, I do.  Why?

-- Thomas.

---

### Post by brettr on 2006-05-09
[QUOTE=linkunderscore]I might be able to post my config for you if you want it.[/QUOTE]


Could you post it, i am currently trying to write my own, and would just like to see what a custom conf looks like. 

Also i am under the impression tha the latest fvwm version has switched the name of the config file to "config"... right?

---

### Post by jpkotta on 2006-05-10
Thomas:  
I figured that because v1 is no longer supported (and because it is very old) that almost everyone would have switched over.  But you certainly know your fvwm, and if v1 is what you want, then more power to you.  Fvwm is all about choice.

brettr:
Yes, the latest versions look at ~/.fvwm/config first, though they still look for the other files too. Tavis Ormandy has a very popular config (I've never used it, but I've seen movies of it and it looks very nice).  You can get it and screenshots at [http://dev.gentoo.org/~taviso/fvwm2rc.html](http://dev.gentoo.org/~taviso/fvwm2rc.html).

---

### Post by ThomasAdam on 2006-05-10
[QUOTE=jpkotta]Thomas:  
I figured that because v1 is no longer supported (and because it is very old) that almost everyone would have switched over.[/quote]

I still use it for posterity.  There's some interesting decor rendering differences between 1.24r and >=2.2.X that seems to adhere more to MWM.

[QUOTE=jpkotta]
brettr:
Yes, the latest versions look at ~/.fvwm/config first,[/QUOTE]

As per:

[http://www.fvwmwiki.org/Configuration/GeneralConfigGuideLines](http://www.fvwmwiki.org/Configuration/GeneralConfigGuideLines)

-- Thomas Adam

---

### Post by brettr on 2006-05-10
Okay, Awesome guys thanks.

---

