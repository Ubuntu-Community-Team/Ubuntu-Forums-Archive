---
title: "launcher + windows menu"
date: 2018-04-06
forum: Desktop Environments
---

### Post by aster94 on 2018-04-06
hello

i used ubuntu for two years but now i moved to xubuntu since my hardware is getting old

in the panel i have some launchers, i would like that them had the "memory" if that application is opened
for example see the first 30 seconds of this video in gnome
[https://www.youtube.com/watch?v=jYi3GKAQ5Pc](https://www.youtube.com/watch?v=jYi3GKAQ5Pc)
when he click on the launcher of an application the laucher change background and if he click again on it the old windows will be opened
in xubuntu if i click on a launcher i get a new windows but i can't open old windows
example of what happen now (two google chrome):
[https://image.ibb.co/c1S1Mc/Untitled.png](https://image.ibb.co/c1S1Mc/Untitled.png)

is there a way to do it?

---

### Post by kerry_s on 2018-04-06
are you asking for a dock?

sudo apt install plank

plank --preferences && plank &

---

### Post by vanadium on 2018-04-07
You are looking for a "launch or switch to" approach where clicking an item switches to the application if it is already running, or opens the application if it is not already running. The xfce slingshot menu and shortcut launchers currently are "always launch". The actual effect of the launch, however, depends on the application. Gimp, for example, will switch to the already running instance when launched again. Inkscape not. Firefox will switch to a running instance and open a new tab there. Some applications provide command line options to control such aspects while launching the executable. 

You can indeed install a dock which implements that. However, that is a different interface, and usually only mouse supported. You may prefer the native environment of xfce.

I recently ran into a tool "jumpapp": [https://github.com/mkropat/jumpapp](https://github.com/mkropat/jumpapp). It can be used to make any application you want "launch and switch to" aware. One way is to edit the .desktop files of the applications you want to acquire that behaviour, which is what launchers and slingshot or other menu systems in xfce are using.

The neatest way is to just copy these .desktop files you want to change to your private .local/share/applications folder. Open the file in a text editor, look for the "Exec=" line. Insert "jumpapp" before the current command. Your desktop environment will now use your private modified .desktop file instead of the system wide version.

---

### Post by aster94 on 2018-04-08
> **vanadium said:**
> You are looking for a "launch or switch to" approach where clicking an item switches to the application if it is already running, or opens the application if it is not already running. The xfce slingshot menu and shortcut launchers currently are "always launch". The actual effect of the launch, however, depends on the application. Gimp, for example, will switch to the already running instance when launched again. Inkscape not. Firefox will switch to a running instance and open a new tab there. Some applications provide command line options to control such aspects while launching the executable. 

You can indeed install a dock which implements that. However, that is a different interface, and usually only mouse supported. You may prefer the native environment of xfce.

I recently ran into a tool "jumpapp": [https://github.com/mkropat/jumpapp](https://github.com/mkropat/jumpapp). It can be used to make any application you want "launch and switch to" aware. One way is to edit the .desktop files of the applications you want to acquire that behaviour, which is what launchers and slingshot or other menu systems in xfce are using.

The neatest way is to just copy these .desktop files you want to change to your private .local/share/applications folder. Open the file in a text editor, look for the "Exec=" line. Insert "jumpapp" before the current command. Your desktop environment will now use your private modified .desktop file instead of the system wide version.

yeeeesss that is exactly what i was looking for, i wasn't unable to explain, i  just moved from gnome to xfce and i already changed the windows manager, i wouldn't like to change also the docker or i would have staid with another desktop environment :D

did you managed to have it working for every lauchers? i am not able to make it working for the file manager and a few others like chrome

---

### Post by vanadium on 2018-04-09
For chrome it should work with "jumpapp -i chrome -p  /usr/bin/google-chrome-stable %U" in the desktop file. google-chrome-stable is a bash script that in the end launches the chrome executable. The -i option indicates to jumpapp to look for the proces chrome, not google-chrome-stable. The -p option is there to have the browser itself take over its window management when we pass an argument. With this option, jumpapp will immediately call the executable if an argument, i.e., an URL, is passed, and not look for an existing proces first. If no argument is passed, jumpapp will first look if there is a window to switch to, and only launch the command if that is not the case.

Some tweaking may also be needed with your file manager. "man jumpapp" gives you the options jumpapp knows. With xprop, you can identify properties of a running window, and process names are visible in the output of "top" or "ps aux".

---

### Post by again? on 2018-04-09
jumpapp looks interesting. Seems to implement wmctrl commands to bring into focus if it finds a window or launch if not found.
eg
```
wmctrl -xa Google-chrome || /usr/bin/google-chrome-stable
```

I found plank to be the simplest solution in Xfce, with the benefit of being able to access unity quicklist menus with right mouse click.
You can also use dockbarx with xfce4-panel as outined in this [**youtube video**]("https://www.youtube.com/watch?v=tJQ0y2XMoMw&index=5&list=PLSmXPSsgkZLt4F4tFSreGqtoFSMUpGo2Q").

---

### Post by aster94 on 2018-04-11
yes plank seems to be a good solution, especially for the quicklist
the only feature i am unable to find in any dock is the ability to show all the opened application in the dock like in windows machines or gnome. do you know any?

---

### Post by again? on 2018-04-11
> **aster94 said:**
> yes plank seems to be a good solution, especially for the quicklist
the only feature i am unable to find in any dock is the ability to show all the opened application in the dock like in windows machines or gnome. do you know any?
If you mean to show unpinned windows on the dock, you can change in Plank preferences. 
ctrl+rightmouse on plank dock.

---

### Post by kerry_s on 2018-04-11
> **aster94 said:**
> yes plank seems to be a good solution, especially for the quicklist
the only feature i am unable to find in any dock is the ability to show all the opened application in the dock like in windows machines or gnome. do you know any?

are you talking about the expose feature? super key in gnome.

in xfce most people use skippy-xd

sudo apt install skippy-xd

then just bind it to a keyboard shortcut or create a launcher. the command is: skippy-xd

also if your trying to get xfce to be like gnome, you can go with xfdashboard to get that gnome look.
[http://goodies.xfce.org/projects/applications/xfdashboard/start](http://goodies.xfce.org/projects/applications/xfdashboard/start)

sudo apt install xfdashboard


i only use skippy on my solus budgie install, had to build from source. haven't tried building xfdashboard maybe 1 day when i'm bored. :)

---

### Post by again? on 2018-04-11
Skippy-xd isn't available in the repos.
I compiled from [https://github.com/richardgv/skippy-xd](https://github.com/richardgv/skippy-xd).
I used checkinstall to create a deb file that should install in Xubuntu 17.10.

---

### Post by kerry_s on 2018-04-11
> **guber2 said:**
> Skippy-xd isn't available in the repos.
I compiled from [https://github.com/richardgv/skippy-xd](https://github.com/richardgv/skippy-xd).
I used checkinstall to create a deb file that should install in Xubuntu 17.10.

does yours have the close button? i notice in mine there's no close button like there is in gnome. but it's been a few years since i used skippy & i don't remember if it even had that feature.
also i'm on solus budgie, don't know if that would make a difference.
my favorite distro is elementary os, but i wanted a rolling release, so i'm just coping the general look & feel of eos.
[ATTACH=CONFIG]279254[/ATTACH][ATTACH=CONFIG]279255[/ATTACH]

---

### Post by again? on 2018-04-11
I have always used unity so have never used skippy before.
Recently moved to xfce4 after giving gnome-shell a good run and not liking it.
Decided to try skippy after reading your post.

The scaled windows don't show a close button.
Left mouse......select  
Right mouse.....iconify
Middle mouse..... close

Can you make minimised windows draw fully or do they only show as icons?

---

### Post by kerry_s on 2018-04-11
minimized windows show normal, i don't get icons, always thumb nail.

> Middle mouse..... close


good to know, i usually use mostly moving from app to app, but sometimes id like to close several apps with out having to leave overview. thanks

right mouse does nothing on mine.

---

### Post by again? on 2018-04-11
The version I have installs a config to /etc/xdg/skippy-xd.rc
```
# **Copy this to ~/.config/skippy-xd/skippy-xd.rc and edit it to your liking**
#
# Notes:
#
# - colors can be anything XAllocNamedColor can handle
#   (like "black" or "#000000")
#
# - distance is a relative number, and is scaled according to the scale
#   factor applied to windows
#
# - fonts are Xft font descriptions
#
# - booleans are "true" or anything but "true" (-> false)
#
# - opacity is an integer in the range of 0-255
#
# - brighness is a floating point number (with 0.0 as neutral)
#
# - if the update frequency is a negative value, the mini-windows will only
#   be updated when they're explicitly rendered (like, when they gain or
#   lose focus).
#
# - the 'shadowText' option can be a color or 'none', in which case the
#   drop-shadow effect is disabled
#
# - Picture specification:
#   [WIDTHxHEIGHT] [orig|scale|scalek|tile] [left|mid|right] [left|mid|right]
#   [COLOR|#FFFFFFFF] [PATH]
#
#   Examples:
#   background = 500x400 tile right mid #FF0000 /home/richard/screenshots/256.png
#   background = orig mid mid #FF000080
#
# - Bindings in [bindings] section can bind to "no" (do nothing), "focus"
#   (focus to window), "iconify", "shade-ewmh" (toggle window shade state),
#   "close-icccm" (close window with ICCCM method), "close-ewmh" (close
#   window with EWMH method), or "destroy" (forcefully destroy the window).
#

[general]
distance = 50
useNetWMFullscreen = true
ignoreSkipTaskbar = true
updateFreq = 10.0
lazyTrans = false
pipePath = /tmp/skippy-xd-fifo
movePointerOnStart = true
movePointerOnSelect = true
movePointerOnRaise = true
switchDesktopOnActivate = false
useNameWindowPixmap = false
forceNameWindowPixmap = false
includeFrame = true
allowUpscale = true
showAllDesktops = false
showUnmapped = true
preferredIconSize = 48
clientDisplayModes = thumbnail icon filled none
iconFillSpec = orig mid mid #00FFFF
fillSpec = orig mid mid #FFFFFF
background =

[xinerama]
showAll = true

[normal]
tint = black
tintOpacity = 0
opacity = 200

[highlight]
tint = #101020
tintOpacity = 64
opacity = 255

[tooltip]
show = true
followsMouse = true
offsetX = 20
offsetY = 20
align = left
border = #ffffff
background = #404040
opacity = 128
text = #ffffff
textShadow = black
font = fixed-11:weight=bold

[bindings]
miwMouse1 = focus
miwMouse2 = close-ewmh
miwMouse3 = iconify
```

---

### Post by kerry_s on 2018-04-11
mine same as yours:
```
# Copy this to ~/.config/skippy-xd/skippy-xd.rc and edit it to your liking
#
# Notes:
#
# - colors can be anything XAllocNamedColor can handle
#   (like "black" or "#000000")
#
# - distance is a relative number, and is scaled according to the scale
#   factor applied to windows
#
# - fonts are Xft font descriptions
#
# - booleans are "true" or anything but "true" (-> false)
#
# - opacity is an integer in the range of 0-255
#
# - brighness is a floating point number (with 0.0 as neutral)
#
# - if the update frequency is a negative value, the mini-windows will only
#   be updated when they're explicitly rendered (like, when they gain or
#   lose focus).
#
# - the 'shadowText' option can be a color or 'none', in which case the
#   drop-shadow effect is disabled
#
# - Picture specification:
#   [WIDTHxHEIGHT] [orig|scale|scalek|tile] [left|mid|right] [left|mid|right]
#   [COLOR|#FFFFFFFF] [PATH]
#
#   Examples:
#   background = 500x400 tile right mid #FF0000 /home/richard/screenshots/256.png
#   background = orig mid mid #FF000080
#
# - Bindings in [bindings] section can bind to "no" (do nothing), "focus"
#   (focus to window), "iconify", "shade-ewmh" (toggle window shade state),
#   "close-icccm" (close window with ICCCM method), "close-ewmh" (close
#   window with EWMH method), or "destroy" (forcefully destroy the window).
#

[general]
distance = 50
useNetWMFullscreen = true
ignoreSkipTaskbar = true
updateFreq = 10.0
lazyTrans = false
pipePath = /tmp/skippy-xd-fifo
movePointerOnStart = true
movePointerOnSelect = true
movePointerOnRaise = true
switchDesktopOnActivate = false
useNameWindowPixmap = false
forceNameWindowPixmap = false
includeFrame = true
allowUpscale = true
showAllDesktops = false
showUnmapped = true
preferredIconSize = 48
clientDisplayModes = thumbnail icon filled none
iconFillSpec = orig mid mid #00FFFF
fillSpec = orig mid mid #FFFFFF
background =

[xinerama]
showAll = true

[normal]
tint = black
tintOpacity = 0
opacity = 200

[highlight]
tint = #101020
tintOpacity = 64
opacity = 255

[tooltip]
show = true
followsMouse = true
offsetX = 20
offsetY = 20
align = left
border = #ffffff
background = #404040
opacity = 128
text = #ffffff
textShadow = black
font = fixed-11:weight=bold

[bindings]
miwMouse1 = focus
miwMouse2 = close-ewmh
miwMouse3 = iconify
```

also i'm using mine in daemon mode:
startup: skippy-xd --start-daemon
command: skippy-xd --toggle-window-picker

i didn't want no lag when using keyboard or shortcut.
```
[Desktop Entry]
Type=Application
Name=Expose
Comment=Show all windows
Icon=multitasking-view
Exec=skippy-xd --toggle-window-picker
Categories=GTK;GNOME;Other;

```

---

### Post by logix2 on 2018-04-12
You can also give [Xfdashboard]("https://github.com/gmc-holle/xfdashboard") a try. It's available in the official repositories. It's like a Gnome Shell dashboard of open windows for Xfce. More about it [here]("http://goodies.xfce.org/projects/applications/xfdashboard/start").

---

### Post by again? on 2018-04-12
> **kerry_s said:**
> mine same as yours:


also i'm using mine in daemon mode:
startup: skippy-xd --start-daemon
command: skippy-xd --toggle-window-picker

i didn't want no lag when using keyboard or shortcut.

I just set "skippy-xd" to an easystroke gesture.
Haven't experienced any lag.

This python script for hot corners I lifted from bunsenlabs might interest you.

_bl-hotcorners_
```
#!/usr/bin/env python2.7
#
#    bl-hotcorners: a script for adding hot corners to Openbox.
#    Copyright (C) 2012 Philip Newborough   <corenominal@corenominal.org>
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
#    Renamed for BunsenLabs
#	 sudo apt update && sudo apt install python-xlib wmctrl xdotool
# 	 create config directory... mkdir ~/.config/bl-hotcorners
#	 After first run edit ~/.config/bl-hotcorners for custom commands.


from Xlib import display
from Xlib.ext.xtest import fake_input
from Xlib import X
from subprocess import Popen, PIPE, STDOUT
import sys, time, os, ConfigParser, re
import argparse

check_intervall = 0.2

ap = argparse.ArgumentParser(description="Hotcorners")
ap.add_argument("-k", "--kill", help="attempt to kill any runnng instances",
            action="store_true")
ap.add_argument("-d", "--daemon", help="run daemon and listen for cursor triggers",
            action="store_true")
opts = ap.parse_args(sys.argv[1:])

p = Popen(['xdotool','getdisplaygeometry'], stdout=PIPE, stderr=STDOUT)
Dimensions = p.communicate()
Dimensions = Dimensions[0].replace('\n', '')
Dimensions = Dimensions.split(' ')
width = int(Dimensions[0])
height = int(Dimensions[1]bl-hotcorners
rt = width - 1
bt = height - 1

if opts.kill:
    print "Attempting to kill any running instances..."
    os.system('pkill -9 -f bl-hotcorners')
    exit()

elif opts.daemon:
    Config = ConfigParser.ConfigParser()
    cfgdir = os.getenv("HOME")+"/.config/bl-hotcorners"
    rcfile = cfgdir+"/bl-hotcornersrc"
    bounce = 15
    disp = display.Display()
    root=display.Display().screen().root

    def mousepos():
        data = root.query_pointer()._data
        return data["root_x"], data["root_y"], data["mask"]

    def mousemove(x, y):
        fake_input(disp, X.MotionNotify, x=x, y=y)
        disp.sync()

    try:
        cfgfile = open(rcfile)
    except IOError as e:
        if not os.path.exists(cfgdir):
            os.makedirs(cfgdir)
        cfgfile = open(rcfile,'w')
        Config.add_section('Hot Corners')
        Config.set('Hot Corners','top_left_corner_command', 'xdotool key Super+d')
        Config.set('Hot Corners','top_right_corner_command', '')
        Config.set('Hot Corners','bottom_left_corner_command', '')
        Config.set('Hot Corners','bottom_right_corner_command', '')
        Config.write(cfgfile)
        cfgfile.close()

    while True:
        Config.read(rcfile)
        time.sleep(check_intervall)
        pos = mousepos()

        if pos[0] == 0 and pos[1] == 0:
            if Config.get('Hot Corners','top_left_corner_command') != '':
                time.sleep(0.2)
                pos = mousepos()
                if pos[0] == 0 and pos[1] == 0:
                    mousemove(pos[0] + bounce, pos[1] + bounce)
                    os.system('(' + Config.get('Hot Corners','top_left_corner_command') + ') &')
                    mousemove(pos[0] + bounce, pos[1] + bounce)
                    time.sleep(2)

        elif pos[0] == rt and pos[1] == 0:
            if Config.get('Hot Corners','top_right_corner_command') != '':
                time.sleep(0.2)
                pos = mousepos()
                if pos[0] == rt and pos[1] == 0 :
                    mousemove(pos[0] - bounce, pos[1] + bounce)
                    os.system('(' + Config.get('Hot Corners','top_right_corner_command') + ') &')
                    mousemove(pos[0] - bounce, pos[1] + bounce)
                    time.sleep(2)

        elif pos[0] == 0 and pos[1] == bt:
            if Config.get('Hot Corners','bottom_left_corner_command') != '':
                time.sleep(0.2)
                pos = mousepos()
                if pos[0] == 0 and pos[1] == bt:
                    mousemove(pos[0] + bounce, pos[1] - bounce)
                    os.system('(' + Config.get('Hot Corners','bottom_left_corner_command') + ') &')
                    mousemove(pos[0] + bounce, pos[1] - bounce)
                    time.sleep(2)

        elif pos[0] == rt and pos[1] == bt:
            if Config.get('Hot Corners','bottom_right_corner_command') != '':
                time.sleep(0.2)
                pos = mousepos()
                if pos[0] == rt and pos[1] == bt:
                    mousemove(pos[0] - bounce, pos[1] - bounce)
                    os.system('(' + Config.get('Hot Corners','bottom_right_corner_command') + ') &')
                    mousemove(pos[0] - bounce, pos[1] - bounce)
                    time.sleep(2)
```

```
sudo apt install python-xlib wmctrl xdotool
```
Create config directory.
```
mkdir ~/.config/bl-hotcorners
```

Run to create a config
```
bl-hotcorners -d
```

Then to customise, edit 
```
~/.config/bl-hotcorners/bl-hotcornersrc
```
eg 
```
[Hot Corners]
top_left_corner_command = skippy-xd
top_right_corner_command = xfce4-terminal --drop-down
bottom_left_corner_command = xdotool key Super+d
bottom_right_corner_command = 
```

Add **bl-hotcorners -d** to startups.

---

### Post by aster94 on 2018-04-13
skippy-xd and xfdashboard are very interesting, right now i am using xfdashboard with an hotcorner (built in plug in) which launch it but i guess that skippy is more lightweight, maybe in the future i will replace xfdashboard with skippy-xd

by the way if someone is interested xfdashboard does have the close button

i still doesn't tried plank but i will do

anyway does someone know how i could add the whisker menu search (in red) to the panel? right now there is the verve command line (in blue)

[IMG]https://ibb.co/h7f8E7[/IMG][IMG]https://image.ibb.co/kFEX7S/Untitled.png[/IMG]


does anyone have tried a xfce theme manager? there is this [one]("http://www.webupd8.org/2013/06/xfce-theme-manager-single-gui-to-change.html") but the ppa doesn't work anymore and i wouldn't like to compile it from source

about the night mode? does have someone tried some pachages that let you change the saturation, brightness and colors of the screen?

---

### Post by again? on 2018-04-13
The yaketty deb from the xfce-theme-manager ppa installs in 17.10 but doesn't work properly with latest themes.
Your better off just using installed tools.

For my eyes I use redshift-gtk. See here ----> [https://ubuntuforums.org/showthread.php?t=2330459&p=13516421#post13516421](https://ubuntuforums.org/showthread.php?t=2330459&p=13516421#post13516421)
Using a dark theme helps the eyes as well.

arc-theme is in the artful repos.
[ATTACH=CONFIG]279283[/ATTACH]

adapta-theme ppa --->[https://launchpad.net/~tista/+archive/ubuntu/adapta](https://launchpad.net/~tista/+archive/ubuntu/adapta) (I use this one)
[ATTACH=CONFIG]279282[/ATTACH]

---

### Post by aster94 on 2018-04-16
> **guber2 said:**
> If you mean to show unpinned windows on the dock, you can change in Plank preferences. 
ctrl+rightmouse on plank dock.

at the end i moved to plank, i should have done it before, it is perfect :lolflag:

i also purged xfdashboard since really i don't need to work with many workspace, usually i prefer to work on a project at a time. Maybe i will install skippy, but i m not sure which is the difference with skippy-xd maybe one is newer/deprecated/better?

[COLOR=#000000]redshift is working perfeclty, i would love something more customizable, sometimes i do astrophotography and maybe i would need to do something [like this]("https://ubuntuforums.org/showthread.php?t=1080867")[/COLOR]

i am still unable to find a way to just type in the screen and search for installed application, i would like to avoid to click on the whisker menu

---

### Post by again? on 2018-04-16
I use kupfer.
On the surface a simple launcher but lot's more if you look deeper.
[https://www.youtube.com/watch?v=TG4L-hLsoCk](https://www.youtube.com/watch?v=TG4L-hLsoCk)

For screen colors it depends on gfx/drivers.
I have nvidia gfx which I can customise rgb colour with nvidia-settings.
Redshift allows some customization in the config.
eg for late night I use
```
gamma-night=0.3:1.0:0.3
```
which corresponds to r:g:b values. (0.0 - 1.0)
Just have to restart redshift if you edit the config.
Wouldn't be too hard to set up a script to load different configs.

Also look at the xgamma command.
eg
```
xgamma -bgamma 0.2
```
```
xgamma --help
man xgamma
```

---

### Post by aster94 on 2018-04-17
> **guber2 said:**
> I use kupfer.
On the surface a simple launcher but lot's more if you look deeper.
[https://www.youtube.com/watch?v=TG4L-hLsoCk](https://www.youtube.com/watch?v=TG4L-hLsoCk)

For screen colors it depends on gfx/drivers.
I have nvidia gfx which I can customise rgb colour with nvidia-settings.
Redshift allows some customization in the config.
eg for late night I use
```
gamma-night=0.3:1.0:0.3
```
which corresponds to r:g:b values. (0.0 - 1.0)
Just have to restart redshift if you edit the config.
Wouldn't be too hard to set up a script to load different configs.

Also look at the xgamma command.
eg
```
xgamma -bgamma 0.2
```
```
xgamma --help
man xgamma
```

guber, i really have to say a big thank you to you, i am loving xfce thanks to you :D

xgamma was what i was looking for, but in the help it said that it is better to use xrandr, so i make an alias in .bashrc
```
alias nightMode='xrandr --output LVDS-1 --brightness 0.6 --gamma 3:0.3:0.3'
``` 
and another one to come back to normal

i installed kupfer and it is almost what i was looking for, to start it i need to press a shortcut, i would rather to just type the name of the application but it is ok even this way

about skippy-xd, i read that it used to crash often, now it looks like that [there is a ppa]("https://github.com/richardgv/skippy-xd") so the upgrade to new version should be easier, really the ppa is broken, but the github page is active and I opened an issue so hopefully would be fixed soon

---

### Post by again? on 2018-04-17
```

```Glad to help.
Yeah, I have never really used xgamma but noticed the man page recommended xrandr.
Also tried xfdashboard but doesn't really suit my needs.
I compiled skippy and have had no problems.
That ppa hasn't been updated for a couple of years.

I've only just recently made xfce my default desktop after dabbling with it in the past.
I liked Unity but don't like the switch to gnome-shell.
Too resource hungry and the extensions I use keep breaking with gnome updates.
Satisfied with the setup at the moment.
Plank on the left like unity, tint2 panel and kupfer.

P.S. If you are not aware xfce4-terminal has a Quake style console function.
```
xfce4-terminal --drop-down
```

Here's a nightmode toggle script for you.
_nightmode-toggle.sh_
```
#!/bin/bash

STATUS=$(xrandr --verbose | awk '/Gamma/{print $2}')

if [ "$STATUS" == "1.0:1.0:1.0" ]
	then
		xrandr --output LVDS-1 --brightness 0.6 --gamma 3:0.3:0.3
                notify-send -i info "Nightmode Activated"
	else
		xrandr --output LVDS-1 --brightness 1 --gamma 1:1:1
fi
exit 0
```

Make executable and bind to keyboard shortcut to toggle between normal and nightmode.

---

### Post by aster94 on 2018-04-17
every time i come back in this thead i discover something new, i really liked the drop terminal, it is similar to yakuake in kde, i added it to the autostart application ;)

thank you very much for the script i am using linux only since two years and i didn't deep into the bash scripting yet! :D it would be very useful!

---

