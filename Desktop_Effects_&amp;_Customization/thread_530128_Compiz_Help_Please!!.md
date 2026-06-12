---
title: "Compiz Help Please!!"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by Parms on 2007-08-20
OK, I've tried just about every route on these forums. Was hoping to get it running but have had errors with all of them.

I'm running 7.04 64bit with an ATI card. I got the drivers when I tried to enabled the restriced drivers thing. That seemed to work, as far as I know.

I tried the script that installs everything since I'm a noob. Problem is is that it can't find the compizconfig. I get the following error... 

parms@parms-laptop:~$ fusion-icon
* Using the GTK Interface
* No module named compizconfig
... Trying another interface
* Using the Qt4 Interface
* No module named PyQt4
... Trying another interface
* Using the Qt3 Interface
* No module named qt
... Trying another interface
* Error: All interfaces failed, aborting!
parms@parms-laptop:~$ 

I tried to uninstall / install several times. I read that forum like 30 times and can;'t figure out what I'm doing wrong. I followed everything to a tee.

Whats the easiest way to get this up and running?? Should I try another OS? Or a new install? My goal is to get compiz or beryl and all those cool effects. I need help!!! I messed around for  9 hours today and can't get any thing to work. Errrrrrrrrrrrrr!!!!!!!!!!!!  

Please Help. Thanks in advance.

---

### Post by Rupertronco on 2007-08-20
What repository did you use for the most recent install? also, did you make sure to remove any existing installs of compiz prior to your most recent one? What ati card are you using? The x1### cards are often difficult to get working properly (drivers-wise). Need a bit more info from you.

---

### Post by Ub1476 on 2007-08-20
I suppose you used this script: [Link]("http://ubuntuforums.org/showthread.php?t=508769")

It's not wroking for me neither, and I have an ATI card as well.. If you don't find a fix I recomend you to uninstall (run the script choose install, then uninstall), then delete the .compizconfig folder in your home directory (ctrl+h to show hidden files) then do:

```
sudo apt-get autoremove

apt-get clean
```

Now follow this [Guide.]("http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#amd64")

After you have installed CF, install Emerald too:

```
sudo apt-get install emerald emerald-themes
```

Now press ctrl+F2 and launch CF with:

```
compiz --replace -c emerald
``` ( if it doesn't work, you can try "compiz --replace" instead.

Hope that fix it.

---

### Post by hidden_leaf_sasuke on 2007-08-20
if you dont mind to give it a clean uninstall ( uninstall compiz n emeral ), you can try my guide on how to install it..kudos..:)

---

### Post by Parms on 2007-08-20
Yes I used that script with the link posted above. I have an ATI Radeon 200M video card. 

This was the order I did everything..

Updated to the latest everything...
Uninstalled previous attempts of installing emerald, compiz and veryl.

When I first ran the script It ended up un-installing everything.

I answered yes for Gnome on Gnome or KDE, I'm assuming Gnome is the GUI, that I'm using. I don't know what KDE is. 

When it asked if I had KDE files I selected no, and it installed some.

Nvidia graphics card.. Selected no

On all the installs I selected Yes.

I have the universe and multi universe options selected for the repositories. 

I think I'm going to start from scratch and a step by step guide would be nice. Because apparently this script hasn't worked for me, or there is more too it. 

I am a n00b to ubuntu but all my other scripts have worked for me.

---

### Post by Parms on 2007-08-20
> **hidden_leaf_sasuke said:**
> if you dont mind to give it a clean uninstall ( uninstall compiz n emeral ), you can try my guide on how to install it..kudos..:)

OK, I tried this and installed eyecandy. I get the gdesklets and when I load it, the shell window opens for about 10-15 seconds and thats it.

---

### Post by Parms on 2007-08-20
> **Ub1476 said:**
> I suppose you used this script: [Link]("http://ubuntuforums.org/showthread.php?t=508769")

It's not wroking for me neither, and I have an ATI card as well.. If you don't find a fix I recomend you to uninstall (run the script choose install, then uninstall), then delete the .compizconfig folder in your home directory (ctrl+h to show hidden files) then do:

```
sudo apt-get autoremove

apt-get clean
```

Now follow this [Guide.]("http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#amd64")

After you have installed CF, install Emerald too:

```
sudo apt-get install emerald emerald-themes
```

Now press ctrl+F2 and launch CF with:

```
compiz --replace -c emerald
``` ( if it doesn't work, you can try "compiz --replace" instead.

Hope that fix it.

I successfully did everything up to the ctrl+F2 part. Do you mean alt+F2. Anyways I tried those command lines and nothing happens. This is what I've got now...

I can succesfully open compizconfig. I can select and deselect things, yet nothing is happening to my windows, etc.. 

Is there anything else I have to do to get this to start when ubuntu starts? I mean the same settings each time?

---

### Post by Martje_001 on 2007-08-20
> **Parms said:**
> I can succesfully open compizconfig. I can select and deselect things, yet nothing is happening to my windows, etc.. 
Seems like that's a bug.. I've got it too.

---

### Post by Parms on 2007-08-20
> **Martje_001 said:**
> Seems like that's a bug.. I've got it too.

Errr... I thought I was there. A bug, huh? Is there a fix to this? Or any solutions that work?? I've been wanting to pull my hair outta my head, because I can't seem to get this program to work properly. I've tried just about everything!!

---

### Post by Parms on 2007-08-20
OK... I tried running in terminal to see what happens this is what I get...

parms@parms-laptop:~$ compiz --replace -c emerald
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
parms@parms-laptop:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
parms@parms-laptop:~$ 

Impossible to run on system?? 

Do I need extra drivers for my ATI card... I just clicked enable restricted driver and it installed its own thing. It says it's enabled.

ATI Radeon Xpress 200M

1 gig ram

---

### Post by Martje_001 on 2007-08-21
Have you set your setting in xorg.conf to 24 bit?

---

### Post by Parms on 2007-08-21
> **Ub1476 said:**
> I suppose you used this script: [Link]("http://ubuntuforums.org/showthread.php?t=508769")

It's not wroking for me neither, and I have an ATI card as well.. If you don't find a fix I recomend you to uninstall (run the script choose install, then uninstall), then delete the .compizconfig folder in your home directory (ctrl+h to show hidden files) then do:

```
sudo apt-get autoremove

apt-get clean
```

Now follow this [Guide.]("http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#amd64")

After you have installed CF, install Emerald too:

```
sudo apt-get install emerald emerald-themes
```

Now press ctrl+F2 and launch CF with:

```
compiz --replace -c emerald
``` ( if it doesn't work, you can try "compiz --replace" instead.

Hope that fix it.

I followed this step by step and this is what I get..

parms@linux:~$ compiz --replace
Backend     : ini
Integration : true
Profile     : default
Adding plugin plane (plane)
Adding plugin colorfilter (colorfilter)
Adding core settings (General Options)
Adding plugin annotate (annotate)
Adding plugin splash (splash)
Adding plugin resize (resize)
Adding plugin move (move)
Adding plugin clone (clone)
Adding plugin video (video)
Adding plugin winrules (winrules)
Adding plugin glib (glib)
Adding plugin crashhandler (crashhandler)
Adding plugin vpswitch (vpswitch)
Adding plugin snap (snap)
Adding plugin tile (tile)
Adding plugin thumbnail (thumbnail)
Adding plugin neg (neg)
Adding plugin text (text)
Adding plugin rotate (rotate)
Adding plugin png (png)
Adding plugin ezoom (ezoom)
Adding plugin extrawm (extrawm)
Adding plugin atlantis (atlantis)
Adding plugin ring (ring)
Adding plugin group (group)
Adding plugin snow (snow)
Adding plugin addhelper (addhelper)
Adding plugin trailfocus (trailfocus)
Adding plugin wall (wall)
Adding plugin switcher (switcher)
Adding plugin mousegestures (mousegestures)
Adding plugin scalefilter (scalefilter)
Adding plugin wallpaper (wallpaper)
Adding plugin resizeinfo (resizeinfo)
Adding plugin bench (bench)
Adding plugin firepaint (firepaint)
Adding plugin shift (shift)
Adding plugin kiosk (kiosk)
Adding plugin widget (widget)
Adding plugin scale (scale)
Adding plugin fade (fade)
Adding plugin keybinding (keybinding)
Adding plugin cheatsheet (cheatsheet)
Adding plugin screensaver (screensaver)
Adding plugin cube (cube)
Adding plugin minimize (minimize)
Adding plugin wobbly (wobbly)
Adding plugin gears (gears)
Adding plugin water (water)
Adding plugin inotify (inotify)
Adding plugin gotovp (gotovp)
Adding plugin opacify (opacify)
Adding plugin screenshot (screenshot)
Adding plugin 3d (3d)
Adding plugin svg (svg)
Adding plugin fs (fs)
Adding plugin regex (regex)
Adding plugin quickchange (quickchange)
Adding plugin dbus (dbus)
Adding plugin mblur (mblur)
Adding plugin workarounds (workarounds)
Adding plugin blur (blur)
Adding plugin fadedesktop (fadedesktop)
Adding plugin bs (bs)
Adding plugin animation (animation)
Adding plugin flash (flash)
Adding plugin reflex (reflex)
Adding plugin cubereflex (cubereflex)
Adding plugin put (put)
Adding plugin expo (expo)
Adding plugin imgjpeg (imgjpeg)
Adding plugin scaleaddon (scaleaddon)
Adding plugin decoration (decoration)
Adding plugin zoom (zoom)
Adding plugin showdesktop (showdesktop)
Adding plugin fakeargb (fakeargb)
Adding plugin place (place)
Initializing core options...done
Initializing resize options...done
Initializing move options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing minimize options...done
Initializing workarounds options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity

is there a way I can download that?

---

### Post by ricardoec on 2007-08-21
EVERITHING works fine for me EXCEPT

Compiz-Fusion !!!

Well, I have been posting and reading posts on this subject for more that two weeks now and seems like nobody has a clear anser:
-----------------------------------------------------------------------------------------------
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
-------------------------------------------------------------------------------------------------

upon runing compiz --replace in a terminal window.. same with ALT+F2 (no Compiz)

This is a HP nw8440 witn a ATI Fire GL V5200 (X1600):


Some data:
--------------------------------------------------------------------------
ricardo@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6747 (8.40.4)
ricardo@ubuntu:~$ glxinfo | grep direct
direct rendering: Yes
ricardo@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
etc......
---------------------------------------------------------------------------

(Same with the Mesa drivers..so dont blame the ATI Binaries).

Now, I have another computer, this a clone with an integrated Intel chip (i810) and the thing works like a charm, so I might be doing something correct in one and something wrong with this ATI board or the piece of hardware does not suppor or is not being supported by Compiz.

Anyone for a hit??

---

