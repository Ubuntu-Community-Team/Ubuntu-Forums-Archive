---
title: "beryl 3d  cube"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by zerobinary on 2007-06-26
beryl 3d deaktop cube i check the cube option in beryl manager and i can only rotate try press ctrl+alt + mouse still no goal

---

### Post by steve-shinn on 2007-06-26
have you enable desktop cube & rotate cube....if so try pressing & holding mouse wheel down whilst moving the mouse

---

### Post by bodhi.zazen on 2007-06-26
Try rotating with the mouse wheel or I believe the arrow keys.

Also you can rotate with the middle mouse button. Push down and hole.

---

### Post by halesquad on 2007-06-26
don't you have to be on the desktop to rotate the cube ??

---

### Post by zerobinary on 2007-06-26
is it because i only have two workspace
what have you enable desktop cube & rotate cube???
can u give me a pic for that

---

### Post by bodhi.zazen on 2007-06-27
> **zerobinary said:**
> is it because i only have two workspace
what have you enable desktop cube & rotate cube???
can u give me a pic for that

It sounds as if you may not have beryl running yet :???:

Open a terminal and type : ```
beryl-manager
```

Post any errors.

If you still have no cube, go to the red gem Right click on it go to "Select widow manager" and select Beryl.

You can change (rotate) the cube via mouse or keyboard.

With the mouse, use the scroll wheel.

With the keyboard, Ctrl-Alt-<arrow_keys>

---

### Post by HarshReality on 2007-06-27
I tried this and got file not found... now beryl-settings-manager got something

---

### Post by bodhi.zazen on 2007-06-27
> **HarshReality said:**
> I tried this and got file not found... now beryl-settings-manager got something

Perhaps you need to install beryl ?

```
sudo apt-get install beryl emerald-themes
```

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

---

### Post by zerobinary on 2007-06-27
```
Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options
beryl: Failed to load slide: /home/robb/hotcorners_racarr.svg
beryl: Failed to load slide: /home/robb/hotcorners_racarr.svg
```
and the setting is beryl

---

### Post by bodhi.zazen on 2007-06-27
Try :

```
gnome-xgl-switch -d
gnome-xgl-switch --enable-xgl --auto
```

---

### Post by tom1g on 2007-06-27
I have problems with cube too. I don't see cube when I press ctr alt arrow keys

i have 1 workspace, beryl manager, emerald theme manager,  and beryl settings manager

i also have this problem: [[IMG]http://img224.imageshack.us/img224/5586/screenshotsi3.th.png[/IMG]](http://img224.imageshack.us/my.php?image=screenshotsi3.png)

edit: borders of my windows are damaged

---

### Post by bodhi.zazen on 2007-06-27
> **tom1g said:**
> I have problems with cube too. I don't see cube when I press ctr alt arrow keys

i have 1 workspace, beryl manager, emerald theme manager,  and beryl settings manager

i also have this problem: [[IMG]http://img224.imageshack.us/img224/5586/screenshotsi3.th.png[/IMG]](http://img224.imageshack.us/my.php?image=screenshotsi3.png)

edit: borders of my windows are damaged

Do you need to :

1. Configure compiz (enable cube)

2. Install Beryl (sudo apt-get install beryl) ; then with the red gem change from compiz to beryl.

I looked at your screen shot and am not sure of the problem ??

---

### Post by tom1g on 2007-06-27
> **bodhi.zazen said:**
> Do you need to :

1. Configure compiz (enable cube)

2. Install Beryl (sudo apt-get install beryl) ; then with the red gem change from compiz to beryl.

I looked at your screen shot and am not sure of the problem ??

WIndows don't have maxmize, minimize and restore buttone, neither the border... I see red gem, what now?

---

### Post by bodhi.zazen on 2007-06-27
Ah, well that is compiz ;)

If you float your mouse over the transparent border and click where the buttons should be they may work ... then again maybe not ... You could change the theme.

If you have beryl installed (not just beryl-manager) -> go to the red gem, right click -> select window manager -> select beryl

---

### Post by tom1g on 2007-06-27
> **bodhi.zazen said:**
> Ah, well that is compiz ;)

If you float your mouse over the transparent border and click where the buttons should be they may work ... then again maybe not ... You could change the theme.

If you have beryl installed (not just beryl-manager) -> go to the red gem, right click -> select window manager -> select beryl

They work. Beryl was selected. Should I reboot?

---

### Post by bodhi.zazen on 2007-06-27
You should not need to re-boot.

You could log out and back in. Open a terminal and type ```
beryl-manager
```

If that does not work, select emerald theme manager and choose an alternate theme/window decoration.

---

### Post by tom1g on 2007-06-27
> **bodhi.zazen said:**
> You should not need to re-boot.

You could log out and back in. Open a terminal and type ```
beryl-manager
```

If that does not work, select emerald theme manager and choose an alternate theme/window decoration.

I switched to Compiz and then back to Beryl and window borders are fine now, but i want cube (one of the reasons why i installed ubuntu) :(

tomi@IlFenomeno:~$ beryl-manager
tomi@IlFenomeno:~$

---

### Post by bodhi.zazen on 2007-06-27
No cube ?

What happens if you:

1. use the keyboard ? Ctrl-Alt-Right Arrow (or up arrow ...)

2. Use the mouse. Float it over an empty region of the desktop, roll the mouse wheel. Or push down the mouse wheel and (with the button depressed) drag the mouse ?

---

### Post by tom1g on 2007-06-27
Ctrl Alt Right (or up) 
[[IMG]http://img528.imageshack.us/img528/548/screenshot1wm9.th.png[/IMG]](http://img528.imageshack.us/my.php?image=screenshot1wm9.png)
Using mouse: nothing happens

---

### Post by tom1g on 2007-06-27
> **tom1g said:**
> Ctrl Alt Right (or up) 
[[IMG]http://img528.imageshack.us/img528/548/screenshot1wm9.th.png[/IMG]](http://img528.imageshack.us/my.php?image=screenshot1wm9.png)
Using mouse: nothing happens

Hmmm, strange thing happens: if I enable desktop effects, switch to ckompiz, then back to beryl, desktop efffetcts aren't turned on. Now i turned them back on. Cube still doesn't work =(

edit: new screenshot posted: [[IMG]http://img154.imageshack.us/img154/687/screenshot2ig3.th.png[/IMG]](http://img154.imageshack.us/my.php?image=screenshot2ig3.png)

---

### Post by tom1g on 2007-06-27
> **tom1g said:**
> Hmmm, strange thing happens: if I enable desktop effects, switch to ckompiz, then back to beryl, desktop efffetcts aren't turned on. Now i turned them back on. Cube still doesn't work =(

edit: new screenshot posted: [[IMG]http://img154.imageshack.us/img154/687/screenshot2ig3.th.png[/IMG]](http://img154.imageshack.us/my.php?image=screenshot2ig3.png)

Any ideas?

---

### Post by zerobinary on 2007-06-27
```
zerobinary@zerobinary:~$ beryl-manager
zerobinary@zerobinary:~$ **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options
Engine settings loaded
Engine settings loaded
beryl: Failed to load slide: /home/robb/hotcorners_racarr.svg
beryl: Failed to load slide: /home/robb/hotcorners_racarr.svg
Reloading...
Engine settings loaded

(emerald:6246): Gdk-CRITICAL **: gdk_drawable_unref: assertion `GDK_IS_DRAWABLE (drawable)' failed

```

---

### Post by zerobinary on 2007-06-27
zerobinary@zerobinary:~$ gnome-xgl-switch -d
bash: gnome-xgl-switch: command not found
zerobinary@zerobinary:~$ gnome-xgl-switch --enable-xgl --auto
bash: gnome-xgl-switch: command not found
zerobinary@zerobinary:~$ 
i think u need at least 4 workspace in order to produce a cube 
but i don't know how to add more workspace

---

