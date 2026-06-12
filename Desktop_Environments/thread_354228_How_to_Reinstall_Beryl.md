---
title: "How to Reinstall Beryl"
date: 2007-02-05
forum: Desktop Environments
---

### Post by shareMenaPeace on 2007-02-05
Well i played around with the settings and somehow i switched the video renderer from main menu (yeah really bad idea). 
[COLOR="Magenta"]Note this small how to focus on reinstall - therfor you have the beryl deb sources in your sources.list allready and your /etc/X11/xorg.conf ist configured for beryl allready -- otherwise see the Guides on how to install beryl.[/COLOR]

**Beryl Fresh Install Guides**
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Check this guide about your repositorys
[http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/)


[B][SIZE="6"]
Howto Remove Beryl[/SIZE][/B]
Some parts taken from here (manual way).
[http://ubuntuforums.org/showthread.php?t=353813&highlight=uninstall+beryl](http://ubuntuforums.org/showthread.php?t=353813&highlight=uninstall+beryl)
If you cant login with your user account boot in recovery mode and than run 

```
startx
``` from console to launch gnome as root.

Once ubuntu loads open up a terminal and type 

```
synaptic
``` to start the Synaptic Package Manager

Search than for "beryl" and mark all beryl stuff for removal choose "apply" to start removal of beryl --  choose "complete removal". 
So now logout - back to the console and reboot with

```
shutdown -r now
```

Boot normal and login with your user account. As there are still parts of beryl somewhere in the system you need to do this aswell. (Or after new install beryl hangs again with the old settings).


To remove all beryl settings do this from terminal.
To backup browse to "~/.beryl" and copy profiles and the setting file - later afer reinstall copy them back.
```

rm -r ~/.beryl
rm -r ~/.emerald
rm -r ~/.beryl-managerrc
```


Note: It might be not nessassary to remove all settings - but to keep settings export your beryl profiles.

[B][SIZE="6"]
Howto Reinstall Beryl[/SIZE][/B]
Now you are good to reinstall beryl again with
```
sudo aptitude install beryl emerald-themes
```


**What changed or not working:**
You need to reload beryl manager window to let setting changes become updated.
Or use the general profile (save and activate).

**Recommended Beryl Settings**
Create under "General Options" -> "Settings and Profiles" new profiles, just incase settings get messy.

Desktop -> Rotate Cube -> Behavior -> max. "Zoom"
Desktop -> Desktop Cube -> Caps - add here your own *.png images and choose "scale".
Desktop -> Desktop Cube -> Skydome - add here a overall backgrround wallpaper *.png and animate it.
Desktop -> Desktop Cube -> Trancparency "enable"

Visual Effects -> 3D Effects -> enable "3D Effects" and window depth.
Visual Effects -> 3D Effects -> enable "Blur Effects" 

Extras enable "Screenshot"

Eyecandy
Extras enable water effects. (ALT and WINDOWS KEY)
Extras enable "Splash"

[B]
Recommended Emerald Theme Manager Settings[/B]
Choose a nice window theme.

**Default Beryl ShortCuts**
Note: this can customized set in the general options panel in beryl settings manager.

Window Switcher
Move mouse right corner of Desktop to slide active windows "window switcher - preview mode"

Cube Mode
The default is "middle" mouse button click and hold to zoom out....(click on desktop)

Constant Cube Mode (click on desktop)
ALT + STRG and click middle mouse button.

Plain View
ALT + STRG "page down key" - diffrent view. Here you can use left+rigth KEY to scroll.

Window Slider "centre"
ALT + STRG + TAB access window slider

Move Cube View
ALT + STRG + right, left, up and down - KEY move cube.



If someone has some tips regarding reinstall or things which can be done better please post here, thanks.

Cheers

---

