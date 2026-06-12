---
title: "[B][/B]Beryl? Compiz? Whats Wrong?"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by J.One on 2007-08-05
PROBLEM:
When i log on, Beryl manager is running and after last update when i open a window it appears withought the upper bar with "open" "maximize" and " minimize".

When i change window manager to compiz, everythings fine.

Any ideas? Is Emerald themer causing this? Because when i run onto Beryl, Emerald themer doesen't change.It only change when i'm on compiz.

---

### Post by walkerk on 2007-08-05
> **J.One said:**
> PROBLEM:
When i log on, Beryl manager is running and after last update when i open a window it appears withought the upper bar with "open" "maximize" and " minimize".

When i change window manager to compiz, everythings fine.

Any ideas? Is Emerald themer causing this? Because when i run onto Beryl, Emerald themer doesen't change.It only change when i'm on compiz.

Did you try changing the window manager back to Beryl? When I had Beryl installed it crashed frequently. When the combined Compiz and Beryl this issue was resolved for me..

you can try in terminal:
to see if compiz will load
```
compiz --replace &
```

i believe this works.. don't remember though:
```
beryl --replace &
```

and to fall back on metacity (default)
```
metacity --replace &
```


I don't think emerald is the issue. It would be the WM's problem..

---

### Post by khughitt on 2007-08-05
What window manager did you want to use? If you right-click on beryl-manager you should be able to tell it what WM and what decoration drawer to use. If you are trying to use beryl, you might consider trying out [compiz fusion]("http://ubuntuforums.org/showthread.php?t=481314") which is the result of the compiz-beryl merge and has all of the old beryl features along with some new ones. First time I tried upgrading to compiz fusion it worked like a charm!

---

### Post by J.One on 2007-08-05
I tryied to change compiz and beryl window manager again and again, even the window decorator (i did all compinations) and still when i'm on beryl i can't see the upper bar. Only on compiz. I saw similar threats but they have not answer.

Any help would be appreciated!

---

### Post by walkerk on 2007-08-05
> **pwnedd said:**
> What window manager did you want to use? If you right-click on beryl-manager you should be able to tell it what WM and what decoration drawer to use. If you are trying to use beryl, you might consider trying out [compiz fusion]("http://ubuntuforums.org/showthread.php?t=481314") which is the result of the compiz-beryl merge and has all of the old beryl features along with some new ones. First time I tried upgrading to compiz fusion it worked like a charm!

I agree with upgrading.. Beryl is unstable. With the merge the Beryl project's unstability went away and you can still use your Emerald themes.

---

### Post by J.One on 2007-08-05
i want beryl manager to be enable and i understand how beryl is unstable.
I also didn't understand what you mean by that

---

### Post by J.One on 2007-08-05
i just have installed compiz-fusion and it has non such similarity to Beryl...Beryl is miles ahead...Animations are much better...i think compiz is not yet ready....
ANYWAY! Any ideas to my problem? Still when i change to Beryl WM i don't get the upper bar. Do you think is the last update? Yesterday i had a huge update that i did't check what it did..

---

### Post by khughitt on 2007-08-05
> i just have installed compiz-fusion and it has non such similarity to Beryl...Beryl is miles ahead

Actually..beryl is more likely  [miles *behind* ]("http://www.opencompositing.org/"). As mentioned above the projects merged, and there is no longer any work done on beryl / beryl-manager. All of the features were subsumed with compiz-fusion, and any recent releases have been with compiz or compiz-fusion.

Did you install all of the optional plugins, and have you tried modifying the settings for compiz fusion? There is a configuration manager for compiz fusion which has all or nearly all of the options that were in beryl-manager along with some new ones.

---

### Post by J.One on 2007-08-05
of course i have the compiz manager, i tryied to fix it like beryl and it has framerate problem.IT LOOSES FRAMES, some other not working ex all animations even when i clicked them and it has some crap things like rotors moving and fishes going all around......(atlantis)

---

### Post by lucernario on 2007-08-05
Check your xorg.conf file. Make sure all modules are loaded (if you ran the xserver-xorg reconfigure you may have deleted some modules from the file, such as i2c)

You can edit the xorg.conf file (sudo gedit /etc/X11/xorg.conf) and check that these modules are loaded:

Section "Module"
	Load    "i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Also make sure, if you have an nVidia card, that these lines are there as well:
Section "Device"
	Identifier	"nVidia Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	[COLOR="Blue"]Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"[/COLOR]
	Option		"NoLogo"	"True"
EndSection

Remember to backup your xorg.conf file BEFORE you make any changes to it!

sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf_backup

Good luck!

---

### Post by J.One on 2007-08-05
Nothing happen Lucenario....Just the same. Listen to this though!
I've downloaded heliodor from synaptic manager and when i switched to it it worked but when i did a restart i fell onto the same again.Now as before only Aquamarine window decorator works, not heliodor not emerald not GTK either....All this when i'm on Beryl.

When i switch to conpiz fusion every window manager works fine.....What's hapenning?

---

### Post by J.One on 2007-08-05
didn't work.....

---

### Post by khughitt on 2007-08-05
That is strange. Can you give us a little more background information please- 1) Are you using Ubuntu 7.04? 2) What version of the driver do you have installed? 3) What is the output when you run **fglrxinfo** at the command prompt?

---

### Post by J.One on 2007-08-06
A)Ubuntu 7,04 AMD64 version

B)Last Drivers from Envy (no other way can play, not manual, not Automatix)

C)john@pc:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.09

---

### Post by khughitt on 2007-08-07
I have no set-up compiz with an nvidea card before- does anyone know if there is anything like the **aticonfig** tool for nvidia cards?

J.One - can you please post your entire xorg.conf to the forums.

---

