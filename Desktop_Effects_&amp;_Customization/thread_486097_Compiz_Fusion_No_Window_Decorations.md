---
title: "Compiz Fusion: No Window Decorations"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by Leniad on 2007-06-27
First post here, I recently installed ubuntu on my machine in a new partition and I'm liking it very much. I followed the stickied how-to to install compiz fusion, but I'm having a problem that seems pretty common: I'm lacking window decorations.

I've tried reinstalling emerald, starting with emerald --replace &, with , compiz --replace -c emerald &, and pretty much all suggestions I could find on the forums.

I'm hoping everyone posts all the tips to solve this problem in this post, so we can have them all in the same place for users with the same problem.

Thanks in advance!

(btw: my vid card is a GF 6600 if that helps)

---

### Post by Waappu on 2007-06-28
> **Leniad said:**
> First post here, I recently installed ubuntu on my machine in a new partition and I'm liking it very much. I followed the stickied how-to to install compiz fusion, but I'm having a problem that seems pretty common: I'm lacking window decorations.

I've tried reinstalling emerald, starting with emerald --replace &, with , compiz --replace -c emerald &, and pretty much all suggestions I could find on the forums.

I'm hoping everyone posts all the tips to solve this problem in this post, so we can have them all in the same place for users with the same problem.

Thanks in advance!

(btw: my vid card is a GF 6600 if that helps)

Hi

see if you can find solution here
[http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#An_automatic_easy_solution_for_.28almost.29_all_problems](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#An_automatic_easy_solution_for_.28almost.29_all_problems)
or here
[http://forum.beryl-project.org/viewforum.php?f=35&sid=8028ec95f007978da77798180a5d0e13](http://forum.beryl-project.org/viewforum.php?f=35&sid=8028ec95f007978da77798180a5d0e13)

---

### Post by mid_night gypsy on 2007-06-28
Today's update I guess, more or less forces the gtk-window deco. In a terminal edit /usr/bin/compiz....Near the bottom of the you see this....
```
# start the gtk-window-decorator if present
if [ -x /usr/bin/gtk-window-decorator ]; then
	/usr/bin/gtk-window-decorator --replace &
fi

```
 I change it to this to get emerald working.
```
# start the emerald-window-decorator if present
if [ -x /usr/bin/emerald ]; then
	/usr/bin/emerald --replace &
fi

```
 Run this command to edit (gedit).
```
sudo gedit /usr/bin/compiz
```
 Now your command for compiz and emerald will work.
```
compiz --replace -c emerald
```
 hope this helps,gypsy

---

### Post by neopulsar on 2007-06-28
Hey, first post here.
I'm not getting any window decorator:(
i've installed and re-installed everything, but when i run with *compiz --replace -c emerald* compiz starts but without any borders.

I've just noticed that if i try to run ccsm in a terminal i get the following

```
neopulsar@neopulsar-laptop:~$ ccsm
Adding core settings (General Options)
Adding plugin annotate (Annotate)
Adding plugin blur (Blur Windows)
Adding plugin clone (Clone Output)
Adding plugin cube (Desktop Cube)
Adding plugin dbus (Dbus)
Adding plugin decoration (Window Decoration)
Adding plugin fade (Fading Windows)
Adding plugin fs (Userspace File System)
Adding plugin glib (GLib)
Adding plugin inotify (Inotify)
Adding plugin minimize (Minimize Effect)
Adding plugin move (Move Window)
Adding plugin place (Place Windows)
Adding plugin plane (Desktop Plane)
Adding plugin png (Png)
Adding plugin regex (Regex Matching)
Adding plugin resize (Resize Window)
Adding plugin rotate (Rotate Cube)
Adding plugin scale (Scale)
Adding plugin screenshot (Screenshot)
Adding plugin svg (Svg)
Adding plugin switcher (Application Switcher)
Adding plugin video (Video Playback)
Adding plugin water (Water Effect)
Adding plugin wobbly (Wobbly Windows)
Adding plugin zoom (Zoom Desktop)
Adding plugin animation (Animations)
Adding plugin expo (Expo)
Adding plugin imgjpeg (JPEG)
Adding plugin neg (Negative)
Adding plugin opacify (Opacify)
Adding plugin put (Put)
Adding plugin resizeinfo (Resize Info)
Adding plugin ring (Ring Switcher)
Adding plugin scaleaddon (Scale Addons)
Adding plugin snap (Snapping Windows)
Adding plugin text (Text)
Adding plugin thumbnail (Window Previews)
Adding plugin vpswitch (Viewport mouse switch)
Adding plugin wall (Desktop Wall)
Adding plugin winrules (Window Rules)
Adding plugin addhelper (AddHelper)
Adding plugin bench (Benchmark)
Adding plugin crashhandler (Crash handler)
Adding plugin cubereflex (Cube Reflection)
Adding plugin extrawm (Extra WM Actions)
Adding plugin fadedesktop (Fade to Desktop)
Adding plugin firepaint (Paint fire on the screen)
Adding plugin group (Group and Tab Windows)
Adding plugin mblur (Motion blur)
Adding plugin reflex (Reflection)
Adding plugin showdesktop (Show desktop)
Adding plugin splash (Splash)
Adding plugin trailfocus (Trailfocus)
Adding plugin fakeargb (Color Opacity)
Adding plugin snow (Snow)
Adding plugin tile (Tile)
[B]libccs: dlopen: /usr/lib/compizconfig/backends/libini.so: cannot open shared object file: No such file or directory
libccs: dlopen: /usr/lib/compizconfig/backends/libini.so: cannot open shared object file: No such file or directory[/B]
Integration : true
Profile     : default
Segmentation fault (core dumped)

```

what happened to my libini.so, what can i do to solve this????
I think thats why i'm not getting borders.
I hope you can help me, thanks.

---

### Post by neopulsar on 2007-06-28
pleeeeeaase help, now i'm sure that without this file i can't make compiz and emerald work.
I don't know where to find it or how to restore it.
*/usr/lib/compizconfig/backends/libini.so*

---

### Post by Leniad on 2007-06-28
Well, I somehow made it work!

While looking at every post in the board for help, I found this tip:

Open your xorg.conf file (located at /etc/x11/xorg.conf)

Add this text to the Section "Device"

	Option "AddARGBGLXVisuals" "True"
	Option "RenderAccel" "True"
	Option "AllowGLXWithComposite" "True"
	Option "backingstore" "True"
	Option "TripleBuffer" "True"

After that, it worked for me.
(You might want to open gedit with the "sudo gedit" command, so it lets you overwrite xorg.conf)

Compiz Fusion is looking great!
I hope this solves the problem for at least some of you...

---

### Post by keesjelol on 2007-06-28
when i type in compiz --replace -c emerald i get this back

```
Adding core settings (General Options)
Adding plugin annotate (annotate)
Adding plugin blur (blur)
Adding plugin clone (clone)
Adding plugin cube (cube)
Adding plugin dbus (dbus)
Adding plugin decoration (decoration)
Adding plugin fade (fade)
Adding plugin fs (fs)
Adding plugin glib (glib)
Adding plugin inotify (inotify)
Adding plugin minimize (minimize)
Adding plugin move (move)
Adding plugin place (place)
Adding plugin plane (plane)
Adding plugin png (png)
Adding plugin regex (regex)
Adding plugin resize (resize)
Adding plugin rotate (rotate)
Adding plugin scale (scale)
Adding plugin screenshot (screenshot)
Adding plugin svg (svg)
Adding plugin switcher (switcher)
Adding plugin video (video)
Adding plugin water (water)
Adding plugin wobbly (wobbly)
Adding plugin zoom (zoom)
Adding plugin animation (animation)
Adding plugin expo (expo)
Adding plugin imgjpeg (imgjpeg)
Adding plugin neg (neg)
Adding plugin opacify (opacify)
Adding plugin put (put)
Adding plugin resizeinfo (resizeinfo)
Adding plugin ring (ring)
Adding plugin scaleaddon (scaleaddon)
Adding plugin snap (snap)
Adding plugin text (text)
Adding plugin thumbnail (thumbnail)
Adding plugin vpswitch (vpswitch)
Adding plugin wall (wall)
Adding plugin winrules (winrules)
Adding plugin addhelper (addhelper)
Adding plugin bench (bench)
Adding plugin crashhandler (crashhandler)
Adding plugin cubereflex (cubereflex)
Adding plugin extrawm (extrawm)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin group (group)
Adding plugin mblur (mblur)
Adding plugin reflex (reflex)
Adding plugin showdesktop (showdesktop)
Adding plugin splash (splash)
Adding plugin trailfocus (trailfocus)
Adding plugin fakeargb (fakeargb)
Adding plugin snow (snow)
Adding plugin tile (tile)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing minimize options...done
Initializing move options...done
Initializing place options...done
Initializing resize options...done
Initializing wobbly options...done
Initializing zoom options...done
Initializing fade options...done
Initializing cube options...done
Initializing rotate options...done
Initializing scale options...done
Initializing switcher options...done

```

please say it's something stupid thats keeping me from having windows with borders

---

### Post by mid_night gypsy on 2007-06-28
keesjelol,
 Well, not knowing your system or if this is your first time with compizfusion or beryl.
I have to guess that you have your nvidia or ati driver install. I would do as Leniad posted 'bout device section, Also if you don't have this at the bottom of your /etc/x11/xorg.conf add this
```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```
You can use this command to edit (gedit) xorg.
```
sudo gedit /etc/x11/xorg.conf
```
hope this helps, gypsy

---

### Post by Raineer on 2007-07-01
I just wanted to post a reply of EXTREME JOY.  Two of the posters above recommended adding the following to xorg.conf:

```
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

And OH MY I have window decorations again.  May the sun, moon, and stars shine down on you wherever you walk and may there be a pot of gold at the end of every rainbow for you fine people.

(yes, I had pulled out THAT much hair over this issue)

I love these forums.

---

### Post by campnic on 2007-07-01
> **Leniad said:**
> 

Open your xorg.conf file (located at /etc/x11/xorg.conf)

Add this text to the Section "Device"

	Option "AddARGBGLXVisuals" "True"
	Option "RenderAccel" "True"
	Option "AllowGLXWithComposite" "True"
	Option "backingstore" "True"
	Option "TripleBuffer" "True"


Hoooray!  Thanks for the tip.  This is all i needed to add to get it working.   :KS :KS :KS :KS :KS

---

### Post by fjf on 2007-07-01
May I join my joy to yours?.   FINALLY IT WORKS!!.

Thanks to everyone.


> **Raineer said:**
> I just wanted to post a reply of EXTREME JOY.  Two of the posters above recommended adding the following to xorg.conf:

```
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

And OH MY I have window decorations again.  May the sun, moon, and stars shine down on you wherever you walk and may there be a pot of gold at the end of every rainbow for you fine people.

(yes, I had pulled out THAT much hair over this issue)

I love these forums.

---

