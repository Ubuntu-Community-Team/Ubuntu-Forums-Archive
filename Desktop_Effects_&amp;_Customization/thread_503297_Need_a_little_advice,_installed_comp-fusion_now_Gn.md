---
title: "Need a little advice, installed comp-fusion now Gnome is misbehaving"
date: 2007-07-17
forum: Desktop Effects &amp; Customization
---

### Post by stoer on 2007-07-17
Hi,
sorry to ask, but i can't seem to work out exactly what i've done wrong, 
I've followed the following guide
Compiz Fusion for ATI cards + Xgl in Feisty     [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
and everything works just fine...
The eye candy is imperssive, the effects are just as everyone promised they would be, that is they are in the xgl sessions that i start.
The problem is with my ''normal Gnome session''
If i log into a Gnome session i am now experiencing apparently what everybody else is experiencing as problems within the compiz fusion +xgl sessions.  That is, i'm getting borderless windows, windows sticking to the top left hand corner, the welcom pannel hanging in the middle of my desktop.
Now, i know i've messed up, and i've looked and looked, but i still don't know what it is i've done. :(

I have an ATI radeon mobility 9700, running a clean install of Feisty (multimedia codecs added, build essentials and dvd support as per [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)  installing mm support sticky.

If anyone has the patience to point me in the right direction i'd greatly appreciate it.
To be frank i'd rather have Gnome working without the eyecandy if that's the only option.

---

### Post by stoer on 2007-07-17
Ah, been moved.....
Sorry still see myself as a rank beginner here in Linux land, apologies for the wrong choice of fora.

---

### Post by Deco_21 on 2007-07-17
Try installing libdecoration0

sudo apt-get install libdecoration0

and restart your X session
CTRL + ALT + BACKSPACE

---

### Post by kittyhawk63 on 2007-07-17
I experienced exactly the successes and failures that you are talking about. I would like to know if the suggestion given by Deco_21 for installing the file from the repositories works. Please post if you were successful.
kh

Edit: Too bad that didn't do it for you..

---

### Post by stoer on 2007-07-17
Thanks for your quick response, appreciate it.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdecoration0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Apparently the latest version is already installed.... I guess as a part of the above mentioned How to.

---

### Post by Deco_21 on 2007-07-17
Try this .
in the beryl-manager choose Select windows manager "Compiz" then . 

In terminal

compiz --replace -c emerald &

And tell me what it saids.

---

### Post by stoer on 2007-07-17
> **Deco_21 said:**
> Try this .
in the beryl-manager choose Select windows manager "Compiz" then . 

In terminal

compiz --replace -c emerald &

And tell me what it saids.


Ok.
1) in gnome session or compiz fusion +xgl session?
i  assume in Gnome.
2) In the Beryl-manager.....
I don have this, i have the compiz config manager but don see ´select windows manager´

Running your suggested comamand anyway, i get  

```
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

?

It&#347; a little awkward because i need to close  my browser each time (stuck to the top left corner) in order to access the gnome top panel.
trying the windows manager under preferences delivers,

cannot start the preferences application for your windows manager.
Windows manager ´Unknown´ has not registered a configuration tool.

Just to add that when i now start a Gnome session i seeing a problem reported with the keyboard layout and the restricted driver icon (ati) is also gone. No idea if this helps.

---

### Post by Deco_21 on 2007-07-17
1) Yes, in the xlg session



2) Did you install beryl right ??

Check the part in the HOW-TO [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

**"BERYL"**

sudo apt-get install beryl [SIZE="4"]**beryl-manager**[/SIZE] beryl-core beryl-plugins beryl-settings emerald emerald-themes

You must have beryl in order to use Compiz Fusion. Its more easy.

Then again. Try in  the terminal first ... "beryl -manager" then change the windows manager to "compiz". then in other terminal "compiz --replace --c emerald &".

Tell me wait it said. ok.

---

### Post by stoer on 2007-07-17
> **Deco_21 said:**
> 1) Yes, in the xlg session



2) Did you install beryl right ??

Check the part in the HOW-TO [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

**"BERYL"**

sudo apt-get install beryl [SIZE="4"]**beryl-manager**[/SIZE] beryl-core beryl-plugins beryl-settings emerald emerald-themes

You must have beryl in order to use Compiz Fusion. Its more easy.

Then again. Try in  the terminal first ... "beryl -manager" then change the windows manager to "compiz". then in other terminal "compiz --replace --c emerald &".

Tell me wait it said. ok.



Now, making headway :)

I read the following in the guide....

BERYL
If you want Compiz Fusion - skip ahead to the Compiz Fusion section.

and skipped directly to  to installing compizfusion without installing beryl !

Now i have ´Select window manager´

In the compiz fusion + xgl session all appears to be great, not tried anything but wobbly windows and rotating cube which both appear to work without a flaw.

In the Gnome session, selecting Metacity or compiz results in borderless frozen windows. Selecting Beryl gives me windows and borders...and a working Gnome :)

I&#314;l switch to compiz fusion and try your command now "compiz --replace --c emerald &".
back in a minute.

---

### Post by Deco_21 on 2007-07-17
If everything works you dont need to try "compiz --replace --c emerald &"
that only works if you dont have decorations.
That command copy the emerald theme manager decoration to the compizFusion session. So if you have everything ok you dont need to do nothing.

---

### Post by stoer on 2007-07-17
Ok,
switched to compiz in select windows manager and in terminal get the following....

```
:~$ compiz --replace --c emerald &
[1] 12586
steve@laptop:~$ /usr/bin/compiz.real (core) - Warn: Unknown option '--c'

Backend     : ini
Integration : true
Profile     : default
Adding plugin snap (snap)
Adding plugin switcher (switcher)
Adding core settings (General Options)
Adding plugin firepaint (firepaint)
Adding plugin expo (expo)
Adding plugin svg (svg)
Adding plugin fadedesktop (fadedesktop)
Adding plugin wall (wall)
Adding plugin plane (plane)
Adding plugin crashhandler (crashhandler)
Adding plugin put (put)
Adding plugin cubereflex (cubereflex)
Adding plugin png (png)
Adding plugin fade (fade)
Adding plugin showdesktop (showdesktop)
Adding plugin wobbly (wobbly)
Adding plugin inotify (inotify)
Adding plugin screenshot (screenshot)
Adding plugin cube (cube)
Adding plugin scalefilter (scalefilter)
Adding plugin rotate (rotate)
Adding plugin group (group)
Adding plugin clone (clone)
Adding plugin blur (blur)
Adding plugin gotovp (gotovp)
Adding plugin decoration (decoration)
Adding plugin annotate (annotate)
Adding plugin regex (regex)
Adding plugin resize (resize)
Adding plugin water (water)
Adding plugin imgjpeg (imgjpeg)
Adding plugin extrawm (extrawm)
Adding plugin reflex (reflex)
Adding plugin scale (scale)
Adding plugin video (video)
Adding plugin ring (ring)
Adding plugin text (text)
Adding plugin bench (bench)
Adding plugin splash (splash)
Adding plugin trailfocus (trailfocus)
Adding plugin fs (fs)
Adding plugin zoom (zoom)
Adding plugin resizeinfo (resizeinfo)
Adding plugin move (move)
Adding plugin dbus (dbus)
Adding plugin glib (glib)
Adding plugin addhelper (addhelper)
Adding plugin thumbnail (thumbnail)
Adding plugin scaleaddon (scaleaddon)
Adding plugin opacify (opacify)
Adding plugin place (place)
Adding plugin vpswitch (vpswitch)
Adding plugin neg (neg)
Adding plugin animation (animation)
Adding plugin winrules (winrules)
Adding plugin minimize (minimize)
Adding plugin mblur (mblur)
Initializing core options...done
Initializing firepaint options...done
Initializing decoration options...done
Initializing resize options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing zoom options...done
Initializing move options...done
Initializing place options...done
Initializing vpswitch options...done
Initializing minimize options...done
Initializing snap options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing rotate options...done
Initializing scale options...done
Initializing switcher options...done



```

---

### Post by Deco_21 on 2007-07-17
Well it looks that everything its ok right ?? , Do you have any other problem ??.
You should try effects like the dodge part.

---

### Post by stoer on 2007-07-17
> **Deco_21 said:**
> If everything works you dont need to try "compiz --replace --c emerald &"
that only works if you dont have decorations.
That command copy the emerald theme manager decoration to the compizFusion session. So if you have everything ok you dont need to do nothing.

Hi Again.
(and thanks for all the help)
Selecting compiz results in lost boardes and selecting beryl gives me boarders. So i guess there is still a problem. Bugger.

edit.....
retyping compiz --replace lets compiz work, boarders and all :)
I'll look further tomorrow, i'm about falling off my chair now...been up since 06.00 and it's now 02.15 :(

Many, many thanks for the helping hand, very much appreciated.

---

### Post by Deco_21 on 2007-07-17
> **stoer said:**
> Hi Again.
(and thanks for all the help)
Selecting compiz results in lost boardes and selecting beryl gives me boarders. So i guess there is still a problem. Bugger.

Try in beryl-manager >Select windows decoration > GTK Windows Decorator.
And tell me if the decorations appear .

---

### Post by Deco_21 on 2007-07-17
> **stoer said:**
> Hi Again.
(and thanks for all the help)
Selecting compiz results in lost boardes and selecting beryl gives me boarders. So i guess there is still a problem. Bugger.

edit.....
retyping compiz --replace lets compiz work, boarders and all :)
I'll look further tomorrow, i'm about falling off my chair now...been up since 06.00 and it's now 02.15 :(

Many, many thanks for the helping hand, very much appreciated.

Your welcome. See you next time.

---

