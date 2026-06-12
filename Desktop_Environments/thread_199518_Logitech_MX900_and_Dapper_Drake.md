---
title: "Logitech MX900 and Dapper Drake"
date: 2006-06-18
forum: Desktop Environments
---

### Post by DyDx on 2006-06-18
I don't think I ever had trouble with the Logitech MX900 in any previous version of Ubuntu (it is a Bluetooth mouse).  

I've figured out how to pair it with the bluetooth receiver using the command:

sudo hidd --connect 00:07:61:15:2E:E6

that being the MAC address of the mouse, which I get from hidd --search and then hitting the connect button on the mouse.

However, it appears I have to press the connect button every time I use the --connect switch, or do --search (which requires I press connect) and then --connect.

Does anyone have any idea how to get this to automatically pair when I boot my computer, without having to press connect?

It is a shame that it worked in previous versions fine but not now.

---

### Post by glotz on 2006-06-18
Well, what does your **cat /proc/bus/input/devices** read and what about your **cat /etc/X11/xorg.conf** (the mouse part) say?

---

### Post by luften on 2006-06-19
This information solved the problem for me:

-> [http://ubuntuforums.org/showthread.php?t=87919](http://ubuntuforums.org/showthread.php?t=87919)

However, My "back" and "forward" buttons are not working.. yet..

---

### Post by static chaser on 2006-06-22
Did anyone ever get the side buttons to work? I've gotten all the rest of the buttons to work with the hidd --connect business.

---

### Post by luften on 2006-06-26
[QUOTE=static chaser]Did anyone ever get the side buttons to work? I've gotten all the rest of the buttons to work with the hidd --connect business.[/QUOTE]

Yeah, I got all buttons (except the extra button on top) working.

The solution was simply to change settings in the xorg.conf file.

Currently my mouse settings there are:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7 8"
        Option          "Emulate3Buttons"       "false"
EndSection

```

---

### Post by glotz on 2006-06-26
[https://wiki.ubuntu.com/ManyButtonsMouseHowto](https://wiki.ubuntu.com/ManyButtonsMouseHowto)

---

### Post by Eddy_V on 2006-06-26
Hello,

I have a Logitech mx310 mouse. I tried a few howto's on the forum but none of them worked.
After experimenting I got my left/right buttons working in Nautilus, Firefox...

Some HOWTO's on this forum use 'xev', but mine xev showed left button as button number 8 and right button as button number 9. This is impossible cause mx310 has fewer buttons.

This is what got mine buttons working:
In /etc/X11/xorg.conf I have:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option          "Emulate3Buttons"       "false"
    Option          "Buttons"               "7"
    Option          "ZAxisMapping"          "4 5"
    Option          "ButtonMapping"   "1 2 3 6 7"
EndSection
```
First I used "xmodmap -e pointer = 1 2 3 6 7 4 5", but I got a error:
```
xmodmap:  commandline:1:  bad number of buttons, must have 11 instead of 7
xmodmap:  1 error encountered, aborting.
```
After that I 
```
sudo apt-get install imwheel
```
In /etc/X11/imwheel/imwheelrc on the end I have put:
(credits to someone on this forum, I think).
```

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

```
I made a startup script
```
nano -w mouse_buttons
```
```

#!/bin/sh
exec imwheel -k -b "67" &
exec $REALSTARTUP

```
Don't forget to make this file executable:
```
chmod +x mouse_buttons
```
Then I put this file in your sessions
(System -> Preferences -> Session
Under Startup Programs add your script
Mine is under /home/eddy/bin/mouse_buttons)
Login again and hopefully you will have back/forward buttons working in your apps.

---

