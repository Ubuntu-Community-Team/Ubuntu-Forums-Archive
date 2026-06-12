---
title: "Enable / Disable Touchscreen"
date: 2013-01-02
forum: Desktop Environments
---

### Post by jpmolla on 2013-01-02
Hi,
That's not a post to complain but to share :-)
I have bought a X202EP computer with Windows 8 pre-installed and have succeeded (with friends from arround...) to dual boot it with Ubuntu in UEFI. This computer is great as I wanted to have a touch screen experience. As Windows 8 is well design for a touch experience (really focused on that...) I don't spend most of my time on it. Ubuntu still is my preference but I don't find the necessity of the touchscreen on it. So I have decided to disable it !

If some of you are interested here is what I have done. And if you can do much better or just improve it, please share !!!

The command to know for that is ''xinput''. You can grab or change the status of peripherals with it. a ''man xinput'' will tell you more on that.

To use it you need to know what peripheral you are interested to :
```

gepeto@x202ep ~$ xinput --list
&#9121; Virtual core pointer                      id=2    [master pointer  (3)]&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                  id=13   [slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer            id=10   [slave  pointer  (2)]
&#9123; Virtual core keyboard                     id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                      id=9    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                          id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=12   [slave  keyboard (3)]

```Ok that's the list of input peripherals. the device I am interested in (the touchscreen) is the 'Atmel maXTouch Digitizer" (id=10), just find yourself if your configuration is different. So if I wanna disable it I can do it in 3 manners :

```

xinput set-prop 'Atmel Atmel maXTouch Digitizer' 'Device Enabled' 0

xinput set-prop 10 'Device Enabled' 0

xinput disable 'Atmel Atmel maXTouch Digitizer'

```I am sure you can find a fourth one and even the way to enable it, right ? But that's enough to me. I am only using the third way. So to Enable or Disable the touchscreen I will use this


```
xinput enable 'Atmel Atmel maXTouch Digitizer'
```or this

```
xinput disable 'Atmel Atmel maXTouch Digitizer'
```OK. In the script, I wanna switch from activation to desactivation depending on the present state. So I need to grab the state of the touchscreen. Is it currently enabled or disabled ? For that purpose, I will need that :
```
xinput list-props 'Atmel Atmel maXTouch Digitizer'
``` (man is your friend :-))

The problem is that i have got a lot of features... For my final script I only need the Device Enabled result : is it 0 or 1 ?  So I will play with grep and sed :

```

gepeto@x202ep ~$ xinput list-props 'Atmel Atmel maXTouch Digitizer' | grep 'Device Enabled' | sed 's/.*\([0-9]\)$/\1/'
1

```I am pretty sure that something more beautiful could be done to extract this but that's the way I have done. Share your suggestion to complete.

So now I have got my result so I can do the script. Here it is :

```

#! /bin/bash
#  switch_touchscreen.sh
 
DEVICE="Atmel Atmel maXTouch Digitizer"
STATUS=`xinput list-props "$DEVICE" | grep 'Device Enabled' | sed 's/.*\([0-9]\)$/\1/'`
 
if [ "$STATUS" = "1" ]
then
    xinput disable 'Atmel Atmel maXTouch Digitizer'
    echo "Touch-screen disabled"
elif [ "$STATUS" = "0" ]
then
    xinput enable 'Atmel Atmel maXTouch Digitizer'
    echo "Touch-screen enabled"
else
    echo "Error : bad argument"
fi

```then you have to make this script executable :

```
sudo chmod a+x switch_touchscreen.sh
```That's it ! you've got a script to enable/disable the touchscreen !

If you want, you just have to define a custom keyboard shortcut on ubuntu to launch it (seek for "shortcut")

Now... about a desktop notification ? you can do that like this in the script and in the right place :

```
notify-send "Touch-screen" "Disabled" -i /usr/share/pixmaps/touch-screen.png
```The icon is not included. So you have to grab one (thanx google) and place it on the right folder with the right name...

Hope it helps ! ;)

---

### Post by mr E on 2013-05-11
Many Thanks! This helps a lot
For my "Acer All in One" I do this:
```

#! /bin/bash
#  switch_touchscreen.sh
#  http://ubuntuforums.org/showthread.php?t=2100744
 
DEVICE="3M 3M MicroTouch USB controller"
STATUS=`xinput list-props "$DEVICE" | grep 'Device Enabled' | sed 's/.*\([0-9]\)$/\1/'`
 
if [ "$STATUS" = "1" ]
then
    xinput set-prop "$DEVICE" 'Device Enabled' 0
    echo "Touch-screen disabled"
    notify-send "Touch-screen" "Disabled" -i /usr/share/pixmaps/touch-screen.png
elif [ "$STATUS" = "0" ]
then
    xinput set-prop "$DEVICE" 'Device Enabled' 1
    echo "Touch-screen enabled"
    notify-send "Touch-screen" "Enabled" -i /usr/share/pixmaps/touch-screen.png
else
    echo "Error : bad argument"
fi

```

---

