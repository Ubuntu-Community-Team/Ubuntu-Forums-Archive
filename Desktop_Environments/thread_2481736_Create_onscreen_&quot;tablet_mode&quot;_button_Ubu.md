---
title: "Create onscreen &quot;tablet mode&quot; button? Ubuntu 22.04/Gnome 42.5"
date: 2022-12-07
forum: Desktop Environments
---

### Post by tumblew33d on 2022-12-07
I'm creating this thread to address an issue that is resolved on some hardware, unresolved on others, and on which many folks have give up. Ultimately my hope is find/create a universal work-around, rather than flounder in the specifics of how a given brand of 2-in-1 laptop/tablet detects which mode the user wants. So for starters:

System: Lenovo ThinkPad Yoga 11e
OS: Ubuntu 22.04 LTS
Desktop: GNOME 42.5

The good news to start: This model, like many modern Lenovo products, comes with out-of-the-box touchscreen support on Ubuntu 18.04+.
The challenge: when folded into tablet, 1) auto-rotate screen, 2) enable on-screen keyboard, and 3) disable the onboard keyboard

Goal 1: auto-rotate screen: gnome extensions already exist to solve this. While I've previously managed extensions through gnome-tweaks, it's now easier (less buggy) to manage them through the web browser. This requires both a native host application, and a browser extension. Simply follow the links on the Gnome.org web page to install the browser extension. For the native host, GNOME advises the package
gnome-broswer-connecter. In Ubuntu 22.04, however, you will need to use the deprecated package name (regardless of which browser you plan to use)
```
sudo apt install chrome-gnome-shell
```
then reboot. Yes I know, your poor uptime stats... Next, install the "[Screen Rotate]("https://extensions.gnome.org/extension/5389/screen-rotate")" extension. I also recommend installing "[Extension List]("https://extensions.gnome.org/extension/3088/extension-list")", which creates a tray icon for enabling and disabling extensions (very convenient for a "tablet"!). You'll see why.
Goal 1 status: resolved (screen rotation works flawlessly)

Unfortunately for me, the Yoga 11e does not have a (linux-recognizable) tablet mode hardware switch. Without it, Gnome will (apparently) disable this mode by default. A lot of proverbial spilled ink (e.g. [for the same model]("https://askubuntu.com/questions/909126/detecting-tablet-mode-on-a-thinkpad-yoga-11e"), [other Lenovo models]("https://askubuntu.com/questions/1256660/yoga-laptop-autodisable-keyboard-when-screen-folded-back-to-use-as-tablet-he"), and other brands), with no clear resolution. So first up, some existing work-arounds, followed by lingering problems.

Goal 2: enable on-screen keyboard: This can be achieved through accessibility options, but sticking with gnome extensions, "[Force Show OSK]("https://extensions.gnome.org/extension/4316/force-show-osk/")". Combined with Extension List, the on-screen keyboard can be enabled at disabled at will. Automation can wait, I suppose...

Goal 3: disable built-in keyboard: This is where I hit a brick wall. I've tried a number of solutions, and none have really worked so far. Many (not all) of these attempts have come from this [Ask Ubuntu Thread]("https://askubuntu.com/questions/160945/is-there-a-way-to-disable-a-laptops-internal-keyboard").
Failed option a) [Input Device Indicator]("https://github.com/brandizzi/input-device-indicator").A utility for the system tray/top bar to toggle devices on and off. Unfortunately, the ppa seems broken, and manually installing from source code results in a whole lot of nothing happening. 

Failed option b) This [command prompt util]("https://www.youtube.com/watch?v=LvoIwqFutlg") obviously isn't ideal, and doesn't seen to work for me anyhow. 

Failed option c) this is only partly failed, so I'll go into more detail. I adapted [a bash script from this thread]("https://askubuntu.com/questions/160945/is-there-a-way-to-disable-a-laptops-internal-keyboard/713597#713597"), which oddly seems to work only conditionally for me, and not in any useful way. Nonetheless maybe it signals progress? 
First up, you need to know your keyboard input device. Unfortunately for me I'm stuck in my ways and still haven't learned proper use of Wayland, but this old X command **xinput | grep keyboard** still works fine, giving me the output: 
```
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; xwayland-keyboard:16                        id=9    [slave  keyboard (3)] 
```
From there, I adapted the bash script from the the thread and saved it as xinputKeyboard.sh:
```
#!/bin/bash

## this script is intented to create a simple GUI toggle for
## enabling/disabling the onboard keyboard input.
## adapted from https://....

Icon="/home/USER/bash/IcOnKey.png"
Icoff="/home/USER/bash/IcOffKey.png"
fconfig=".keyboard"
id=9
## for id, use the results from $xinput-list

if [ ! -f $fconfig ]; then
    echo "Creating config file"
    echo "enabled" > $fconfig
    var="enabled"
else
    read -r var< $fconfig
    echo "keyboard is : $var"
fi

if [ "$var" = "disabled" ]; then
    notify-send -i $Icon "Enabling keyboard..." \ "ON - keyboard connected";
    echo "enable keyboard..."
    xinput enable $id
    echo "enabled" > $fconfig
elif [ "$var" = "enabled" ]; then
    notify-send -i $Icoff "Disabling Keyboard" \ "OFF - Keyboard disconnected";
    echo "disable keyboard"
    xinput disable $id
    echo "disabled" > $fconfig
fi
```
Then I enabled the the script with ```
chmod +x xinputKeyboard.sh
```
To create a desktop icon, I created a file in /usr/share/applications (note the path in Ubuntu 22.04 is different than in the original thread) named keyToggle.desktop: 
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Toggle ON-OFF
Icon=/home/USER/bash/IcOnKey.png
Exec=bash xinputKeyboard.sh
Path=/home/USER/bash/
NoDisplay=false
Categories=Utility;
StartupNotify=false
Terminal=false
```
did another chmod +x  ..., copied it to my desktop, and then from the right-click-menu selected "Allow Launching"

The notifications appear as expected, however the behavior is underwhelming. It does in fact disable the key, albeit *only in Firefox* for some inexplicable reason. This means any inadvertant key presses will still transmit to any other application, to the launcher, etc.

Ideally, it would be great if the combined actions of disabling the onboard keyboard and enabling the on-screen keyboard could be triggered by any screen rotation that is not the default orientation. 
I will happily, however, settle for a toggle button (either in the launcher or system tray) that performs this switching procedure with a simple tap. 
What would be best is if the user could easier tune to their own hardware, like the way the above bash file uses the $id variable.

---

