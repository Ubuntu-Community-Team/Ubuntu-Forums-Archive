---
title: "Compiz Fusion WM Issues (version related?)"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by sdelano on 2007-06-29
I have just installed compiz-fusion (as per the mini how-to) and the compiz --replace command at first was nnot working for me. I saw that I needed to update a few things (system update notification), did so, and it still doesnt work. I then read that restarting help, so i restarted and tried compiz --replace again. Well... Compiz works...but my window manager does not.

When I did the system update I have a feeling I updated something having to do with the WM. This is the error I get when loading compiz:

```
Adding plugin zoom (zoom)
Adding plugin tile (tile)
Adding core settings (General Options)
Adding plugin wobbly (wobbly)
Adding plugin expo (expo)
Adding plugin screenshot (screenshot)
Adding plugin cubereflex (cubereflex)
Adding plugin scaleaddon (scaleaddon)
Adding plugin firepaint (firepaint)
Adding plugin glib (glib)
Adding plugin clone (clone)
Adding plugin addhelper (addhelper)
Adding plugin fs (fs)
Adding plugin place (place)
Adding plugin fadedesktop (fadedesktop)
Adding plugin move (move)
Adding plugin thumbnail (thumbnail)
Adding plugin fade (fade)
Adding plugin bench (bench)
Adding plugin cube (cube)
Adding plugin annotate (annotate)
Adding plugin snow (snow)
Adding plugin reflex (reflex)
Adding plugin switcher (switcher)
Adding plugin resizeinfo (resizeinfo)
Adding plugin video (video)
Adding plugin splash (splash)
Adding plugin wall (wall)
Adding plugin text (text)
Adding plugin opacify (opacify)
Adding plugin dbus (dbus)
Adding plugin animation (animation)
Adding plugin vpswitch (vpswitch)
Adding plugin snap (snap)
Adding plugin svg (svg)
Adding plugin group (group)
Adding plugin imgjpeg (imgjpeg)
Adding plugin water (water)
Adding plugin blur (blur)
Adding plugin fakeargb (fakeargb)
Adding plugin ring (ring)
Adding plugin rotate (rotate)
Adding plugin put (put)
Adding plugin minimize (minimize)
Adding plugin crashhandler (crashhandler)
Adding plugin plane (plane)
Adding plugin resize (resize)
Adding plugin decoration (decoration)
Adding plugin mblur (mblur)
Adding plugin inotify (inotify)
Adding plugin winrules (winrules)
Adding plugin trailfocus (trailfocus)
Adding plugin showdesktop (showdesktop)
Adding plugin neg (neg)
Adding plugin png (png)
Adding plugin scale (scale)
Adding plugin regex (regex)
Adding plugin extrawm (extrawm)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing zoom options...done
Initializing place options...done
Initializing move options...done
Initializing thumbnail options...done
Initializing minimize options...done
Initializing resize options...done
[COLOR="Red"]/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319[/COLOR]

Initializing decoration options...done
Initializing mblur options...done
Initializing showdesktop options...done
Initializing wobbly options...done
Initializing reflex options...done
Initializing animation options...done
Initializing blur options...done
Initializing fade options...done
Initializing cube options...done
Initializing switcher options...done
Initializing rotate options...done
Initializing scale options...done
Initializing expo options...done
Initializing cubereflex options...done
```

Thanks,
Stephen

---

### Post by hyperair on 2007-06-30
You're using Trevino's eyecandy repositories right? Run this:
```

sudo apt-get update
sudo apt-get upgrade

```

That'll make sure all your packages are up to date. Mine have no problems regarding versions, and it's clear that your Compiz version is very out to date (last year's one)

---

### Post by bodhi.zazen on 2007-07-06
> **sdelano said:**
> I have just installed compiz-fusion (as per the mini how-to) and the compiz --replace command at first was nnot working for me. I saw that I needed to update a few things (system update notification), did so, and it still doesnt work. I then read that restarting help, so i restarted and tried compiz --replace again. Well... Compiz works...but my window manager does not.

When I did the system update I have a feeling I updated something having to do with the WM. This is the error I get when loading compiz:

```
Adding plugin zoom (zoom)
Adding plugin tile (tile)
Adding core settings (General Options)
Adding plugin wobbly (wobbly)
Adding plugin expo (expo)
Adding plugin screenshot (screenshot)
Adding plugin cubereflex (cubereflex)
Adding plugin scaleaddon (scaleaddon)
Adding plugin firepaint (firepaint)
Adding plugin glib (glib)
Adding plugin clone (clone)
Adding plugin addhelper (addhelper)
Adding plugin fs (fs)
Adding plugin place (place)
Adding plugin fadedesktop (fadedesktop)
Adding plugin move (move)
Adding plugin thumbnail (thumbnail)
Adding plugin fade (fade)
Adding plugin bench (bench)
Adding plugin cube (cube)
Adding plugin annotate (annotate)
Adding plugin snow (snow)
Adding plugin reflex (reflex)
Adding plugin switcher (switcher)
Adding plugin resizeinfo (resizeinfo)
Adding plugin video (video)
Adding plugin splash (splash)
Adding plugin wall (wall)
Adding plugin text (text)
Adding plugin opacify (opacify)
Adding plugin dbus (dbus)
Adding plugin animation (animation)
Adding plugin vpswitch (vpswitch)
Adding plugin snap (snap)
Adding plugin svg (svg)
Adding plugin group (group)
Adding plugin imgjpeg (imgjpeg)
Adding plugin water (water)
Adding plugin blur (blur)
Adding plugin fakeargb (fakeargb)
Adding plugin ring (ring)
Adding plugin rotate (rotate)
Adding plugin put (put)
Adding plugin minimize (minimize)
Adding plugin crashhandler (crashhandler)
Adding plugin plane (plane)
Adding plugin resize (resize)
Adding plugin decoration (decoration)
Adding plugin mblur (mblur)
Adding plugin inotify (inotify)
Adding plugin winrules (winrules)
Adding plugin trailfocus (trailfocus)
Adding plugin showdesktop (showdesktop)
Adding plugin neg (neg)
Adding plugin png (png)
Adding plugin scale (scale)
Adding plugin regex (regex)
Adding plugin extrawm (extrawm)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing zoom options...done
Initializing place options...done
Initializing move options...done
Initializing thumbnail options...done
Initializing minimize options...done
Initializing resize options...done
[COLOR="Red"]/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319[/COLOR]

Initializing decoration options...done
Initializing mblur options...done
Initializing showdesktop options...done
Initializing wobbly options...done
Initializing reflex options...done
Initializing animation options...done
Initializing blur options...done
Initializing fade options...done
Initializing cube options...done
Initializing switcher options...done
Initializing rotate options...done
Initializing scale options...done
Initializing expo options...done
Initializing cubereflex options...done
```

Thanks,
Stephen

I had to remove libberyldecoration0 to fix that error

---

### Post by bodhi.zazen on 2007-07-07
OK, now I am getting a similar problem :

> /usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

Any solution ?

---

### Post by hyperair on 2007-07-07
Strange. I've been seeing this problem around a lot, but haven't gotten it before. I've got practically every Beryl component installed, Emerald and Emerald-Themes, and libdecoration0 among other things. My libberyldecoration0 is still intact as well. When I installed Compiz Fusion, I just installed every package with compiz in its name that didn't conflict with any other plugins.

---

