---
title: "Solve the problem and earn a cookie... :)"
date: 2009-08-25
forum: Desktop Environments
---

### Post by red33m on 2009-08-25
I was just trying to install a program called byzanza (from the synaptic package manager).I did install it but for the program to run well the visual effects must be turned off.I did that too... But when I tried to select the Extra visual effects the computer said that it cannot be done...Note that I was using the extra visual effects and compiz config...I had the cube, expo function and everything...

How can I get the Extra visual effects back?:confused::confused::confused:

---

### Post by rwittke on 2009-08-25
I had se same problem when I updated from 7.04 to 8.04. I solved it by removing my graphiccard Module/Driver from compiz blacklist.

---

### Post by pawhtiobo on 2009-08-25
Hi :)

What do you get when you type in console:

$**lspci | grep VGA**

and

$**glxinfo | grep direct**

tell us the result...


see ya...

---

### Post by red33m on 2009-08-25
> **rwittke said:**
> I had se same problem when I updated from 7.04 to 8.04. I solved it by removing my graphiccard Module/Driver from compiz blacklist.



how can I do that...

yeah a little noobish....


Thanks for your time...!

---

### Post by red33m on 2009-08-25
well that:

for the first: 05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 LE] (rev a2)
and the second one: direct rendering: Yes

---

### Post by pawhtiobo on 2009-08-25
Well, direct rendering is working, so something changed (byzanza) your xorg.conf, that is probably the reason why you can't enable efects...

1º Make a copy of your xorg.conf... **/etc/X11/xorg.conf**

2º $[B]sudo dpkg-*reconfigure* -phigh *xserver*-xorg

[/B]3º[B] Reboot

[/B]tell us the result...[B]


[/B]see ya...[B]
[/B]

---

### Post by red33m on 2009-08-25
God I am such a noob...how do I do the first one?

---

### Post by pawhtiobo on 2009-08-25
No problem :)... we are here to help...

It can be done this way, in console:

$**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup **or just use the filemanager to browse to this folder /etc/X11 and copy xorg.conf to anywhere you like :)
Then you can do in console...the other steps i said in previous post[B].

[/B]see ya...

---

### Post by red33m on 2009-08-25
I did the first two...the first said nothing

the second said this:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090825135315
now I am rebooting..

---

### Post by pawhtiobo on 2009-08-25
The last msg is normal :)... he is just saying that he made a backup of the original xorg.conf.

see ya...

---

### Post by red33m on 2009-08-25
After the reboot I tried to enable the extra visual effects and nothing...it said that it could not be enabled...

---

### Post by red33m on 2009-08-25
After the reboot I tried to enable the extra visual effects and nothing...it said that it could not be enabled...is their anything I can do now?

---

### Post by pawhtiobo on 2009-08-25
Next we can try to remove byzanza using synaptics package manager...it was after this that the problem started...

---

### Post by red33m on 2009-08-25
Nah..I completely removed it and again nothing..

---

### Post by pawhtiobo on 2009-08-25
We can also try this in console:

$[B]sudo gedit .config/compiz/compiz-manager 
[/B]
then add to the file this[B]

SKIP_CHECKS=yes[/B]

then logoff or reboot

see ya...

---

### Post by zipperback on 2009-08-25
Hi,

There are quite a number of programs that don't work very well with compiz running.

To shut off compiz and the fancy graphic stuff I have a script which I can run that issues the following command.

```

metacity --replace &

```

To turn compiz and the fancy graphic stuff back on, I have a script which I can run that issues the following command.
```

compiz --replace &

```

I have my desktop setup, so I can just right click on the desktop and select it from a menu to turn it on or off.

You can also use "fusion-icon" which is a small system tray application that does basically the same thing. It should be available to you to install using synaptic. 

Hope this helps you,

- zipperback

---

### Post by pawhtiobo on 2009-08-25
> **zipperback said:**
> Hi,

There are quite a number of programs that don't work very well with compiz running.

To shut off compiz and the fancy graphic stuff I have a script which I can run that issues the following command.

```

metacity --replace &

```To turn compiz and the fancy graphic stuff back on, I have a script which I can run that issues the following command.
```

compiz --replace &

```I have my desktop setup, so I can just right click on the desktop and select it from a menu to turn it on or off.

You can also use "fusion-icon" which is a small system tray application that does basically the same thing. It should be available to you to install using synaptic. 

Hope this helps you,

- zipperback

That's true, but now compiz don't activate effects, any idea?

---

### Post by red33m on 2009-08-25
not even that seems to work... :(

---

### Post by pawhtiobo on 2009-08-25
No pain no gain...lool :D

We can try to remove compiz using synaptics, and choose "complete remove", and reinstall it again, also install fusion icon and compiz manager, and add fusion icon to startup, if you don't know how to, just ask :)

see ya...

---

### Post by red33m on 2009-08-25
did all of that...fusion icon does not open so I am rebooting..

---

### Post by red33m on 2009-08-25
yap...nothing at all... o_O

and the fusion icon won't start... !

---

### Post by pawhtiobo on 2009-08-25
Try to launch fusion icon from console, type:

$**fusion-icon**

then put here, if it gives an error.

Also see this [http://ubuntuforums.org/showthread.php?t=1093512](http://ubuntuforums.org/showthread.php?t=1093512)

---

### Post by red33m on 2009-08-25
As you said it..it gave me an error but I could not copy it..because after that the window decorations were gone and I had to reboot...

The only sure thing is that the fusion icon did not start....grrr....

---

### Post by pawhtiobo on 2009-08-25
Have you seen the other post that i mentioned earlier? Have you tryed that option:
[B]
fusion-icon --no-start

[/B]Another thing that i remember now, is that maybe the VGA driver is not correct, or not activated in the hardware manager.

---

### Post by red33m on 2009-08-25
did not work...here is the error:
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Segmentation fault
Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
/home/red33m/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/red33m/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/red33m/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

Lets try one more thing out...How can I remove graphic cards module/drivers from compiz black list?

---

### Post by pawhtiobo on 2009-08-25
With that extra text added to compiz manager:

**SKIP_CHECKS=yes**

One question, if you run in the console:


**glxgears**

Can you see the image moving correctly?

---

### Post by red33m on 2009-08-25
it wrote this:

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

You know what that is?

---

### Post by pawhtiobo on 2009-08-25
That a driver/xorg.conf related error.

See this [http://ubuntuforums.org/archive/index.php/t-431265.html](http://ubuntuforums.org/archive/index.php/t-431265.html)

Also you can restore your original xorg.conf (the one we renamed to xorg.conf.backup), check if the driver is correctly activated in the HW maanager.


see ya...

---

### Post by red33m on 2009-08-25
I checked the hw manager and it is correctly installed...  !

First win  !  lol

---

### Post by red33m on 2009-08-25
I appreciate all the help mate...!!

I didn't manage to fix it but its O.K. I will just wait for the next Ubuntu upgrade were almost for sure the computer will be fixed(the Ubuntu 10.2 or something like that)...or I will just get along with it...Feels like I am in prison 'cause I have only one workspace left!! 

Ahh what the heck...I'll just shut it down and eat some Mousaka, watch some T.V. and rest a little..
It is gonna be a long night tonoght if you know what I'm saying ;)...

 See you later pal...take care!

---

### Post by pawhtiobo on 2009-08-25
Ok :)

One of these days we can try again if you want :)


see ya...

---

