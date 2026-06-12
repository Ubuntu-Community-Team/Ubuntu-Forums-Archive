---
title: "TFT pivot - orientation greyed out"
date: 2006-08-17
forum: Desktop Environments
---

### Post by SRTS on 2006-08-17
I'm using KUbuntu 6.06 and a HP2035 TFT that supports pivot, meaning it can be rotated by 90° for portrait mode.
I entered "system settings" -> "hardware" -> "display" -> "Size, Orientation & Positioning" to change the screen orientation, but all options under "Monitor Orientation" are greyed out! I cannot choose any other than "normal". (I was in 'administrator mode' of course.)
Any help is greatly appreciated.

---

### Post by zerwas on 2006-08-17
Hello,

I think this is a question of XRandR support.
Could you copy and paste this in your console and give us the output?
```
cat /var/log/Xorg.0.log |grep -i Rand
```
I would also be interested in the output of
```
xrandr
```
Also, having information about your graphics card would be nice to help you out of this :).

Greetings,
zerwas

---

### Post by SRTS on 2006-08-17
Oh didn't expect such a quick reply ^^

Graphics card is ATI Radeon 9500,
I installed ATIs driver and it says fglrx now, I think.

:~$ cat /var/log/Xorg.0.log |grep -i Rand
(==) RandR enabled
(II) Initializing built-in extension RANDR

:~$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1600 x 1200   ( 413mm x 313mm )  *75   70   60   65
 1   1792 x 1344   ( 413mm x 313mm )   60
 2   1856 x 1392   ( 413mm x 313mm )   60
 3   1400 x 1050   ( 413mm x 313mm )   75   60   85   70
 4   1920 x 1440   ( 413mm x 313mm )   60   75
 5   1280 x 960    ( 413mm x 313mm )   75   85   60
 6   1280 x 1024   ( 413mm x 313mm )   60   85   75
 7   1280 x 854    ( 413mm x 313mm )   55
 8   1152 x 768    ( 413mm x 313mm )   55
 9   1152 x 864    ( 413mm x 313mm )   75   85
 10  1024 x 768    ( 413mm x 313mm )   60   70   75   85
 11   832 x 624    ( 413mm x 313mm )   75
 12   800 x 600    ( 413mm x 313mm )   60   85   75   72   56
 13   640 x 480    ( 413mm x 313mm )   85   75   73   60
 14  1920 x 1200   ( 413mm x 313mm )   73   60
 15  1680 x 1050   ( 413mm x 313mm )   85   60
 16  1440 x 900    ( 413mm x 313mm )   60
 17  1280 x 800    ( 413mm x 313mm )   60
 18  1280 x 768    ( 413mm x 313mm )   60
 19   720 x 400    ( 413mm x 313mm )   85
 20   640 x 400    ( 413mm x 313mm )   85
 21   640 x 350    ( 413mm x 313mm )   85
 22   416 x 312    ( 413mm x 313mm )   75
 23   400 x 300    ( 413mm x 313mm )   85   75   72   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none

By the way I noticed another odd thing: It seems the display dialogue doesn't give any option for changing the colour depth? I can only change resolution and frequency.

---

### Post by zerwas on 2006-08-17
> **SRTS said:**
> 
Graphics card is ATI Radeon 9500,
I installed ATIs driver and it says fglrx now, I think.

```
:~$ cat /var/log/Xorg.0.log |grep -i Rand
(==) RandR enabled
(II) Initializing built-in extension RANDR
```

This looks good :)

> **SRTS said:**
> 
```
:~$ xrandr
...
Rotations possible - normal
...
```
This does not look so good. It means, your current driver is not able to rotate the screen (if so, you would see "left", "right" and so on)

Now, you have a few options to make Pivot possible.
[list]
[*]Buy another card - nvidia e.g.
[*]Use an old an deprecated driver - fbdev
[*]Use Xvnc to get portrait mode
[/list]

First, i could tell you that the aeorator from my Radeon 9800 Pro seceded a few months ago. I knew, ATI hasn't built support in for its drivers to this point - that's why i boughta nvidia-card after this). So i used a solution with a patched Xvnc for Palms and had a quite fast surface in Portrait mode. 
If you aren't interested in this way and don't want to buy an nVidia-card (whose driver supports Pivot-mode a long time now) i can tell you another solution i used in my ATI-times:
[LIST=1]
[*]Open the X-configuration file: ```
sudo gedit /etc/X11/xorg.conf
```
[*]search for the word "fglrx" (it's in the Section "Device") and change it to "fbdev"
[*]In this Section "Device" add the following:```
Option   "Rotate" "CCW"
```
[*]Now press CTRL+Alt+Backspace to restart your graphical surface
[/LIST]
With this solution you won't be able to rotate your screen while X (your graphical surface) is running
> 
By the way I noticed another odd thing: It seems the display dialogue doesn't give any option for changing the colour depth? I can only change resolution and frequency.
Thats normal, perhaps in Edgy this circumstance will change. If you want to change your colour depth, use the tool [xorg-edit]("http://www.cyskat.de/dee/progxorg.htm") or change the value of "DefaultDepth" in /etc/X11/xorg.conf.
By the way! You must have a DefaultDepth of 16 with fbdev driver!

I hope i could help you. I remembered the nightmare with pivot, that i had with ATI ;)

Greetings,
zerwas

edit: i have other solutions in mind, but tell me your thoughts on my reply :). If you are still not satisfied, i can tell you more.

---

### Post by SRTS on 2006-08-17
Well I don't feel like buying a new card just for this. oO

Also, I use opengl, will that work with 'fbdev'? If yes, what's the drawback using it?

xvnc.. I have some idea what that implies. Well, if it doesn't slow the computer down a lot, I'd like to hear more of it.

Also, did I get that right: If just ATI added a pivot option to their linux drivers, that would solve all the problems?

---

### Post by zerwas on 2006-08-17
> Also, I use opengl, will that work with 'fbdev'? If yes, what's the drawback using it?
OpenGL does not work with fbdev, sorry.

> xvnc.. I have some idea what that implies. Well, if it doesn't slow the computer down a lot, I'd like to hear more of it.
Umm..ok, it's a long time ago since i have done this. It means you have to go to [homepage]("http://www.freesoft.org/software/vncrotation/") of the Xvnc+rotation developer.
There are two options to use it:
[list]
[*]run x11vnc as a user or
[*]configure the (physical display's) X server to support the vnc extension[/list]
For the first method read the text in the link.
Let me give a sentence on the second method. You should have vnc-common and x11-vnc installed. You also have to substitute the Xvnc-executable from the link above with your current.
In /etc/X11/xorg.conf under Section "Module" there must be a line:
```
  Load     "vnc"
```
and in Section "Screen" this:
```

  #This tells X where to locate the VNC password file
  Option     "PasswordFile"    "/home/your_user_name/.vnc/passwd"

```
Change Section "Files" to include this:
```
 Section "Files"
    ModulePath "/usr/lib/modules/extensions"
    ModulePath "/usr/lib/xorg/modules"
```
Ok, i think it's done then by doing:
```
$ mkdir ~/.vnc
 $ vncpasswd ~/.vnc/passwd
   Password:
   Verify:
```
Restart X after this.

There are much Xvnc HOWTOs around the web :) if this is not the perfect solution. I can remember i had activated Xvnc by the start of GDM.

> Also, did I get that right: If just ATI added a pivot option to their linux drivers, that would solve all the problems?
That's completely right. You should peeve ATI to do that ;) (write mails, bug on the forums)

---

