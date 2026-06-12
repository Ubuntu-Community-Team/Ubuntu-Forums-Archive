---
title: "WINE w/ World of Warcraft (WoW) walking stutters"
date: 2009-04-08
forum: General Help
---

### Post by brianbourke75 on 2009-04-08
Having recently upgraded to the Jaunty Beta and installing Wine 1.1.18, I have noticed that when I am playing WoW my character "stutter steps" when I walk forward.  By all appearances it seems that by holding down the "W" or "S" keys for walking forwards or backwards seems to send a continous stream of key-up and key-down events.

Anyone else have this issue?

B

---

### Post by leveliv on 2009-04-08
Damn I wish I could even play my install of WoW ...my graphics are all screwy, the sound is great but it's just a graphics problem...Maybe I'll find an updated Intel driver..

What kind of specs are you running maybe it's just generally slow because of your hardware? 

did you try lowering your settings in game? Did that help? Other people have had it installed. Maybe its wine...or it could just be the Jaunty beta acting up. 

Sorry I couldn't be of any help but I will do some searching for you cause I mainly switched to Ubuntu to play WoW (on vista it was hella slow) and thats bad for a DirectX 8 game haha. 


Actually I forgot to ask..What kind of FPS are you getting?  Are you on Nvidia...(with the newest drivers) could be a bug in the drivers? 

Anyways I will look around while I fix my own WoW problems hopefully we can get this fixed, Maybe Blizz will get nice and put out a WoW Linux client *prays* ...I may be asking too much

---

### Post by 3Miro on 2009-04-08
There is big wine forum at winehq, I am sure there are many people that have made WoW work under Linux (it is such a popular game) and they can help you.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922)

Look for newer versions of wine, information about 0.9x is probably no longer valid.

---

### Post by Revan13 on 2009-04-08
I have exactly the same issue! 
The problem appeared when I upgraded my ubuntu from 8.10 to 9.04 beta. 
Maybe there are some differences between the two versions' keyboard event handling... Dunno. 

I've found nothing useful so far :(

---

### Post by brianbourke75 on 2009-04-08
Upon second consideration, I do recall a package (i think xkeyboard or somethign to that affect) failing to install properly.  Upon using the next day's update the problem seem to have fixed itself so I never gave it any more thought... Anyone have any thoughts on this?

B

---

### Post by Revan13 on 2009-04-08
> **brianbourke75 said:**
> Upon second consideration, I do recall a package (i think xkeyboard or somethign to that affect) failing to install properly.  Upon using the next day's update the problem seem to have fixed itself so I never gave it any more thought... Anyone have any thoughts on this?

B

can u explain what did you do to solve the problem? :) It seems that my version of jaunty works fine, except this annoying wow bug. I also updated my system but nothing changed. Can you dig out which package(s) should be updated to fix the error? :)

a fake solution: system -> preferences -> keyboard : uncheck the "key presses repeat when is held down" box
(it works, but it affects the desktop env)

thx n regards

---

### Post by brianbourke75 on 2009-04-08
Oh, I am still experiencing the issue.  I was just hoping that someone had some experience with the xkeyboard issue and that would help a solution come to light.  Regardless, I will try your fix for in the keyboard settings :)

B

---

### Post by jparchem on 2009-04-25
I'm seeing the exact same issue here under Cedega.  I get the repeat character stuttering deal and it doesn't seem to matter if I'm running under DirectX emulation or OpenGL.

---

### Post by jparchem on 2009-04-26
One of the things I have been trying to accomplish is making a script that can be launched with ONE click that disables Compiz, disables the keyboard repeating for the movement keys (to fix the movement stuttering) and then launches WoW.  When WoW exits, I want that same script to turn the key repeats back on and re-load Compiz.  I'm no bash programmer, but I did cobble together a very basic script to do this from bits I found scattered amongst various posts here.

1)  First I used a program called 'xkeycaps' (from repo) that shows the scan codes for your keyboard; you'll need these to tell X11 which keys to turn off the repeating for.   

2)  Next, I downloaded a program called [compiz-switch]("http://forlong.blogage.de/entries/pages/Compiz-Switch") which allows you to toggle on and off compiz.

3)  Finally I created a very simple script borrowing a few lines from [this]("http://ubuntuforums.org/showthread.php?t=989578") post which has a loop which checks to see if a program (Wine in my case) is still running.

4)  Finally, I used xset to toggle on/off the individual keys that impact character stuttering in WoW- mainly the "W", "A", "S", "D" keys.

A copy of the script is below.  Again its basic but its enough for my needs.

```

#! /bin/bash
# Turn off key repeats for W,A,S,D,SPACEBAR and Arrow Keys

xset -r 25
xset -r 38
xset -r 39
xset -r 40
xset -r 41
xset -r 98
xset -r 100
xset -r 102
xset -r 104

# Turn off Compiz
/usr/bin/compiz-switch

# Run WoW
cedega --run "World of Warcraft Wrath of the Lich King" "World of Warcraft"

# Wait for WoW to exit so we can turn the keys back on.  If we don't wait they will immediately
# turn back on
t=`/bin/pidof wine` # checking pid to see if wine is running
while [ -n "$t" ] # while wine is running
do
t=`/bin/pidof wine`
done


if [ -z "$t" ] # If wine process not running , 'pidof' returns null.
then
# Turn on key repeats back on for W,A,S,D,SPACEBAR and Arrow Keys
xset r 25
xset r 38
xset r 39
xset r 40
xset r 41
xset r 98
xset r 100
xset r 102
xset r 104
/usr/bin/compiz-switch
fi # end of if condition

exit 0 # exiting without error


```

---

### Post by Gizim on 2009-04-26
Same issue i found this 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

But doing xset -r makes my ENTER key held down and in all apps the R key is repeated.
Not sure about you guys but its EVERY key not just WASD.

[http://bugs.launchpad.net/bugs/367136](http://bugs.launchpad.net/bugs/367136) has been filed

---

### Post by jparchem on 2009-04-26
Did you try to use xset specifying a key scancode after it ( e.g. xset -r 25)?  If I do that it xset works fine for me. 

If I leave the keyboard scan code out and just try to disable all repeating with "xset -r", then that seems to trigger the bug that causes the endless stream of enter key inputs sent by X but again if I always provide a scancode, I'm good.

Anyhow, I filed a bug report on the 'xset -r' option to at least make them aware of it.

---

### Post by avam323 on 2009-04-29
i had trouble with all this as well, but looking up the links provided by earlier folks to cobble together a much simpler script that does everything one should need to fix all these problems:

```
#!/bin/sh

metacity --replace &
"/home/avam/.wine/drive_c/Program Files/World of Warcraft/Interface/AddOns/wowmatrix"
xset r off
wine "/home/avam/.wine/drive_c/Program Files/World of Warcraft/Wow.exe" -opengl
xset r on
compiz --replace &
```

works great, but those who do not use wowmatrix to update addons (YES they have a native linux client!!!), just get rid of that line. ty for the help all!! :D

---

### Post by dardack on 2009-07-29
For those that want to disable QWSE (my back S, Forward W, Strafe Right Q, Strafe Left E) the only ones that i really use for movement to stop the stuttering while walking here's my script:

```
#! /bin/bash

xset -r 25
xset -r 24
xset -r 39
xset -r 26

env WINE_CURSOR=anything; wine <Your WoW Directory>/Wow.exe

echo "Reenabling auto repeat"
xset r 25
xset r 24
xset r 39
xset r 26

```

the env WINE_CURSOR=anything; is for the OpenGL HW cursor.  Now this wont' work if you change wow.exe to launcher.exe cause once you hit play on the launcher this script assumes it's finished and the renabling of the auto repeat takes place.  Just an FYI.

---

### Post by countervail on 2010-01-23
> **avam323 said:**
> i had trouble with all this as well, but looking up the links provided by earlier folks to cobble together a much simpler script that does everything one should need to fix all these problems:

```
#!/bin/sh

metacity --replace &
"/home/avam/.wine/drive_c/Program Files/World of Warcraft/Interface/AddOns/wowmatrix"
xset r off
wine "/home/avam/.wine/drive_c/Program Files/World of Warcraft/Wow.exe" -opengl
xset r on
compiz --replace &
```

works great, but those who do not use wowmatrix to update addons (YES they have a native linux client!!!), just get rid of that line. ty for the help all!! :D

Thanks for the script! love it =)

No fix yet for the walking stutters? :x

---

### Post by lacktorium on 2010-02-19
thx for the codes, but sadly still no luck. using ubuntu 9.10 w/wine 1.1.31. tried bolth opengl and d3d mode same issue with bolth. i prefer to use d3d because to the hardware cursor but it gives trouble with the shadow and some ground effects.

---

### Post by Blindsleeper on 2010-02-20
if you create a new file in /usr/bin/ and put the following in it (I called it 'gamerun', because that's what the original author of part of this script called it):
```
#!/bin/bash

CHANGE=0

if ps -e | grep compiz; then
CHANGE=1
fi

if [ $CHANGE == 1 ]; then
/usr/bin/metacity --replace &
fi

xset -r 25
xset -r 24
xset -r 39
xset -r 26

$@ &
wait $!

if [ $CHANGE == 1 ]; then
/usr/bin/compiz --replace &
fi

xset r 25
xset r 24
xset r 39
xset r 26

exit 0
```

then change your menu link to be:
```
gamerun wine "/locationtoWoW/Wow.exe" -opengl
```

or if you prefer directx:
```
gamerun wine "/locationtoWoW/Wow.exe"
```

This script will do the following:
1. if compiz is running, switch to metacity, then turn off repeat for q,w,e,s.
2. wait until the program is done
3. if we turned off compiz, switch back to compiz, then turn on repeat for q,w,e,s.

---

### Post by lacktorium on 2010-02-20
Hi Blindsleeper, thank you for sharing. 
however I am get a Segmentation fault when i run it. i am not to skilled at scripting, is there a way to use compiz-switch in the same manner?

---

### Post by Blindsleeper on 2010-02-20
Hello lacktorium, are you getting a seg fault from WoW?

to use compiz switch, you should just be able to change the file to:
```
#!/bin/bash

CHANGE=0

if ps -e | grep compiz; then
CHANGE=1
fi

if [ $CHANGE == 1 ]; then
/usr/bin/compiz-switch
fi

xset -r 25
xset -r 24
xset -r 39
xset -r 26

$@ &
wait $!

if [ $CHANGE == 1 ]; then
/usr/bin/compiz-switch
fi

xset r 25
xset r 24
xset r 39
xset r 26

exit 0
```

note that I have not tested this, as I do not have compiz-switch installed

---

### Post by lacktorium on 2010-02-20
no just from the script
```

lacktorium@Deaths-Desktop:~$ gamerun
23126 ?        00:00:02 compiz.real
Checking for Xgl: not present. 
lacktorium@Deaths-Desktop:~$ xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1920x1080) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Segmentation fault
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x220053b (lacktorium)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

``` this is the output in terminal for just running gamerun

---

### Post by lacktorium on 2010-02-20
> **Blindsleeper said:**
> Hello lacktorium, are you getting a seg fault from WoW?

to use compiz switch, you should just be able to change the file to:
```
#!/bin/bash

CHANGE=0

if ps -e | grep compiz; then
CHANGE=1
fi

if [ $CHANGE == 1 ]; then
/usr/bin/compiz-switch
fi

xset -r 25
xset -r 24
xset -r 39
xset -r 26

$@ &
wait $!

if [ $CHANGE == 1 ]; then
/usr/bin/compiz-switch
fi

xset r 25
xset r 24
xset r 39
xset r 26

exit 0
```

note that I have not tested this, as I do not have compiz-switch installed

this fixed my previous problem but still wont change back on exit

Edit: I am running the newest ATI proprietary fglrx driver. if that helps at all

---

### Post by Blindsleeper on 2010-02-20
it wont change back to compiz or re-enable key repeat?

---

### Post by lacktorium on 2010-02-20
re-enables key repeat but not compiz. i have fusion-icon running and have to manual click on compiz then it reloads.

i am also using emerald.

Edit: also noticed it resets all of compiz to defualt settings.

---

### Post by lacktorium on 2010-02-23
i've had some luck with the code using the compiz switch version it works. however it wont run the program.

```
lacktorium@Deaths-Desktop:~$ gamerun wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl
 3563 ?        00:00:00 compiz
wine: cannot find 'C:\Program'
lacktorium@Deaths-Desktop:~$ 

```

it works fine when I don't add gamerun to it.

---

### Post by Blindsleeper on 2010-02-23
you would need to use the linux directory its attached to more than likely.  Mine is: ```
gamerun wine "/media/Data/WorldofWarcraft/Wow.exe" -opengl
``` for example. I can't really say if that's an issue with ATI or not, I have an nvidia card, but its possible that emerald is the cause of your problems.

---

### Post by lacktorium on 2010-02-23
ok i know mine is in this the wine folder ```
/home/lacktorium/.wine/drive_c/Program Files/World of Warcraft
```

so would i need to move the directory or something else?

thx for your help.

Edit: i copied the entire install from a window comp

---

