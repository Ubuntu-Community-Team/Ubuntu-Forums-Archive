---
title: "ddcutil &amp; Gnome shell extension Argos to change color temp &amp; brightness monitors"
date: 2017-06-01
forum: Desktop Environments
---

### Post by RobertFM on 2017-06-01
Hi, 

Just want to share how I use ddcutil and the Gnome Shell extension Argos to (automatically) change the actual monitor brightness (and temperature) of my 2 dell monitors.
It is probably very specific, but maybe it is of use to somebody. I am using a Nvidia graphics card and 2 dell P2416D monitors. I always liked the easy brightness control of my laptop and wanted something similar on my desktop pc.

First install ddcutil
```
sudo apt install ddcutil
```

Then I added my username to the groupe "i2c"

ddccontrol was still not working but thanks to google and John Doe (I'll try and find your name) I found the solution. I created the file:
> /usr/share/X11/xorg.conf.d/70-ddccontrol.conf
with the following code:

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    Option         "RegistryDwords" "RMUseSwI2c=0x01; RMI2cSpeed=100"
 EndSection
```

Reboot

Now in the terminal run  ```
ddcutil detect
```

and see if you can find your monitors

Now check the feature nr for brightness (in my case 10) Video gain: blue (1A in my case) and Video gain: green (18 for me) and Select color preset (14 for me) for all your monitors
```
ddcutil -d "your monitor nr" capabilities

```

Now get your green and blue day levels by running
```
ddcutil -d "monitor nr" getvcp 14

```

My result was:
VCP code 0x14 (Select color preset           ): 6500 K (sl=0x05)
sl=0x05 was preset nr 5

so running the following command set my color temp for day time use:
```
ddcutil -d 1 setvcp 14 5

```

Install Argos (love this extension!)
[https://extensions.gnome.org/extension/1176/argos/](https://extensions.gnome.org/extension/1176/argos/)

Now for the scripts for manual control via Argos:

(make sure you change everything to your own situation, eg monitor nr etc.)

I creates a script to control the brightness in ~/bin/monitors.sh with the following code:
```
#!/bin/bash
BRIGHTNESS=$1
COLOR=$2
EVENING_LEVEL=70
NIGHT_LEVEL=60


#BRIGHTNESS
ddcutil -d 1 setvcp 10 $BRIGHTNESS
ddcutil -d 2 setvcp 10 $BRIGHTNESS


#COLOR TEMPERATURE
if [ $COLOR = "day" ]; then
    ddcutil -d 1 setvcp 14 5
    ddcutil -d 2 setvcp 14 5
elif [ $COLOR = "evening" ]; then
    ddcutil -d 1 setvcp 18 $EVENING_LEVEL
    ddcutil -d 2 setvcp 18 $EVENING_LEVEL
    ddcutil -d 1 setvcp 1A $EVENING_LEVEL
    ddcutil -d 2 setvcp 1A $EVENING_LEVEL
elif [ $COLOR = "night" ]; then
    ddcutil -d 1 setvcp 18 $NIGHT_LEVEL
    ddcutil -d 2 setvcp 18 $NIGHT_LEVEL
    ddcutil -d 1 setvcp 1A $NIGHT_LEVEL
    ddcutil -d 2 setvcp 1A $NIGHT_LEVEL
fi


#CHECK BRIGHTNESS


D1_BRIGHTNESS=$(ddcutil -d 1 getvcp 10 | awk '{ print $9}')
D2_BRIGHTNESS=$(ddcutil -d 2 getvcp 10 | awk '{ print $9}')


if [ $BRIGHTNESS = ${D1_BRIGHTNESS%?} ]
then
  echo BRIGHTNESS D1 OK
else
  ddcutil -d 1 setvcp 10 $BRIGHTNESS
  echo BRIGHTNESS D1 SET
fi
if [ $BRIGHTNESS = ${D2_BRIGHTNESS%?} ]
then
  echo BRIGHTNESS D2 OK
else
  ddcutil -d 2 setvcp 10 $BRIGHTNESS
  echo BRIGHTNESS D2 SET
fi


#CHECK COLOR TEMPERATURE


if [[ -n "$COLOR" ]]; then
  D1_COLORPRESET=$(ddcutil -d 1 getvcp 14 | awk '{ print $8}')
  D2_COLORPRESET=$(ddcutil -d 2 getvcp 14 | awk '{ print $8}')
  if [ $COLOR = "day" ]; then
    if [ $D1_COLORPRESET = "6500" ] && [ $D2_COLORPRESET = "6500" ] ; then
      echo COLOR PRESET OK
    else
      ddcutil -d 1 setvcp 14 5
      ddcutil -d 2 setvcp 14 5
      echo COLOR PRESET SET
    fi
  elif [ $COLOR = "evening" ] || [ $COLOR = "night" ]; then
    D1_GREEN=$(ddcutil -d 1 getvcp 18 | awk '{ print $11}')
    D2_GREEN=$(ddcutil -d 2 getvcp 18 | awk '{ print $11}')
    D1_BLUE=$(ddcutil -d 1 getvcp 1A | awk '{ print $11}')
    D2_BLUE=$(ddcutil -d 2 getvcp 1A | awk '{ print $11}')
    if [[ $COLOR = "evening" ]]; then
      if [ $D1_COLORPRESET = "User" ] && [ $D2_COLORPRESET = "User" ] && [ $EVENING_LEVEL = ${D1_GREEN%?} ] && [ $EVENING_LEVEL = ${D2_GREEN%?} ] && [ $EVENING_LEVEL = ${D1_BLUE%?} ] && [ $EVENING_LEVEL = ${D2_BLUE%?} ]; then
        echo COLOR LEVELS OK
        else
          ddcutil -d 1 setvcp 18 $EVENING_LEVEL
          ddcutil -d 2 setvcp 18 $EVENING_LEVEL
          ddcutil -d 1 setvcp 1A $EVENING_LEVEL
          ddcutil -d 2 setvcp 1A $EVENING_LEVEL
        echo COLOR LEVELS SET
      fi
    fi
    if [[ $COLOR = "night" ]]; then
      if [ $D1_COLORPRESET = "User" ] && [ $D2_COLORPRESET = "User" ] && [ $NIGHT_LEVEL = ${D1_GREEN%?} ] && [ $NIGHT_LEVEL = ${D2_GREEN%?} ] && [ $NIGHT_LEVEL = ${D1_BLUE%?} ] && [ $NIGHT_LEVEL = ${D2_BLUE%?} ]; then
        echo COLOR LEVELS OK
        else
          ddcutil -d 1 setvcp 18 $NIGHT_LEVEL
          ddcutil -d 2 setvcp 18 $NIGHT_LEVEL
          ddcutil -d 1 setvcp 1A $NIGHT_LEVEL
          ddcutil -d 2 setvcp 1A $NIGHT_LEVEL
        echo COLOR LEVELS SET
      fi
    fi
  else
    echo "what?"
  fi
fi
exit

```

now when running this script you can specify the brightness and color temp like so (for example 10% brightness at night):
```
~/bin/monitors.sh 10 night

```
Create the script ~/.config/argos/Brightness.sh with the following code:
#!/usr/bin/env bash
BRIGHTNESS=$(ddcutil -d 1 getvcp 10 | awk '{ print substr($9, 1, length($9) - 1)}')

```

#!/usr/bin/env bash


echo "Brightness $BRIGHTNESS"%" |iconName=display-brightness-symbolic"
echo "---"


echo "Day 100% | iconName=notification-display-brightness-full bash='~/bin/monitors.sh 100 day' terminal=false refresh=true"
echo "Day 75% | iconName=notification-display-brightness-high bash='~/bin/monitors.sh 75 day' terminal=false refresh=true"
echo "Evening 50% | iconName=notification-display-brightness-medium bash='~/bin/monitors.sh 50 evening' terminal=false refresh=true"
echo "Dusk 35% | iconName=notification-display-brightness-off bash='~/bin/monitors.sh 35 evening' terminal=false refresh=true"
echo "Night 10% | iconName=notification-display-brightness-off bash='~/bin/monitors.sh 10 night' terminal=false refresh=true"
echo "Dead of night 1% | iconName=weather-clear-night bash='~/bin/monitors.sh 1 night' terminal=false refresh=true"

```


If your still reading this, thanks. 

I am no programmer so all help/advise to optimize the above scripts is very welcome..

Thanks for reading.

---

### Post by again? on 2017-06-03
Nice work but, are you using Ubuntu?
ddcutil isn't in the Ubuntu repositories.
I can only find a launchpad ppa with a Xenial package.

---

