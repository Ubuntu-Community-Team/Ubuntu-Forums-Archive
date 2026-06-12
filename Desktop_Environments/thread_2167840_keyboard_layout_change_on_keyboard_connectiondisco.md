---
title: "keyboard layout change on keyboard connection/disconnection - xmodmap / udev"
date: 2013-08-15
forum: Desktop Environments
---

### Post by mongole on 2013-08-15
Hi,

As the Mac Keyboards are one of the best I want to use mine on my Dell Latitude with Ubunto 13.04. Following this [https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard) wiki entry, I managed everything to work, except the swapped ALT and CMD keys.

So i decided to investigate further and set up my own xmodmap for my mac keyboard and also my original laptop keyboard (dell latitude). I wrote to scripts to set the xmodmap configurations, everthing worked fine. But to make everything perfect, I wanted to automate the layout switch on attachment and detachment of my mac keyboard. Hence i dug into udev and wrote two rules, which executed the scripts on attachment and detachment.

After some initial problems (user which run the xmodmap command) I managed to automate it, but strange things happen. The ALT and WIN key on the laptop keyboard is swapped, but the ALT and CMD key on the mac keyboard not!

To clearify, after running attach-apple-keyboard.sh from a bash following happens:
on the laptop keyboard WIN <--> ALT and the right Alt Gr behaves like a WIN key
on the mac keyboard CMD <--> ALT on both sides of the SPACE key

after the same scripts are run be udev follwing happens:
on the laptop keyboard WIN <--> ALT and the right Alt Gr behaves like a WIN key. Same as above.
on the mac keyboard no key is swapped. this should be like above, but is not.

To verify what happened, I ran following commands to look for differences both times (on manual switch and after udev initiated switch):
xmodmap -pm
xmodmap -pk
xmodmap -pke

All of them gave the same output no matter if the switch was done manually or by udev. So the mapping is the same. It seems to be related to the different environment the script is ran in.

the udev rules:
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="05ac", ATTRS{idProduct}=="0221", ATTRS{product}=="Apple Keyboard", ACTION=="add", RUN+="/usr/bin/attached-apple-keyboard.sh"
SUBSYSTEM=="usb", ATTRS{idVendor}=="05ac", ATTRS{idProduct}=="0221", ATTRS{product}=="Apple Keyboard", ACTION=="remove", RUN+="/usr/bin/detached-apple-keyboard.sh"
```

the attach script. the xserver check prevents an error message on startup (xserver starts later then udev rules are applied). xmodmap needs to be run as a certain user, otherwise it will set the map for root, which does not help a lot in this case.
```
#!/bin/bash

xserver_count=$(ps -ef | grep /usr/bin/X | grep -v grep | wc | awk '{print $1}')
if [ $xserver_count -gt 0 ]; then
    sudo -u andi xmodmap -display :0 /etc/X11/Xmodmaps/XmodmapMac &>>/tmp/apple-keyboard-attachment.log
    echo attached apple keyboard >> /tmp/apple-keyboard-attachment.log
else
    echo X-Server not running. apple keyboard layout not possible to be set now. &>> /tmp/apple-keyboard-attachment.log
fi
```

the detach script
```
#!/bin/bash

sudo -u andi xmodmap -display :0 /etc/X11/Xmodmaps/XmodmapOrig &>>/tmp/apple-keyboard-attachment.log
echo detached apple keyboard >> /tmp/apple-keyboard-attachment.log
```

the laptop keyboard xmodmap config
```
clear mod1clear mod4
clear mod5
keycode 133 = Super_L NoSymbol Super_L
keycode  64 = Alt_L Meta_L Alt_L Meta_L
keycode 108 = ISO_Level3_Shift NoSymbol ISO_Level3_Shift
keycode 134 = Super_R NoSymbol Super_R
add mod1 = Alt_L Meta_L
add mod4 = Super_L Super_R Super_L Hyper_L
add mod5 = ISO_Level3_Shift Mode_switch

```

the mac keyboard xmodmap config
```
clear mod1clear mod4
clear mod5
keycode  64 = Super_L NoSymbol Super_L
keycode 133 = Alt_L Meta_L Alt_L Meta_L
keycode 134 = ISO_Level3_Shift NoSymbol ISO_Level3_Shift
keycode 108 = Super_R NoSymbol Super_R
add mod1 = Alt_L Meta_L
add mod4 = Super_L Super_R Super_L Hyper_L
add mod5 = ISO_Level3_Shift Mode_switch
```

It's interesting, that the attach script is called three times. I guess, it's happening, because of the keyboard is shown twice when I check with xinput and the keyboard also has a USB hub included. To verify a problem from this side, I called the script three times from the command line, but this did not cause a problem.

Anybody any idea, what could be the reason for this behavior?

---

### Post by mongole on 2013-09-07
nobody any idea?

---

