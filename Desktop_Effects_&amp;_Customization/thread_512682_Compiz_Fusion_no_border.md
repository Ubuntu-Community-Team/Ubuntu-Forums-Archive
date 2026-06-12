---
title: "Compiz Fusion no border"
date: 2007-07-29
forum: Desktop Effects &amp; Customization
---

### Post by Chemnz on 2007-07-29
hi.. i've been really anxious to try compiz fusion and got it installed using trevino's guide.. the problem is (and i guess there are others too who might have this) the border are gone... either using ALT+F3 or terminal..both made my borders disappear.. running on the terminal gives me this
```
chemnz@ChemStatic:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugin cheatsheet (cheatsheet)
Adding plugin cube (cube)
Adding plugin bench (bench)
Adding plugin quickchange (quickchange)
Adding plugin move (move)
Adding plugin extrawm (extrawm)
Adding plugin vpswitch (vpswitch)
Adding plugin glib (glib)
Adding plugin animation (animation)
Adding plugin put (put)
Adding plugin fade (fade)
Adding plugin kiosk (kiosk)
Adding plugin addhelper (addhelper)
Adding plugin plane (plane)
Adding plugin shift (shift)
Adding plugin mblur (mblur)
Adding plugin annotate (annotate)
Adding plugin text (text)
Adding plugin notification (notification)
Adding plugin clone (clone)
Adding plugin regex (regex)
Adding plugin video (video)
Adding plugin scale (scale)
Adding core settings (General Options)
Adding plugin inotify (inotify)
Adding plugin screenshot (screenshot)
Adding plugin cubereflex (cubereflex)
Adding plugin fadedesktop (fadedesktop)
Adding plugin firepaint (firepaint)
Adding plugin minimize (minimize)
Adding plugin decoration (decoration)
Adding plugin ring (ring)
Adding plugin 3d (3d)
Adding plugin keybinding (keybinding)
Adding plugin colorfilter (colorfilter)
Adding plugin trailfocus (trailfocus)
Adding plugin resizeinfo (resizeinfo)
Adding plugin png (png)
Adding plugin splash (splash)
Adding plugin gotovp (gotovp)
Adding plugin expo (expo)
Adding plugin fs (fs)
Adding plugin svg (svg)
Adding plugin widget (widget)
Adding plugin thumbnail (thumbnail)
Adding plugin wall (wall)
Adding plugin wallpaper (wallpaper)
Adding plugin switcher (switcher)
Adding plugin neg (neg)
Adding plugin zoom (zoom)
Adding plugin blur (blur)
Adding plugin winrules (winrules)
Adding plugin water (water)
Adding plugin reflex (reflex)
Adding plugin crashhandler (crashhandler)
Adding plugin dbus (dbus)
Adding plugin atlantis (atlantis)
Adding plugin snap (snap)
Adding plugin screensaver (screensaver)
Adding plugin resize (resize)
Adding plugin place (place)
Adding plugin group (group)
Adding plugin showdesktop (showdesktop)
Adding plugin imgjpeg (imgjpeg)
Adding plugin scalefilter (scalefilter)
Adding plugin rotate (rotate)
Adding plugin opacify (opacify)
Adding plugin flash (flash)
Adding plugin wobbly (wobbly)
Adding plugin scaleaddon (scaleaddon)
Adding plugin mousegestures (mousegestures)
Adding plugin named ezoom
Initializing core options...done
Initializing move options...done
Initializing video options...done
Initializing minimize options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Initializing decoration options...done
Initializing zoom options...done
Initializing resize options...done
Initializing place options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing fade options...done
Initializing cube options...done
Initializing scale options...done
Initializing switcher options...done
Initializing rotate options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

```

tried using emerald too after that with emerald --replace & i .think didnt do anything

any one? :)

---

### Post by tekkenlord on 2007-07-29
I think you need to change your default depth to 24. Edit the "Screen" section in your /etc/X11/xorg.conf file so that the default depth is set to 24 and then restart the X server. Good luck!

---

### Post by ErusGuleilmus on 2007-07-29
I can open that text file, but I cant save. What is the command to open it as root?

---

### Post by isaacj87 on 2007-07-29
sudo gedit /etc/X11/xorg.conf

---

### Post by Chemnz on 2007-07-31
seems i screwed up my ubuntu :mad:... will get back after i fix thing up..be back in a few... thnks for the heads up.. i'll get on with it tonight

---

### Post by r4p70r on 2007-07-31
hey guys found a fix for this problem..... you need to install this program called Envy, it updates your nvidia and / or ATI drivers automatically then promps you to edit xorg then promps to restart. fixes the GLX depth 32 problem and funky window and white screen problems as well. heres a link. [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/) 

go there and follow the first step and you should be good to go.

hope this helps ya.

---

### Post by Chemnz on 2007-08-01
now i'm not too sure about Envy cuz the last time I got Envy then updated my Ubuntu (all this after a fresh install), I kinda lost my GUI... no gnome.. just the command prompt.. I think I'd better stay away from Envy for now

---

### Post by RedLine on 2007-08-01
the envy method works perfect on a fresh installed ubuntu, just tryed it right now.

---

### Post by figueroavictor66 on 2008-07-23
Well Im no Expert But this lil Fix has worked for me.
{hardy}

First Go To Your Session manager. System > Preferences > Session 
 
In The Start up tab click the add button.
There You would type in What ever you want for the title and description.
For the command just type in the old <   emerald --replace     >   *with out the brackets*

---

### Post by overdrank on 2008-07-24
Hi and this thread is over a year old and in the archive forums so I would suggest making any new post [[COLOR="DarkRed"]Here[/COLOR]](http://ubuntuforums.org/forumdisplay.php?f=330)
Thread closed

---

