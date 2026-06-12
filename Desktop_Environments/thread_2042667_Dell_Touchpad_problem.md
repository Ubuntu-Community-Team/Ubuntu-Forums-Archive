---
title: "Dell Touchpad problem"
date: 2012-08-15
forum: Desktop Environments
---

### Post by bd83862 on 2012-08-15
1) System > Preference > Keyboard > Layouts
     Select "Dell"  or if you know you find your dell model still better.

2) sudo vi /usr/bin/touchpad
     

#!/bin/bash
user=`whoami`
userhome=`getent passwd ${user}|awk -F: '{ print $(NF-1)  }'`

cd $userhome

function messageUser()
{
    if [ "$(which notify-send)" == "" ]; then
        echo "requires... libnotify-bin for messages..."
    elif [ "$1" == "on" ]; then
        notify-send -t 800 -i ${userhome}/myicon.png "Touchpad  enabled" "Profit :)"
    elif [ "$1" == "off" ]; then
        notify-send -t 800 -i ${userhome}/myicon.png "Touchpad disabled" "Profit :)"
    fi
}

touchPadId=$(xinput list | grep -i GlidePoint| awk '{ print $6 }' | cut -d "=" -f 2 | cut -b 1-2)
if [ "$touchPadId" == "" ]; then
    echo "Unable to identify device id..."
else
    if [ -a ".touchPadOnOff" ]; then
        rm -rfv ".touchPadOnOff"
        xinput set-prop $touchPadId 127 1
        messageUser "on"
    else
        touch ".touchPadOnOff"
        xinput set-prop $touchPadId 127 0
        messageUser "off"
    fi
fi


3) sudo chmod 755 /usr/bin/touchpad

4) System > Preference > Keyboard Shortcuts>
     Click  Add
     Name :   <Your wish>
     Command:  /usr/bin/touchpad

Actions column,  under Custom shorcut,  find  your shortcut by the name.
Click on right side.   press   "Fn"  + "F5"  key,   or your touchpad toggle key.

You will get the original notification +  the custom notification.
To remove/edit custom notification play with  messageUser function  in the script.

Profit  :)

---

